# Plan radionice v2 — Hands-on RAG s n8n (40 min)

## Cilj radionice
Učenici prolaze cijeli RAG pipeline — od osnovnog chata do AI-ja koji čita njihov dokument — i na kraju imaju sustav koji su sami izgradili.

**Ključna poruka:** "Ovo nije demo koji ja pokrećem. Vi ste ga napravili."

---

## Timing na jedan pogled

| Dio | Sadržaj | Trajanje | Kumulativno |
|-----|---------|----------|-------------|
| 0 | Orjentacija u n8n | 3 min | 3 min |
| 1 | Basic chat + problem demo | 7 min | 10 min |
| 2 | RAG — objašnjenje i setup | 5 min | 15 min |
| 3 | Hands-on RAG izgradnja | 15 min | 30 min |
| 4 | Test s Teslinim dokumentom | 5 min | 35 min |
| 5 | Finale — vlastiti dokument | 5 min | 40 min |

---

## Dio 0: Orjentacija u n8n (3 min)

**Voditelj demo — učenici gledaju**

Otvoriti Template 1 na projektoru i pokazati:
- Što je node (jedan korak u workflowu)
- Kako se nodeovi povezuju (strelice = tok podataka)
- Gdje se vidi output pojedinog noda (klik na node → rezultat)
- Gdje je chat sučelje

**Reći:** *"Ne trebate razumijeti svaki detalj. Gledate kako podaci teku s jednog mjesta na drugo — to je sve."*

Učenici otvaraju vlastite workspaceove (credentials na papiru pred njima).

**Checkpoint:** Svi imaju n8n otvoren i vide Template 1.

---

## Dio 1: Basic chat + problem demo (7 min)

### 1a — Demo basic chata (2 min)

**Voditelj na projektoru:**
- Pokrenuti chat, postaviti jednostavno pitanje: *"Što je izmjenična struja?"*
- Pokazati odgovor — naglasiti da AI odgovara iz svog treninga
- Pokazati sistemski prompt: dodati *"Odgovaraj samo na hrvatskom. Ako nešto ne znaš, reci to jasno."*

**Reći:** *"Ovaj sistemski prompt je kao uputa zaposleniku — definirate kako se ponaša."*

### 1b — Hands-on: dodavanje memorije (3 min)

**Zadatak (svi rade):**
1. Dodati **Window Buffer Memory node**
2. Spojiti ga na AI Agent node
3. Postaviti history na 5 poruka
4. Test: pitati nešto, zatim reći *"Što sam te upravo pitao?"* — AI treba zapamtiti

**Facilitator cue:** Ako netko ne može spojiti node — *"Klikni i drži na output točku noda, pa povuci do input točke."*

### 1c — Problem demo (2 min)

**Voditelj pita chat** (svi gledaju):
*"Kad je objavljena zadnja vijest na stranici Tehničke škole Virovitica?"*

Očekivani odgovor: *"Nemam pristup internetu niti trenutnim informacijama..."*

**Reći:** *"Ovo nije greška. ChatGPT ne zna što je na vašoj školskoj stranici — jer to nije javni internet podatak. Kako to popraviti? Dajemo mu dokument."*

→ Prijelaz na RAG.

**Checkpoint @10 min:** Svi imaju basic chat s memorijom koji radi.

---

## Dio 2: RAG — što dodajemo i zašto (5 min)

**Voditelj na projektoru — otvoriti Template 2**

Pokazati gotov RAG workflow (koji učenici još nisu izgradili) i proći kroz svaki node:

```
PDF Upload → Text Splitter → Embeddings → Qdrant (insert)
                                                    ↓
Korisničko pitanje → Embeddings → Qdrant (search) → AI Agent → Odgovor
```

**Za svaki node — jedna rečenica:**
- **PDF Upload** — učitava dokument u workflow
- **Text Splitter** — reže tekst na komade (chunks) jer cijeli dokument ne može u prompt
- **Embeddings** — pretvara tekst u vektore (kao što smo vidjeli na prezentaciji)
- **Qdrant insert** — sprema vektore u bazu, jednom
- **Qdrant search** — za svako pitanje pronalazi najrelevantnije dijelove dokumenta
- **AI Agent** — dobiva pitanje + relevantni kontekst → generira odgovor

**Reći:** *"Svaki node koji vidite ovdje — napravit ćete ga za 15 minuta. Idemo."*

