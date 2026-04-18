# GenAI u praksi: Razgovor s Teslinim patentima pomoću RAG arhitekture
*Updated prezentacija v2.0 - Integracija prompt engineering koncepata*
*3E razred elektrotehničke škole - Festival znanosti 2026*

---

## Slide 1: Naslovni slide
**Naslov:** GenAI u praksi: Razgovor s Teslinim patentima pomoću RAG arhitekture
**Podnaslov:** Kako napraviti AI stručnjaka koji zna više o Tesli nego Wikipedia
**Datum:** 21. travnja 2026, 13:00-14:00
**Voditelj:** Marin Kepec

**Vizual:** Tesla coil + AI neural network s electric arcs
**Pozadina:** Naranžasta (Infobip style) s Tesla lightning elements

**Interakcija:** "Tko od vas zna što je Tesla coil?" (provjeri predznanje)

---

## Slide 2: Tesla's Vision vs. Today's Reality (2 min)
**Naslov:** Tesla je sanjao o bežičnom prijenosu energije... Danas AI ima bežični pristup znanju ⚡

**Split-screen layout:**
**LIJEVO (1890-e):**
- Tesla coil u laboratoriju
- "Wireless Power Transmission"
- 50Hz frekvencije, visoki napon

**DESNO (2020-e):**
- AI data center
- "Wireless Knowledge Access"
- Token frekvencije, neural processing

**Hook pitanje:** "Kako biste objasnili Tesli što je ChatGPT?"
**Elektrotehnička veza:** "Tesla je radio s 50Hz, AI radi s token-frequencies"

**Presenter notes:** Početi s pitanjem, povezati frequency domain s oba koncepta

---

## Slide 3: Što je GenAI? - Inteligentni trofazni transformator (2.5 min)
**Naslov:** GenAI = Pametni transformator za tekst ⚙️

**Elektrotehnička analogija:**
```
INPUT           TRANSFORMATOR          OUTPUT
Tekst pitanja  ────→  LLM model  ────→  Generirani odgovor
(napon)              (trofazni)          (modulirana struja)
```

**Ključni koncepti za elektrotehničare:**
- **Token** = najmanji "impuls" podataka (kao sample u A/D konverteru)
- **Model** = složeni elektronički sklop (blackbox s input/output)
- **Training** = "kalibracija" sklopovskih parametara

**Live pitanje publici:** "Što se događa kad transformer ima loš isolation?"
**Odgovor:** "AI 'hallucination' je kao electrical noise u output-u!"

**Vizual:** Blok dijagram s elektrotehničkim simbolima, Tesla coil kao input

---

## Slide 4: Knowledge Cutoff Problem - Tesla Mystery (2 min)
**Naslov:** Zašto ChatGPT ne zna o Teslinim specifičnim patentima? 🤔

**Live demo setup:**
```
DEMONSTRACIJA:
Pitanje za ChatGPT: "Opiši Teslin patent broj 645576 iz 1900. godine"

Očekivani odgovor: "Nemam pristup specifičnim brojevima patenata..."
```

**Problem objašnjenje:**
- **Knowledge cutoff** = datum kada je model prestao učiti
- **Training data** = ne uključuje sve Tesline dokumente
- **Halucinacije** = model "izmišlja" nepostojeće patente

**Analogija:** "Poput udžbenika iz 1990. koji ne zna o modernim mikrokontolerima"

**Interakcija:** "Jeste li ikad googlali nešto pa nije bilo odgovora?"

---

## Slide 5: Perfect Storm for Tesla AI ⛈️ (3 min)
**Naslov:** Zašto tek SADA možemo razgovarati s Teslinim patentima?

**Tesla's Perfect Storm - tri ključna faktora:**

### 📚 **01: DIGITALIZIRANI DOKUMENTI (Fuel for AI)**
- Tesla patenti dostupni online (Google Patents, Archive.org)
- 100+ godina inovacija u PDF formatu
- Pretraživost povijesnih dokumenata

### ⚡ **02: CLOUD COMPUTING POWER (Processing Power)**
- n8n workflow na remote serverima
- API pozivi prema OpenAI/Anthropic u real-time
- Procesat gigabajte Tesla dokumenata u sekundama

### 🧠 **03: TRANSFORMER ALGORITMI (Smarter Models)**
- RAG arhitektura (2020+) - kombiniranje dokumenata s AI-jem
- "Attention mechanism" - razumijevanje konteksta
- Specifičnost umjesto generalnosti

**Ključna formula:** Tesla dokumenti + Cloud snaga + RAG algoritmi = **Tesla AI stručnjak**

