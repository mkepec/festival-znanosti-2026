# GenAI u praksi: RAG arhitektura za privatne dokumente
*Prezentacija za Festival znanosti 2026 — 20 minuta*
*3E razred Tehničke škole — 21. travnja 2026*

---

## Struktura i timing

| # | Slide | Trajanje |
|---|-------|----------|
| 1 | Naslov + zagrijavanje | 1 min |
| 2 | Hook — problem koji svi imaju | 2 min |
| 3 | Zašto AI eksplodira baš sada? | 2 min |
| 4 | Kako AI zapravo radi | 3 min |
| 5 | AI i energija — skupa stvar | 3 min |
| 6 | Kako firme koriste AI | 2 min |
| 7 | Problem privatnih dokumenata | 1 min |
| 8 | Rješenje: RAG | 2 min |
| 9 | Što ćemo napraviti danas | 2 min |
| 10 | Idemo! | 1 min |
| — | Buffer za pitanja | 1 min |
| **Ukupno** | | **20 min** |

---

## Slide 1: Naslov (1 min)

### Sadržaj
**Naslov:** Napravi AI koji zna tvoje dokumente
**Podnaslov:** RAG arhitektura u praksi — od nule za 40 minuta
**Voditelj:** Marin Kepec — DevOps inženjer, Infobip
**Datum:** 21. travnja 2026

### Vizualizacija
Minimalan slide. Samo naslov, ime, datum. Bez bullet točaka.
> **AI image prompt:** "Clean dark background, glowing neural network nodes connecting to a document icon, professional tech aesthetic, no text"

### Speaker notes
Dobrodošli. Ja sam Marin, radim kao DevOps inženjer u Infobipu — to je hrvatska tech firma koja šalje milijarde poruka dnevno. Svaki dan radim s AI sustavima u produkciji.

Za sat vremena vi ćete imati vlastiti AI koji može odgovarati na pitanja o dokumentima koje vi odaberete. Ne demo koji ja pokrećem — nego sustav koji ste vi sami izgradili.

Ali prvo — tko od vas koristi ChatGPT ili neki AI alat? [SHOW HANDS] [PAUSE — primjetiti koliko ruku]

Super. Znači znate što AI može. Danas ćemo vidjeti što ChatGPT *ne može* — i kako to popraviti.

---

## Slide 2: Hook — problem koji svi imaju (2 min)

### Sadržaj
**Naslov:** ChatGPT ne zna nešto što vi znate

**Jedan pokus:**
Pitajte ChatGPT: *"Što se događa u Tehničkoj školi Virovitica ovaj tjedan?"*

**Odgovor:** "Nemam pristup trenutnim informacijama..."

**Zašto?**
- ChatGPT uči na javnim podacima do određenog datuma
- Vaša škola, vaši dokumenti, vaše interne informacije — nisu tamo
- To nije greška. To je namjerno.

**Ali firme trebaju AI koji ZNA njihove podatke:**
- Pravna firma → AI koji čita njihove ugovore
- Bolnica → AI koji poznaje njihove protokole
- Vi danas → AI koji čita dokumente koje vi uploadate

### Vizualizacija
**Lijeva strana:** ikona ChatGPT s oblačićem "Ne znam za taj dokument"
**Desna strana:** isti AI + ikona dokumenta s oblačićem "Odgovor je na stranici 3..."
> **Tip:** jednostavni before/after dijagram, dvije kolone

### Speaker notes
Zamislite ovo: vi radite u bolnici. Imate 500 stranica medicinskih protokola. Htjeli biste AI koji može odmah odgovoriti "Koji je protokol za pacijenta s alergijom na penicilin?"

Pošaljete dokument ChatGPT-u? [PAUSE] Problem: 500 stranica je previše za jedan razgovor. I svaki put kad zatvorite prozor — AI zaboravi sve. I vaši interni protokoli nisu za javnost.

Firme se s ovim susreću svaki dan. Danas ćemo vidjeti kako se to profesionalno rješava.

---

## Slide 3: Zašto AI eksplodira baš sada? (2 min)

### Sadržaj
**Naslov:** Zašto 2022., a ne 2010.?

**Tri stvari su se poklopile:**

**1. PODACI**
Internet je postao ogroman — milijarde stranica teksta za učenje

**2. RAČUNALNA SNAGA**
GPU čipovi postali dovoljno snažni (i dostupni u cloudu)

**3. ALGORITMI**
2017. — Transformer arhitektura. Ovo je bila prekretnica.

*Nijedan od ova tri faktora sam nije dovoljan. Trebala su se sva tri.*

