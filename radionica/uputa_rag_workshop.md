# Uputa: Napravi AI koji zna tvoje dokumente
**Festival znanosti 2026 — Veleučilište u Virovitici**
*n8n RAG radionica — slijedi korake redom*

---

## Što ćeš izgraditi

Na kraju radionice imat ćeš AI agenta koji:
- Razgovara s tobom na hrvatskom jeziku
- Pamti tijek razgovora
- Odgovara na pitanja iz dokumenata koje si mu ti dao

---

## KORAK 1 — Osnovni chat agent

### Što ćemo napraviti
Najjednostavniji mogući AI chat — samo poruka ulazi, odgovor izlazi. Bez memorije, bez dokumenata.

### Upute

**1.1** Otvori n8n i klikni **New Workflow** (gumb gore lijevo)

**1.2** Dodaj prvi čvor — okidač razgovora:
- Klikni **+** u sredini platna
- Pretraži: `Chat Trigger`
- Odaberi **When chat message received**
- Klikni **Add node**

**1.3** Dodaj AI model:
- Klikni **+** desno od Chat Trigger čvora
- Pretraži: `OpenAI Chat Model`
- Odaberi **OpenAI Chat Model**
- U postavkama: **Model** → `gpt-4.1-mini`
- Klikni **Back to canvas**

**1.4** Dodaj AI agenta:
- Klikni **+** desno od Chat Trigger čvora (na glavnoj liniji)
- Pretraži: `AI Agent`
- Odaberi **AI Agent**

> ℹ️ OpenAI Chat Model čvor automatski se spaja na AI Agent kao `ai_languageModel`. Ako se nije spojio sam, povuci vezu od OpenAI Chat Model čvora do AI Agent čvora.

**1.5** Aktiviraj workflow:
- Klikni **Save** (gore desno)
- Klikni **Inactive** toggle → postaje **Active**

**1.6** Testiraj:
- Klikni na **Chat Trigger** čvor
- Klikni **Chat** (gumb koji se pojavi)
- Napiši: `Pozdrav!`
- Agent treba odgovoriti na engleskom (to ćemo popraviti)

---

## KORAK 2 — Dodaj memoriju razgovora

### Što ćemo napraviti
Bez memorije, agent zaboravi svaku poruku. Sad ćemo mu dati kratkoročnu memoriju.

### Upute

**2.1** Klikni na **AI Agent** čvor da ga otvoriš

**2.2** Pri dnu čvora vidiš **+ Add Memory** — klikni

**2.3** Pretraži: `Simple Memory`
- Odaberi **Window Buffer Memory**
- Ostavi zadane postavke (pamti zadnjih 5 poruka)
- Klikni **Back to canvas**

**2.4** Testiraj memoriju:
- Otvori Chat (klikni na Chat Trigger → Chat)
- Napiši: `Moje ime je Ana.`
- Agent potvrdi
- Napiši: `Kako se zovem?`
- Agent treba reći `Ana` ✓

> ⚠️ Ako ne zna ime — memorija se nije spojila. Provjeri je li Simple Memory čvor spojen na AI Agent.

---

## KORAK 3 — Postavi sistemski prompt

### Što ćemo napraviti
Dati agentu ulogu i pravila ponašanja.

### Upute

**3.1** Klikni na **AI Agent** čvor

**3.2** U polju **System Message** upiši točno ovaj tekst:

```
Ti si asistent na Festivalu znanosti 2026 na Veleučilištu u Virovitici.
Uvijek odgovaraj na hrvatskom jeziku.
Ako nešto ne znaš, reci da ne znaš.
```

**3.3** Klikni **Back to canvas** i **Save**

**3.4** Testiraj — otvori Chat i postavi ova pitanja:

> 💬 `What is your name?`
> → Treba odgovoriti na **hrvatskom** ✓

> 💬 `Što se nalazi na jelovniku restorana Strukovne škole Virovitica?`
> → Treba reći da **ne zna** ✓