**Checkpoint @15 min:** Učenici razumiju što će graditi.

---

## Dio 3: Hands-on RAG izgradnja (15 min)

**Voditelj vodi korak po korak na projektoru. Učenici rade paralelno.**

Koristiti Template 2 koji ima placeholder nodeove — učenici ih samo konfiguriraju i spajaju.

### Korak 1 — PDF Input (2 min)
- Dodati **PDF Binary Input** node
- Uploadati pripremljeni Tesla dokument (PDF na desktopu)
- Pokrenuti node, provjeriti da je dokument učitan (output: binary data)

**Facilitator cue:** *"Ne radi? Provjeri je li file path ispravan — klikni na node i pogledaj 'File Path' polje."*

### Korak 2 — Text Splitter (3 min)
- Dodati **Recursive Character Text Splitter** node
- Chunk size: **500**, Overlap: **50**
- Spojiti na PDF node, pokrenuti
- Output treba pokazati listu tekstualnih blokova

**Reći:** *"Overlap znači da svaki chunk dijeli 50 znakova s prethodnim — da ne izgubimo kontekst na rubovima."*

### Korak 3 — Embeddings + Qdrant insert (5 min)
- Dodati **OpenAI Embeddings** node (credentials već postavljeni)
- Dodati **Qdrant Vector Store** node — mode: **Insert**
  - Collection name: `radionica_[ime_tima]` (svaki tim svoja kolekcija)
- Spojiti: Text Splitter → Embeddings → Qdrant Insert
- Pokrenuti — Qdrant treba potvrditi koliko je vektora insertirano

**Facilitator cue:** *"Qdrant greška 'collection not found'? Klikni 'Create collection' checkbox u Qdrant nodu."*

### Korak 4 — Query + Retrieval (5 min)
- Na postojećem AI Agent nodu: dodati **Vector Store Retriever** kao tool
- Qdrant node — mode: **Search**, ista collection kao gore
- Spojiti retriever na AI Agent
- Test query: *"O čemu govori ovaj dokument?"*

**Facilitator cue:** *"AI odgovara ali ne citira? Dodaj u sistemski prompt: 'Uvijek navedi iz kojeg dijela dokumenta dolazi tvoj odgovor.'"*

**Checkpoint @30 min:** Barem 80% timova ima RAG koji radi na dummy pitanju.

---

## Dio 4: Test s Teslinim dokumentom (5 min)

**Svi timovi testiraju s pripremljenim pitanjima:**

1. *"Koji je broj Teslinog patenta za izmjeničnu struju?"*
2. *"Što Tesla opisuje kao prednost svog sustava u usporedbi s istosmjernom strujom?"*
3. *"Napiši sažetak ovog patenta u 3 rečenice."*

**Voditelj na projektoru** pokazuje jedan od odgovora — klikne na Qdrant search node i pokaže koji su chunks bili dohvaćeni za pitanje broj 2.

**Reći:** *"Vidite — AI nije pročitao cijeli patent. Pronašao je 3 najrelevantinija odlomka i na temelju njih odgovorio. To je RAG."*

**Checkpoint @35 min:** Svi su testirali barem jedno pitanje i dobili smislen odgovor.

---

## Dio 5: Finale — vlastiti dokument (5 min)

### Wow moment

**Voditelj uploadava novi dokument** — najnovija vijest sa stranice Tehničke škole Virovitica (PDF pripremljen unaprijed, datum i specifičan naslov koji ne postoji nigdje javno na internetu).

Pitanje: *"Što piše u zadnjoj vijesti na stranici Tehničke škole?"*

Basic chat (bez RAG): *"Nemam tu informaciju."*
RAG chat: točan odgovor s datumom i detaljima.

**Reći:** *"Javni ChatGPT to ne zna. Vaš sustav zna — jer ste vi odlučili što on uči."*

### Slobodni eksperiment (ako ostane vremena)
Učenici uploadaju **vlastiti dokument** — mogu biti school notes, Wikipedia članak, bilo što u PDF formatu.
Pitaju 2-3 pitanja.

**Zaključak:** *"Upravo ste napravili ono što prave firme koriste za interne dokumente. Arhitektura je ista — samo je njihov Qdrant veći, a dokumenti povjerljivi."*

---

## Tehnička priprema (za tebe)

### n8n setup