### Vizualizacija
**Venn dijagram s tri kruga:** Podaci / Compute / Algoritmi — s ChatGPT-om u presjeku
> **AI image prompt:** "Three overlapping circles Venn diagram, labeled Data, Compute, Algorithms, with a glowing AI brain icon in the center intersection, dark tech style"

### Speaker notes
ChatGPT nije iznenađenje. Istraživači su *znali* da je moguć — samo su čekali da se poklopi sve troje.

Analogija iz elektrotehnike: imate izvor napona, ali bez vodiča i trošila — struja ne teče. Trebate sva tri. [PAUSE]

2010. — podaci su bili tu. Algoritmi su bili OK. Ali GPU-ovi nisu bili dovoljno snažni i jeftini. 2022. — sve troje je sazrelo istovremeno.

Pitanje: koji od ova tri faktora mislite da je danas najveći bottleneck za AI razvoj? [PAUSE — čuti 1-2 odgovora]

---

## Slide 4: Kako AI zapravo radi (3 min)

### Sadržaj
**Naslov:** AI ne razumije — računa

**Korak 1 — Tokenizacija:**
`"Tesla je genij"` → `["Tesla", " je", " gen", "ij"]`
*Tekst se reže na komadiće*

**Korak 2 — Embeddings:**
`"Tesla"` → `[0.82, 0.14, 0.93, ...]` (tisuće brojeva)
*Svaki token postaje točka u prostoru — slične riječi su blizu*

**Korak 3 — Transformer:**
Model gleda SVE tokene odjednom i računa koji utječu jedan na drugog

**Rezultat:**
Predviđanje sljedećeg tokena — iznova i iznova — dok ne dobijete odgovor

### Vizualizacija
**Dijagram toka:** Tekst → Tokeni (vizualno izrezani) → Vektori (točke u 2D prostoru, "struja" i "elektricitet" blizu) → Transformer box → Odgovor
> **Tip:** Posebno moćan vizual: 2D scatterplot gdje su "kralj", "kraljica", "muškarac", "žena" raspoređeni geometrijski ispravno

### Speaker notes
Najvažnija rečenica danas: AI ne razumije što pišete. On predviđa koji token najvjerojatnije dolazi sljedeći, baziran na svemu što je vidio u treningu.

To zvuči banalno — ali to je dovelo do GPT-4, Claudea, Geminia.

Embeddings su zanimljivi: "kralj" minus "muškarac" plus "žena" — u vektorskom prostoru dobijete "kraljica". Matematika na riječima. [PAUSE]

Ovo je bitno jer ćemo embeddings koristiti u radionici — kad budete pretvarali dokumente u vektore za pretraživanje.

Autocomplete analogija: vaš mobitel predlaže sljedeću riječ dok pišete. ChatGPT radi isto — samo s puno više konteksta i puno boljim modelom.

---

## Slide 5: AI i energija — skupa stvar (3 min)

### Sadržaj
**Naslov:** Svaki vaš ChatGPT upit košta struju

**Jedan odgovor ChatGPT-a:**
~0.001 - 0.01 kWh (ovisno o duljini)

**Za usporedbu:**
- Google pretraživanje: ~0.0003 kWh (10-30x jeftinije)
- Slanje emaila: ~0.00002 kWh
- Punjenje mobitela: ~0.005 kWh

**Zašto je AI toliko skup?**
GPU farme rade 24/7 — tisuće čipova paralelno

**Investicije koje to pokreće:**
- Microsoft + nuklearna elektrana Three Mile Island (2024.)
- Meta gradi datacentre vrijedne $65 milijardi (2025.)
- Google: svaki novi datacenter treba vlastitu elektranu

**GPU vs CPU:**
GPU = tisuće malih jezgara (paralelno) → savršeno za AI matrice
CPU = nekoliko jakih jezgara (serijalno) → loše za AI

### Vizualizacija
**Bar chart usporedba:** ChatGPT upit / Google search / Email / Punjenje mobitela — vizualno dramatična razlika
> **AI image prompt:** "Aerial view of massive data center at night, glowing with lights, surrounded by cooling units, photorealistic"

> **Tip:** Dodati kontekst za Festival ENERGIJA: "Ovo je zašto AI i energetika postaju neodvojive teme"

### Speaker notes
Pitanje: koliko ChatGPT upita napravite dnevno? [PAUSE — čuti odgovore]

Pomnožite to s 100 milijuna korisnika. Svaki dan. To je ogromna potrošnja energije.

Microsoft je doslovno reaktivirao nuklearnu elektranu Three Mile Island — onu istu koja je bila scena nuklearne nesreće 1979. Zašto? Jer AI datacentri trebaju stabilnu, ogromnu količinu struje, i nuklearka je jedina koja može pratiti taj rast. [PAUSE]