**Pitanje za razmišljanje:** "Što bi Tesla mislio o tome da se njegove ideje 'čitaju' elektronikim mozgom?"

---

## Slide 6: RAG = Pametni elektronički sklop za Tesla znanje (3.5 min)
**Naslov:** RAG arhitektura kao elektronički sustav 🔌

**Elektrotehnička analogija - signal processing chain:**
```
[Tesla PDF] → [Chunker] → [A/D Conv.] → [Memory] → [Selector] → [Amplifier] → [Output]
   Input      Multiplexer  Embeddings    Qdrant     Retrieval     LLM        Odgovor
```

**Komponente objašnjene:**
1. **PDF dokument** = Analogni signal (kontinuiran tekst)
2. **Chunking** = Multiplexer (dijeli signal na kanale)
3. **Embedding** = A/D konverter (tekst → brojevi)
4. **Qdrant** = Adresabilna memorija (storage i quick access)
5. **Retrieval** = Komutator (selektira relevantne signale)
6. **LLM** = Pojačalo s feedback (obrađuje i strukturira)

**RAG vs. obični ChatGPT:**
- **Obični LLM:** Closed-loop system (samo internal memory)
- **RAG:** Open-loop s external feedback (Tesla dokumenti kao reference)

**Demo preview:** "Ovako će izgledati naš Tesla workflow u n8n!"

---

## Slide 7: Voltage Drop in Prompts - Kvaliteta = Napon (2.5 min)
**Naslov:** Kvaliteta prompta = Napon u strujnom krugu ⚡

**Elektrotehnička analogija:**

### ❌ **NIZAK NAPON (Loš prompt):**
```
Input: "Reci mi o Tesla coil"
Signal quality: Weak, generic
Output: Generički odgovor, puno "šuma"
```

### ✅ **VISOK NAPON (Dobar prompt):**
```
Input: "Na temelju Teslinog patenta 645576, objasni rezonantnu
       frekvenciju Tesla coil-a i kako se izračunava induktivnost
       primarnog namota. Koristi formule iz originalnog dokumenta."
Signal quality: Strong, specific
Output: Precizan, stručan odgovor s formulama
```

**Before/After demonstracija:**
- Pokazati oba prompta live u ChatGPT/Claude
- Naglasiti razliku u kvaliteti odgovora

**Ključna pouka:** "Prompt engineering = Electrical engineering - oba trebaju preciznu kontrolu!"

---

## Slide 8: n8n - Visual Circuit Designer za AI (2 min)
**Naslov:** n8n = "Fritzing za AI workflow" 🔧

**Zašto n8n za elektrotehničare:**
- **Visual programming** - kao što crtate sheme u Fritzing/Eagle
- **Node-based** = svaki node je komponenta (IC, resistor, etc.)
- **Real-time testing** = testiranje signala korak-po-korak
- **No-code** = fokus na logiku, ne na syntax

**n8n vs. tradicionalno programiranje:**
```
TRADICIONALNO:           n8n VISUAL:
if (input == "Tesla"):   [Tesla Trigger] → [PDF Process] → [AI Response]
  process_pdf()               ↓                ↓             ↓
  call_ai()              Visual nodes    Drag & drop   Live testing
  return result
```

**Tesla workflow preview:**
- Pokazati screenshot osnovnog RAG workflow-a
- "Za 40 minuta ćete sami spojiti ove 'komponente'!"

**Pitanje:** "Kakav je najveći 'workflow' koji ste napravili u elektronici?"

---

## Slide 9: Energy Accounting - Tesla bi bio ponosan ⚡ (2 min)
**Naslov:** Koliko energije troši jedan razgovor s Teslom?

**Energetska analiza:**
- **ChatGPT odgovor:** ~0.2 Wh
- **Tesla coil demonstracija:** ~1000W (za 1 minutu = 16.7 Wh)
- **Matematika:** 1 Tesla demo = 83 AI pitanja o Tesli!

**Dodatne usporedbe:**
- **Slanje email-a:** ~4 Wh (20x više od AI odgovora)
- **Google pretraživanje:** ~0.3 Wh (slično AI-ju)
- **Gledanje YouTube 1 min:** ~10 Wh (50x više)

**Tesla twist:**
"Tesla je sanjao o besplatnoj energiji za sve - danas AI omogućuje
'besplatno' znanje za sve. Ironija: koristimo energiju da pristupimo
Teslinim idejama o energiji!"

**Pitanje za razmišljanje:** "Je li ovo ono što je Tesla zamišljao kad je govorio o 'world wireless'?"