**Template 1 — Basic Chat (potpuno gotov):**
- Manual/Chat Trigger
- OpenAI Chat Model (gpt-4o-mini, credentials unaprijed)
- Window Buffer Memory (3 poruke — učenici će promijeniti na 5)
- Sistemski prompt placeholder

**Template 2 — RAG Skeleton (80% gotov):**
- Sve iz Template 1
- PDF Binary Input node (dodan, nespojeno)
- Recursive Text Splitter node (dodan, chunk size 500/50 unaprijed)
- OpenAI Embeddings node (credentials unaprijed, nespojeno)
- Qdrant Insert node (nespojeno, collection name prazno)
- Qdrant Search node (nespojeno)
- AI Agent ima Vector Store Retriever slot prazno

Učenici samo: spajaju strelice, unose collection name, i pokreću.

### Workspace setup
- Svaki tim dobiva vlastiti n8n projekt (ne dijele isti workspace)
- Svaki tim dobiva vlastitu Qdrant collection prefix (`tim_a_`, `tim_b_`, itd.)
- Credentials (OpenAI API key) postavljeni globalno — učenici ih ne vide

### Dokumenti
- `tesla_ac_patent.pdf` — pripremljen, ~10 stranica, čist tekst (ne skenirani)
- `skola_vijest_[datum].pdf` — najnovija vijest sa školske stranice, printana u PDF
- `backup_doc.pdf` — neki tehnički članak kao rezerva

### Backup planovi
| Problem | Rješenje |
|---------|---------|
| n8n ne radi | ChatGPT + copy-paste Teslanog teksta u razgovor — demonstrira isti princip |
| OpenAI API limit | Prebaci credentials na Ollama endpoint (pripremiti unaprijed) |
| Nema interneta | Offline screenshotovi gotovog workflowa + live demo s lokalne mašine |
| Tim se zaglavilo | Ti preuzmeš workflow tog tima na projektoru, ostali gledaju |
| Qdrant greška | Obriši collection i ponovi insert — cleanup script u terminalu |

---

## Materijali za učenike (za pripremiti)

### Kartica s uputama (A5, printana)
```
KORACI:
1. Otvori n8n → tvoj workspace
2. Template 1: dodaj Memory node, spoji, testiraj
3. Template 2: prati voditelja korak po korak
4. Upload Tesla PDF → testiraj 3 pitanja
5. Upload vlastiti dokument → slobodni eksperiment

COLLECTION NAME: tim_[tvoje_ime]
n8n URL: [url]
```

### Test pitanja za Tesla dokument
1. Koji je broj patenta?
2. Koja je godina prijave?
3. Što Tesla navodi kao glavnu prednost?
4. Napiši sažetak u 2 rečenice.
5. Što bi se promijenilo da je chunk size bio 100 umjesto 500? *(za brže timove)*

---

## Flow kontrola

### Timing signali
- **@10 min** — svi moraju imati basic chat s memorijom. Ako ne, preskačeš korak 3 (sistemski prompt) i ideš dalje.
- **@20 min** — svi moraju vidjeti RAG dijagram i razumijeti što rade. Ako ne, usporiti — ovaj dio je konceptualno najvažniji.
- **@30 min** — barem 80% timova ima RAG koji vraća odgovor. Ostali mogu gledati i testirati na zajedničkom primjeru.
- **@35 min** — Tesla test gotov. Ako neki tim nije stigao, mogu raditi paralelno dok ti radiš finale demo.

### Ako kasni
1. Preskočiti sistemski prompt u Dijelu 1
2. Korak 2 (Text Splitter) — ti konfiguriraš, oni kopiraju
3. Finale: ti demonstriraš, oni ne uploadaju vlastiti dokument

### Ako ide brže
- Eksperimentiranje s chunk size: 100 vs 500 vs 1000 — koji daje bolje odgovore?
- Više dokumenata u istu collection — funkcionira li cross-document pretraživanje?
- Promijeniti sistemski prompt da AI odgovara kao Nikola Tesla u prvom licu

---

## Success criteria

**Radionica je uspješna ako:**
- Svi su vidjeli razliku basic chat vs RAG — praktično, ne samo pričano
- 80% timova je samostalno izgradilo pipeline
- Barem jedan "wow" moment s lokalnim dokumentom škole
- Učenici razumiju *zašto* svaki korak postoji (ne samo kako ga kliknuti)