Ovo je direktna veza s temom festivala — ENERGIJA. AI razvoj ne možete odvojiti od energetskih pitanja. To su jedni od najvećih inženjerskih izazova sljedećeg desetljeća.

Za vas koji ćete raditi u IT-u — ovo je tema koja će biti sve važnija.

---

## Slide 6: Kako firme koriste AI danas (2 min)

### Sadržaj
**Naslov:** AI u produkciji — što firme zapravo rade

**4 glavne primjene:**

**Kodiranje**
GitHub Copilot, Cursor — AI piše i pregledava kod
→ Programeri su 30-55% produktivniji (GitHub studija, 2023.)

**Dokumenti i izvještaji**
Analiza ugovora, sažimanje sastanaka, pisanje specifikacija

**Podrška korisnicima**
AI chatbotovi koji rješavaju 60-80% upita bez čovjeka

**Automatizacija procesa**
Workflow alati poput n8n-a (koji ćemo danas koristiti)

### Vizualizacija
**2x2 grid** s ikonama za svaku kategoriju i jednim konkretnim brojem/primjerom po kvadrantu
> **Tip:** Zadržati kratko — ovo je kontekst, ne glavni sadržaj

### Speaker notes
Ovo nije budućnost. Ovo se događa sada, u firmama gdje ćete vi raditi.

U Infobipu gdje ja radim — AI pregledava kod, piše dokumentaciju, i pomaže s customer support ticketima. To je stvarnost enterprise IT-a danas.

Ali sve ove primjene imaju jedan zajednički problem... [PAUSE — prijeđite na sljedeći slide bez da dovršite rečenicu]

---

## Slide 7: Problem privatnih dokumenata (1 min)

### Sadržaj
**Naslov:** Ali — ChatGPT ne zna vaše podatke

**Zašto firme ne mogu samo koristiti ChatGPT:**
- Interni dokumenti su povjerljivi → ne smiju izaći van
- Knowledge cutoff → model ne zna što se dogodilo prošli tjedan
- Kontekst limit → ne možete poslati 10.000 stranica u jedan razgovor

**Dva rješenja:**
| | Fine-tuning | RAG |
|---|---|---|
| Trošak | $$$$ | $ |
| Brzina | Tjedni | Sati |
| Ažurnost | Zamrznut | Real-time |
| Preporučeno | Rijetko | **Da** ✅ |

### Vizualizacija
Tablica gore je dovoljno — clean i čitljiv kontrast

### Speaker notes
Fine-tuning je kao školovanje novog zaposlenika — traje, košta, i kad se pojave novi dokumenti moraš opet sve ispočetka.

RAG je kao dati zaposleniku pristup knjižnici — kad nešto treba, ode potraži, pročita, i odgovori. Brzo, jeftino, uvijek ažurno.

---

## Slide 8: Rješenje — RAG arhitektura (2 min)

### Sadržaj
**Naslov:** RAG = AI + vaši dokumenti, u realnom vremenu

**Dvije faze:**

**Faza 1 — Indeksiranje (radite jednom):**
Dokument → Izreži na dijelove → Pretvori u vektore → Spremi u vektorsku bazu

**Faza 2 — Pretraživanje (svaki upit):**
Pitanje → Pretvori u vektor → Pronađi slične dijelove → Pošalji kontekst + pitanje AI-ju → Odgovor

**Rezultat:** AI koji odgovara točno i citira izvor

### Vizualizacija
**Dijagram toka u dva reda:**
- Gornji red (plavi): PDF → Chunker → Embeddings → Qdrant (vektorska baza)
- Donji red (zeleni): Pitanje → Embeddings → Similarity Search → LLM → Odgovor s citatom

> **AI image prompt:** "Clean flowchart diagram showing document going through processing pipeline into a database, then a query retrieving relevant chunks and feeding into a chat interface, minimal flat design, blue and green color scheme"

> **Napomena:** Ovo je isti dijagram koji će studenti vidjeti kao n8n workflow — koristite isti vizualni jezik

### Speaker notes
Ključna intuicija: embeddings koje smo vidjeli za "Tesla" i "genij" — ista stvar se događa s vašim dokumentima.

Kad pitate "Što Tesla kaže o izmjeničnoj struji?" — vaše pitanje se pretvori u vektor, i baza vrati najsličnije dijelove dokumenta. Taj dio onda ide AI-ju kao kontekst.

AI ne "čita" cijeli dokument svaki put. Samo relevantne dijelove. To je brzo i jeftino.

