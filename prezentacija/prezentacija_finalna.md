# GenAI u praksi: RAG arhitektura za privatne dokumente
*Prezentacija za Festival znanosti 2026 - 20 minuta*
*3E razred elektrotehničke škole - 21. travnja 2026*

---

## Slide 1: Naslovni slide (0.5 min)

### Sadržaj:
**Naslov:** GenAI u praksi: RAG arhitektura za privatne dokumente
**Podnaslov:** Kako firme stvarno koriste AI - specijalizirani sustavi koji rade s internim dokumentima
**Voditelj:** Marin Kepec
**Datum:** 21. travnja 2026, 13:00-14:00

### Presenter notes:
- Kratko pozdraviti, predstaviti se
- Naglasiti da će vidjeti kako se AI zaista koristi u firmama, ne samo ChatGPT
- Spomenuti da će nakon prezentacije imati priliku sami napraviti takav sustav
- Pitanje za zagrijavanje: "Tko od vas koristi ChatGPT ili neki drugi AI?"

---

## Slide 2: Hook - AI u firmama vs javni ChatGPT (2 min)

### Sadržaj:
**Naslov:** Kako firme koriste AI drugačije od nas?

**Problem:**
- Vi koristite ChatGPT za opće pitanja
- Firme trebaju AI koji zna o njihovim dokumentima
- Javni AI ne zna o privatnim informacijama

**Primjeri:**
- Pravna firma → AI koji zna sve njihove ugovore
- Bolnica → AI koji zna medicinske protokole
- Tehnička škola → AI koji zna najnovije vijesti s vaše stranice

### Presenter notes:
- Pitanje: "Što mislite, zašto ChatGPT ne zna o najnovijoj vijesti s stranice vaše škole?"
- Objasniti da ovo nije greška nego namjerno - privatnost i troškovi
- Naglasiti da ćemo danas pokazati kako se to rješava
- Povezati s njihovom budućnošću u IT industriji

---

## Slide 3: Perfect Storm - Zašto sada? (3 min)

### Sadržaj:
**Naslov:** Perfect Storm - Zašto AI eksplodira baš sada?

**Tri ključna faktora:**

1. **💾 PODACI (Data)**
   - Sve je digitalizirano (dokumenti, slike, video)
   - Internet pun sadržaja za treniranje AI modela
   - Kvalitetni dataseti dostupni

2. **⚡ RAČUNALNA SNAGA (Compute)**
   - GPU-ovi dovoljno snažni za treniranje
   - Cloud servisi dostupni svima
   - Paralelno procesiranje podataka

3. **🧠 ALGORITMI (Algorithms)**
   - Transformer arhitektura (2017)
   - Attention mechanism
   - Velike količine podataka + snažni algoritmi = ChatGPT

### Presenter notes:
- Naglasiti da nijedan od ova tri faktora sam po sebi nije dovoljao
- Analogija: kao što trebate sva tri za električni krug (izvor, vodič, trošilo)
- Pitanje: "Koji od ova tri faktora mislite da je najvažniji?"
- Povezati s time da će oni raditi s ovim tehnologijama u budućnosti

---

## Slide 4: Kako LLM radi - tokens i transformers (3 min)

### Sadržaj:
**Naslov:** Kako AI "razumije" tekst?

**Korak 1: Tokenizacija**
```
"Tesla je genij" → ["Tesla", "je", "gen", "ij"]
```

**Korak 2: Embeddings (brojevi)**
```
"Tesla" → [0.2, 0.8, 0.3, ...]
"genij" → [0.25, 0.75, 0.35, ...]
```

**Korak 3: Transformer obrada**
- Model "gleda" na sve tokene odjednom
- Računa veze između riječi
- Predviđa sljedeći token

**Rezultat:** Generirani odgovor

### Presenter notes:
- Objasniti da je ovo jako pojednostavljeno, ali bit je tu
- Naglasiti da model ne "razumije" kao čovjek, nego računa vjerojatnosti
- Analogija: kao autocomplete na mobitel, samo puno napredniji
- Pitanje: "Što mislite, zašto se zove 'transformer'?"