**Vizual:** Energetski dijagram s Tesla coil-om i data center-om

---

## Slide 10: Što ćemo danas napraviti - Tesla AI inženjer! (2 min)
**Naslov:** Postajte Tesla AI inženjeri za 40 minuta! 🚀

**Vaš zadatak - izgraditi Tesla RAG sustav:**

**Input:** Teslini patenti (AC motor, wireless power, Tesla coil)
**Output:** AI asistent koji zna Tesla povijest bolje od Wikipedije

**Alati za workshop:**
- **n8n visual workflow** - kao PCB designer
- **Tesla dokumenti** - 3-4 ključna patenta
- **OpenAI API** - neural processing power
- **Qdrant vektorska baza** - high-speed storage
- **Grafana monitoring** - real-time resource tracking

**Timski rad:** 2-3 učenika po računalu (kao lab partneri)

**Success criteria:**
✅ Workflow uspješno spoji sve komponente
✅ Odgovori na Tesla pitanja s citatima iz dokumenata
✅ Eksperiment s različitim parametrima
✅ Razumije energy/performance trade-off

---

## Slide 11: Two-Track Workshop Structure (1.5 min)
**Naslov:** Idemo u lab - dva pristupa! 🔬

**Track 1: Visual Engineers (n8n)**
```
✅ Za one koji vole visual programming
✅ Drag & drop workflow building
✅ Real-time testing
✅ Full RAG pipeline experience
```

**Track 2: Backup Engineers (ChatGPT + Tesla docs)**
```
✅ Ako tehničko ne radi
✅ Copy/paste Tesla dokumenti
✅ Prompt optimization focus
✅ Same learning outcomes
```

**Help each other! 💛** - Tesla je bio kolaborativan, budite i vi!

**Transition:** "Za 40 minuta ćete razgovarati s Teslom preko AI-ja. Ready?"

**Vizual:** Split screen - n8n interface vs ChatGPT interface, oboje s Tesla temom

---

## Rezervni slideovi (backup/timing adjustment)

### Backup Slide 1: Vector Magic Explained
**Za slučaj da treba pojašnjenje vektora:**
```
Kako AI "razumije" Tesla coil?

"Tesla" → [0.2, 0.8, 0.3, 0.1, 0.5]
"coil"  → [0.25, 0.75, 0.35, 0.15, 0.48]
"inductor" → [0.22, 0.78, 0.32, 0.12, 0.51]

Slični koncepti = slični brojevi!
Kao što slični otpori imaju slične boje na shemi.
```

### Backup Slide 2: Troubleshooting Guide
**Za slučaj tehničkih problema:**
- n8n ne radi → prebaci na Track 2
- API limit → koristi lokalni model
- Internet spor → offline dokumenti
- "Nešto ne radi" → Help each other!

### Backup Slide 3: Tesla Fun Facts
**Za motivaciju ako workshop prestane:**
- Tesla je imao 300+ patenata
- Govorio je 8 jezika
- Zamislio je smartphone 1926.
- "Danas gradimo ono što je on sanjao!"

---

## Presenter Notes - Generalni savjeti

### **Timing per slide (ukupno 20 min):**
1. **Naslovni slide:** 0.5 min
2. **Tesla vs AI:** 2 min
3. **GenAI transformer:** 2.5 min
4. **Knowledge cutoff:** 2 min
5. **Perfect Storm:** 3 min
6. **RAG elektronički:** 3.5 min
7. **Voltage prompts:** 2.5 min
8. **n8n visual:** 2 min
9. **Energy accounting:** 2 min
10. **Workshop zadatak:** 2 min
11. **Track struktura:** 1.5 min
**Buffer:** 1.5 min za pitanja/flexibility

### **Interakcija strategija:**
- **Svaki slide počinje pitanjem** za publiku
- **Elektrotehničke analogije** kroz sve objašnjenje
- **Live demo elementi** kad god moguće
- **"Help each other!"** kultura poticanja

### **Tesla tema održavanje:**
- **Stalno vraćanje na Tesla/energiju** vezu
- **170. godišnjica** spomenuti 2-3 puta
- **Energetska svjesnost** kroz cijelu prezentaciju
- **Praktični fokus** - "what would Tesla do?"

### **Backup plan management:**
- **Ako kasni:** preskočiti backup slideove
- **Ako brzo:** dodati tech details u main slideove
- **Ako ne radi tech:** fokus na koncepte i analogije
- **Uvijek završiti na pozitivnoj noti:** "Idemo napraviti nešto što bi Tesla volio!"