Ono što ćete za 40 minuta izgraditi u n8n-u — to je točno ova arhitektura, vizualno. Svaki box koji vidite ovdje bit će jedan node u vašem workflowu.

---

## Slide 9: Što ćemo napraviti danas (2 min)

### Sadržaj
**Naslov:** Za 40 minuta — vaš vlastiti RAG sustav

**Alat:** n8n — vizualni workflow editor
*Drag & drop, bez pisanja koda, vidi se tok podataka*

**Koraci koje ćete napraviti:**
1. Osnovni AI chat (5 min)
2. Dodavanje memorije razgovora (10 min)
3. Upgrade na RAG — dodavanje dokumenta (15 min)
4. Test s Teslinim patentom (5 min)
5. **Finale:** uploadate vlastiti dokument i chatate s njim (5 min)

**Na kraju:**
Vaš AI zna nešto što javni ChatGPT ne zna — jer vi ste mu to pokazali.

### Vizualizacija
**Screenshot n8n sučelja** s označenim nodovima koji odgovaraju koracima (ili skica ako screenshot nije dostupan)
> Ovo je najvažniji "preview" koji ih motivira — neka izgleda stvarno i ostvarivo

### Speaker notes
n8n je alat koji se koristi u pravim firmama za workflow automatizaciju. Nije igračka.

U pravim produkcijskim sustavima iza ovoga stoji Python i LangChain — ali vizualni pristup je savršen za razumijevanje arhitekture jer *vidite* kako podaci teku između koraka.

Radit ćete u parovima. Ja ću voditi na projektoru, korak po korak. Nema greške koja se ne može popraviti.

Pitanje koje ću vas pitati na kraju: "Koji dokument biste vi voljeli uploadati u vlastiti RAG sustav?" [PAUSE — neka razmisle]

---

## Slide 10: Idemo! (1 min)

### Sadržaj
**Naslov:** Tri stvari koje ste danas naučili

1. **AI ne razumije — računa** vjerojatnosti sljedećeg tokena
2. **AI troši ozbiljnu energiju** — i to pokreće milijardne investicije
3. **RAG = praktično rješenje** za AI koji zna vaše podatke

**Za 40 minuta:** Imate vlastiti sustav koji rade prave firme.

*"The best way to understand a technology is to build it."*

### Vizualizacija
Čist slide. Tri boda, citat. Nikakav clutter.

### Speaker notes
Brzo ponovimo — ne zato što ne vjerujem da ste zapamtili, nego da stavimo kontekst za ono što dolazi.

[ČITATI TOČKE NAGLAS — kratko]

Ono što ćete napraviti danas nije školski zadatak. Ovo je arhitektura koju koriste Infobip, Google, Microsoft — samo vi ćete je izgraditi u jednom satu.

Idemo u computer lab. [PAUZA] Pitanja možete postaviti i za vrijeme radionice.

---

## Backup slideovi

### Backup A: Što ako n8n ne radi?
**Plan B:**
- ChatGPT + direktno lijepljenje Teslanovog teksta u razgovor
- Demonstrira isti princip: AI s kontekstom vs. bez
- Fokus prebaciti na prompt engineering tehnike

### Backup B: Dublje u RAG tehničke detalje
*(Za studente koji pitaju više)*
- **Chunk size:** Manji = precizniji, veći = više konteksta. Trade-off.
- **Similarity search:** Cosine distance između vektora
- **Reranking:** Nakon dohvata, drugi model sortira po relevantnosti
- **Qdrant:** Open-source vektorska baza, self-hosted, GDPR-friendly

### Backup C: Karijere u AI/IT
*(Ako ostane vremena ili pitaju o budućnosti)*
- Prompt engineer, ML engineer, AI product manager — novi poslovi
- DevOps + AI = MLOps — rastuće područje
- Svaki developer danas treba znati koristiti AI alate
- Croatia: Infobip, Rimac, Gideon Brothers — sve firme traže AI znanje

---

## Opće napomene za izvedbu

### Interakcijska strategija
Svaki slide počinje pitanjem ili izjavom koja provocira odgovor — nikad objašnjenjem. Studenti moraju govoriti, ne samo slušati.

### Timing discipline
- Slide 5 (energija) ima tendenciju razvlačenja — cut ako kasnite
- Slide 6 i 7 mogu se spojiti u 2 minute ako je potrebno
- Slide 9 (preview radionice) ne smije biti kraći od 1.5 min — motivacija je ključna

### Energetska tema kao nit vodilja
Ne tretirati energiju kao poseban topic. Provući kroz cijelu prezentaciju:
- Slide 3: GPU compute = energija
- Slide 5: direktno
- Slide 8: RAG je efikasniji od fine-tuninga (manji energy footprint)