---

## Slide 5: LLM hijerarhija (2 min)

### Sadržaj:
**Naslov:** Hijerarhija AI modela

**GPT-4, Claude, Gemini** (Flagship modeli)
- Najnapredniji, najskuplji
- Koriste se za složene zadatke

**GPT-3.5, Llama** (Standard modeli)
- Brži, jeftiniji
- Dovoljni za većinu zadataka

**Specijalizirani modeli**
- Codex za programiranje
- DALL-E za slike
- Whisper za govor

### Presenter notes:
- Objasniti da izbor modela ovisi o zadatku i budžetu
- Analogija: kao izbor automobila - Lamborghini vs Golf vs bicikl
- Pitanje: "Za što biste koristili najjeftiniji model?"
- Naglasiti da ćemo danas koristiti OpenAI API

---

## Slide 6: AI troši PUNO energije! ⚡ (5 min)

### Sadržaj:
**Naslov:** Energetska realnost AI-ja - ENERGIJA tema festivala

**Koliko troši jedan ChatGPT odgovor?**
- ~2.9 Wh (Watt-sati) po upitu
- 1000 upita = 2.9 kWh

**Usporedbe:**
- Slanje emaila: ~4 Wh
- Google pretraživanje: ~0.3 Wh
- Gledanje YouTube 1 min: ~10 Wh

**Datacenter planovi:**
- Meta planira 4 nova datacentra do 2030
- Google investira $9.5 milijardi u datacentre 2024
- Microsoft partnership s nuklearnim elektranama

**Zašto GPU a ne CPU?**
- AI zadaci = paralelni
- GPU = tisuće malih jezgara
- CPU = nekoliko velikih jezgara

### Presenter notes:
- Ovo je direktna veza s temom festivala ENERGIJA
- Naglasiti da AI razvoj pokreće investicije u obnovljive izvore
- Pitanje: "Mislite li da je ova energetska potrošnja opravdana?"
- Povezati s Nikolom Teslom kao vizionarem energetike
- Spomenuti da je ovo jedan od najvećih tehničkih izazova današnjice

---

## Slide 7: AI u firmama - Problem privatnih dokumenata (3 min)

### Sadržaj:
**Naslov:** Problem: ChatGPT ne zna o vašim dokumentima

**Kako firme koriste AI:**
- 📝 Analiza dokumenata i izvještaja
- 💻 Pomoć u programiranju
- 🤖 Automatizacija procesa
- 📊 Stvaranje sadržaja

**Problem:**
- Javni AI modeli nemaju pristup privatnim dokumentima
- Sigurnosni rizici slanja osjetljivih podataka
- Knowledge cutoff - modeli ne znaju najnovije informacije

**Rješenja:**
1. **Custom training** - skupo, komplicirano
2. **RAG arhitektura** - praktično, brže ✅

### Presenter notes:
- Objasniti da ovo nije teoretski problem nego stvarni business izazov
- Pitanje: "Zašto mislite da firme ne mogu samo poslati dokumente ChatGPT-u?"
- Naglasiti sigurnosne i pravne aspekte
- Uvesti RAG kao elegantno rješenje

---

## Slide 8: RAG - Retrieval-Augmented Generation (2 min)

### Sadržaj:
**Naslov:** RAG = AI + Vaši dokumenti

**Kako RAG radi:**
```
1. 📄 Učitaj dokumente
2. ✂️  Podijeli na dijelove (chunks)
3. 🔢 Pretvori u brojeve (embeddings)
4. 💾 Spremi u bazu podataka
5. ❓ Korisnik pita pitanje
6. 🔍 Pronađi relevantne dijelove
7. 🤖 Pošalji AI-ju kontekst + pitanje
8. ✨ Generiraj odgovor s citatima
```

**Prednosti:**
- AI "čita" vaše dokumente u realnom vremenu
- Sigurno - dokumenti ostaju kod vas
- Ažurno - možete dodavati nove dokumente