**Zapiši što je odgovorio na pitanje o jelovniku — uspoređivat ćemo to s odgovorom nakon što dodamo dokumente.**

---

## KORAK 4 — Dodaj upload dokumenata u Qdrant

### Što ćemo napraviti
Novi dio workflowa koji prima datoteku i sprema je u vektorsku bazu.

> ℹ️ Ovaj dio workflowa je **odvojen** od chata — radi samo kad uploadaš dokument.

### Upute

**4.1** Klikni na prazno mjesto na platnu (dalje lijevo od postojećih čvorova)

**4.2** Dodaj čvor za upload forme:
- Klikni **+**
- Pretraži: `Form Trigger`
- Odaberi **On form submission**
- Postavi:
  - **Form Title**: `Dodaj dokument`
  - **Form Description**: `Dodaj dokument u Vector bazu podataka`
  - Klikni **Add Field**:
    - **Field Label**: `Pretraži datoteke`
    - **Field Type**: `File`
    - Uključi **Required**
- Klikni **Back to canvas**

**4.3** Dodaj Qdrant čvor za spremanje:
- Klikni **+** desno od Form Trigger čvora
- Pretraži: `Qdrant`
- Odaberi **Qdrant Vector Store**
- Postavi:
  - **Operation Mode**: `Insert Documents`
  - **Qdrant Collection**: odaberi svoju kolekciju (npr. `student_01`)
- Klikni **Back to canvas**

**4.4** Dodaj Embeddings (pretvara tekst u vektore):
- Klikni **+** ispod Qdrant čvora (na `ai_embedding` liniji)
- Pretraži: `Embeddings OpenAI`
- Odaberi **Embeddings OpenAI**
- Ostavi zadane postavke
- Klikni **Back to canvas**

**4.5** Dodaj Data Loader (čita datoteke):
- Klikni **+** ispod Qdrant čvora (na `ai_document` liniji)
- Pretraži: `Default Data Loader`
- Odaberi **Default Data Loader**
- Postavi **Data Type**: `Binary`
- Klikni **Back to canvas**

**4.6** Klikni **Save**

### Provjera spajanja
Na kraju bi trebalo biti ovako spojeno:
```
Form Trigger → Qdrant (spremi)
                  ↑ ai_embedding: Embeddings OpenAI
                  ↑ ai_document:  Default Data Loader
```

**4.7** Dodaj Sticky Note za ovaj dio:
- Desni klik na prazno platno → **Add Sticky Note**
- Upiši: `📥 Pohrana dokumenata`
- Povuci da pokrije ovaj dio workflowa

---

## KORAK 5 — Spoji Qdrant s AI Agentom

### Što ćemo napraviti
Dati agentu mogućnost pretraživanja vektorske baze kao alat.

### Upute

**5.1** Klikni na **AI Agent** čvor → **+ Add Tool**

**5.2** Pretraži: `Qdrant`
- Odaberi **Qdrant Vector Store**
- Postavi:
  - **Operation Mode**: `Retrieve Documents (As Tool for AI Agent)`
  - **Tool Description**: `Obavezno koristi ovaj alat kao prvi korak za svako korisničko pitanje.`
  - **Qdrant Collection**: odaberi **istu kolekciju** kao u koraku 4.3
- Klikni **Back to canvas**

**5.3** Dodaj Embeddings za čitanje:
- Klikni **+** ispod novog Qdrant čvora (na `ai_embedding` liniji)
- Pretraži: `Embeddings OpenAI`
- Odaberi **Embeddings OpenAI**
- Ostavi zadane postavke

> ⚠️ Ovo je **drugi** Embeddings čvor — jedan je za upload, jedan za čitanje. Oba moraju biti spojena na **ispravne** Qdrant čvorove.

**5.4** Ažuriraj sistemski prompt u AI Agent čvoru:

```
Ti si asistent na Festivalu znanosti 2026 na Veleučilištu u Virovitici.
Uvijek odgovaraj na hrvatskom jeziku.
Za svako pitanje PRVO pretraži bazu dokumenata.
Dokumente koristi kao primarni izvor činjenica.
Opće znanje koristi samo za razumijevanje i interpretaciju.
Ako nešto ne znaš, reci da ne znaš.
```

**5.5** Klikni **Save**

**5.6** Dodaj Sticky Note za ovaj dio:
- Desni klik na prazno platno → **Add Sticky Note**
- Upiši: `💬 Razgovor s dokumentima`
- Povuci da pokrije Chat Trigger, AI Agent i sve čvorove desno

---

## KORAK 6 — Uploadaj dokument i testiraj

### Upute

**6.1** Otvori upload formu:
- Klikni na **Form Trigger** čvor (onaj lijevi, za upload)
- Klikni **Test step** ili kopiraj URL forme
- Otvori URL u novom tabu

**6.2** Uploadaj jelovnik restorana (datoteka `restoran-ssv.md`)
- Klikni **Choose file**, odaberi datoteku
- Klikni **Submit**

**6.3** Provjeri je li upload prošao:
- Vrati se u n8n
- Trebao bi vidjeti zelenu oznaku na čvorovima (execution success)

**6.4** Testiraj chat — otvori Chat i postavi ista pitanja kao u Koraku 3:

> 💬 `Što se nalazi na jelovniku restorana Strukovne škole Virovitica?`
> → Sada treba nabrojiti pizze s cijenama ✓

> 💬 `Imam alergiju na jaja. Mogu li naručiti pizzu Struki?`
> → Treba reći da Pizza Struki sadrži jaje na oko ✓

> 💬 `Koji je Teslin zadnji američki patent?`
> → Ne zna još — baza nema taj dokument

**6.5** Uploadaj i ostale dokumente:
- Ponovi korak 6.1–6.3 za svaki dokument:
  - `US334823A.txt` — Teslin prvi patent
  - `US1655113A.txt` — Teslin zadnji patent
  - `List_of_Nikola_Tesla_patents.pdf` — popis svih patenata

**6.6** Testiraj s Teslom:
> 💬 `Što opisuje Teslin zadnji američki patent?`
> → Treba opisati US1655113 — metoda vertikalnog polijetanja i slijetanja (VTOL zrakoplov), 1928. ✓

> 💬 `Koji su najveći energetski izazovi danas koje bi Tesla, s obzirom na njegove patente u bazi, mogao pokušati riješiti?`
> → Agent kombinira podatke iz baze s interpretacijom ✓

---

## Česta pitanja i problemi

**Agent ne zna sadržaj dokumenta koji sam uploadao:**
→ Provjeri je li Qdrant kolekcija ista u oba Qdrant čvora (upload i čitanje)

**Agent odgovara na engleskom:**
→ Provjeri sistemski prompt u AI Agent čvoru — mora biti uneseno točno kao u Koraku 5.4

**Upload forme ne radi:**
→ Provjeri je li workflow **aktivan** (Active, ne Inactive)

**Agent pamti razgovor između različitih sesija:**
→ To je normalno za Simple Memory — osvježi stranicu chata da počneš novu sesiju

**Dva Embeddings čvora — koji ide gdje:**
→ Lijevi (uz Qdrant spremi) → za upload
→ Desni (uz Qdrant čitaj) → za chat
→ Nikad ne mijenjaj njihove veze

---

## Krajnji izgled workflowa

```
[Form Trigger] → [Qdrant (spremi)]
                      ↑ Embeddings OpenAI (upload)
                      ↑ Default Data Loader

[Chat Trigger] → [AI Agent]
                      ↑ OpenAI Chat Model
                      ↑ Simple Memory
                      ↑ Qdrant (čitaj) ← Embeddings OpenAI (čitanje)
```

---

*Radionica: Festival znanosti 2026 — Veleučilište u Virovitici*
*Voditelj: Marin Kepec, DevOps inženjer, Infobip*