### Presenter notes:
- Objasniti da je ovo kao "pametna tražilica + AI"
- Analogija: kao da AI ima pristup vašoj knjižnici
- Pitanje: "Što mislite koji je korak najvažniji?"
- Naglasiti da ćemo ovo implementirati za 40 minuta

---

## Slide 9: Transition - Što ćemo napraviti danas (2 min)

### Sadržaj:
**Naslov:** Napravit ćemo AI koji zna više od ChatGPT-a!

**Naš projekt:**
- 🎯 Cilj: RAG sustav koji čita Tesla patente
- 🛠️ Alat: n8n (vizualni workflow editor)
- 📄 Podaci: Tesla dokumenti + najnovija vijest s vaše škole
- ⚡ Rezultat: AI asistent specijaliziran za vaše potrebe

**Zašto Tesla dokumenti?**
- Praktičan primjer (ne glavna tema)
- Dostupni u PDF formatu
- Povijesni značaj za Festival znanosti

**Zašto n8n?**
- Vizualni pristup (drag & drop)
- Vidi se tok podataka između koraka
- Brže od programiranja

### Presenter notes:
- Pojasniti da Tesla tema je samo praktičan primjer
- Naglasiti da će naučiti tehniku koju mogu primijeniti na bilo koje dokumente
- Pitanje: "Koje dokumente bi vi voljeli 'učiti' AI-ju?"
- Motivirati za praktični dio - "Za 40 minuta ćete imati vlastiti AI sustav!"

---

## Slide 10: Završni slide - Idemo u radionicu! (1 min)

### Sadržaj:
**Naslov:** Ready? Idemo napraviti vaš prvi poslovni AI sustav! 🚀

**Što čeka:**
- ⏱️ 40 minuta hands-on rada
- 👥 Rad u timovima (2-3 osobe)
- 🖥️ n8n vizualni editor
- 🧪 Testiranje s pravim dokumentima

**Learning outcome:**
Razumijevanje kako firme stvarno koriste AI za rad s privatnim dokumentima

**Pitanje za razmišljanje:**
"Kako mislite da će se AI razvijati u sljedećih 5 godina?"

### Presenter notes:
- Kratko rekapitulirati ključne točke
- Naglasiti praktičnu vrijednost vještine
- Motivirati za aktivno sudjelovanje
- Pitanje o budućnosti AI-ja da ih stavi u mindset razmišljanja
- Transition: "Idemo u computer lab!"

---

## Backup slideovi (po potrebi)

### Backup 1: Što ako tehnologija ne radi?
**Alternativni plan:**
- ChatGPT + copy/paste Tesla dokumenta
- Isti learning outcome
- Fokus na prompt engineering

### Backup 2: Dodatni AI primjeri
**Još AI aplikacija u firmama:**
- Customer support chatbots
- Analiza sentiment-a u emailovima
- Automatsko pisanje izvještaja
- Code review pomoć

### Backup 3: Tehnički detalji RAG-a
**Za one koji pitaju više tehničkih detalja:**
- Vector databases (Qdrant)
- Similarity search algoritmi
- Embedding modeli
- Chunk size optimizacija

---

## Presenter notes - Generalni savjeti

### Timing po slideovima:
1. Naslovni: 0.5 min
2. Hook: 2 min
3. Perfect Storm: 3 min
4. LLM proces: 3 min
5. LLM hijerarhija: 2 min
6. Energetska realnost: 5 min
7. AI u firmama: 3 min
8. RAG objašnjenje: 2 min
9. Transition: 2 min
10. Završni: 1 min
**Buffer:** 1.5 min za pitanja

### Interakcija strategija:
- Svaki slide počinje pitanjem
- Praktični primjeri iz njihovog iskustva
- Povezivanje s budućnom karijerom u IT
- Energetska tema kroz cijelu prezentaciju

### Ključne poruke za zapamćivanje:
1. AI u firmama ≠ javni ChatGPT
2. RAG = praktično rješenje za privatne dokumente
3. AI troši puno energije - važna tema
4. Ovo su vještine za budućnost IT industrije