# GenAI u praksi: Razgovor s Teslinim patentima pomoću RAG arhitekture
*Prezentacija za 3E razred elektrotehničke škole - Festival znanosti 2026*

---

## Slide 1: Naslovni slide
**Naslov:** GenAI u praksi: Razgovor s Teslinim patentima pomoću RAG arhitekture
**Podnaslov:** Kako napraviti AI stručnjaka za Teslinu energiju
**Datum:** 21. travnja 2026
**Voditelj:** Marin Kepec

**Vizual:** Tesla coil + AI robot ikona

---

## Slide 2: Hook - Tesla vs. AI (1 min)
**Naslov:** Tesla je sanjao o bežičnom prijenosu energije...

**Sadržaj:**
- 1890-e: Tesla - bežični prijenos energije
- 2020-e: AI - bežični pristup znanju
- **Pitanje:** Kako biste objasnili ChatGPT-u što je Tesla coil?

**Vizual:** Tesla laboratorij 1890 vs. današnji data center

**Presenter notes:**
- Početi s pitanjem učenicima
- Pokazati da oboje koriste "nevidljive veze"

---

## Slide 3: Što je GenAI? (2 min)
**Naslov:** Generativna AI - "Inteligentni transformator"

**Sadržaj:**
- **Input:** Tekst pitanja (napon)
- **"Crna kutija":** LLM model (transformator)
- **Output:** Generirani tekst (struja)

**Analogija za elektrotehničare:**
- Token = najmanji "impuls" podataka
- Model = složeni elektronički sklop
- Training = "kalibracija" sklopovske logike

**Vizual:** Blok dijagram s elektrotehničkim simbolima

---

## Slide 4: Demo - ChatGPT o Tesli (2 min)
**Naslov:** Testirajmo ChatGPT uživo

**Live demo:**
- Pitanje: "Objasni Teslinu AC motor tehnologiju"
- Pokazati dobar odgovor
- **Zatim kritično pitanje:** "Koje su karakteristike Teslinog patenta iz 2025?"

**Očekivani rezultat:** ChatGPT će izmisliti nepostojeći patent

**Prezenter notes:**
- Namjerno postaviti "zamku" s budućim datumom
- Pokazati kako AI može "halucinirati"

---

## Slide 5: Problem - Knowledge Cutoff (1.5 min)
**Naslov:** Zašto AI ne zna sve?

**Ključni pojmovi:**
- **Knowledge cutoff** = datum kada je model prestao učiti
- **Halucinacije** = izmišljanje nepostojećih informacija
- **Statički model** = ne uči nove stvari nakon treninga

**Analogija:** Poput udžbenika iz 2020. koji ne zna o događajima iz 2024.

**Vizual:** Kalendar s "cutoff" linijom

---

## Slide 6: Rješenje - RAG arhitektura (3 min)
**Naslov:** RAG = Retrieval-Augmented Generation

**Komponente:**
- **R**etrieval = pronalaženje relevantnih dokumenata
- **A**ugmented = obogaćivanje pitanja kontekstom
- **G**eneration = stvaranje odgovora s novim znanjem

**Elektrotehnička analogija:**
- Dokumenti = kondenzatori (čuvaju podatke)
- Vektorska baza = komutator (selektira relevantne)
- LLM = pojačalo (obrađuje i pojačava signal)

**Vizual:** Shematski prikaz RAG procesa

---

## Slide 7: RAG u praksi - korak po korak (3 min)
**Naslov:** Kako RAG funkcionira?

**Koraci:**
1. **Unos dokumenta** → PDF s Teslinim patentima
2. **Chunking** → Dijeljenje na manje dijelove
3. **Embedding** → Pretvaranje u brojčane vektore
4. **Storage** → Čuvanje u vektorskoj bazi
5. **Query** → Postavljanje pitanja
6. **Retrieval** → Pronalaženje relevantnih dijelova
7. **Generation** → AI odgovor s kontekstom

**Vizual:** Flowchart s ikonama za svaki korak

---

## Slide 8: n8n - Vizualni workflow (2 min)
**Naslov:** n8n = "LEGO kocke" za AI

**Karakteristike:**
- **No-code** alat za povezivanje servisa
- **Node-based** = svaki čvor ima funkciju
- **Visual** = vidiš kako podaci teku
- **Real-time** = testiraš korak po korak

**Primjer workflow-a:**
PDF Input → Text Extract → Embedding → Vector Store → Chat

**Vizual:** Screenshot n8n sučelja s RAG workflow-om

---

## Slide 9: Energetska cijena AI (2 min)
**Naslov:** Koliko energije troši jedan AI odgovor?

**Činjenice:**
- **ChatGPT odgovor** ≈ 0.1-0.3 Wh
- **Google pretraživanje** ≈ 0.2-0.3 Wh
- **Email slanje** ≈ 4 Wh

**Tesla veza:**
- Tesla coil: ~1000W za demonstraciju
- 1 Tesla demo = 3000-10000 AI odgovora

**Pitanje za razmišljanje:** Kako optimizirati AI za manju potrošnju?

**Vizual:** Grafikon energetske potrošnje različitih aktivnosti

---

## Slide 10: Što ćemo danas napraviti? (2.5 min)
**Naslov:** Vaš zadatak - Postajite AI inženjeri!

**Cilj:**
Izgraditi RAG sustav koji može odgovoriti na pitanja o Teslinim izumima

**Alati:**
- **n8n** za workflow dizajn
- **Teslini patenti** kao baza znanja
- **OpenAI API** za generiranje odgovora
- **Qdrant** vektorska baza
- **Grafana** za praćenje potrošnje

**Timski rad:** 2-3 učenika po računalu

---

## Slide 11: Transition u radionicu (1 min)
**Naslov:** Idemo u lab!

**Što slijedi:**
- Pristup računalima
- Login u n8n sučelje
- Step-by-step izgradnja RAG sustava
- Testiranje s Teslinim pitanjima
- Optimizacija i eksperimentiranje

**Motivacija:** "Za 40 minuta ćete imati vlastiti AI sustav koji zna više o Tesli nego Wikipedia!"

**Vizual:** "Let's build!" s Tesla + AI ikonama

---

## Rezervni slideovi (ako treba)

### Backup Slide: Što je Vector Database?
**Objašnjenje vektora kroz elektrotehničke veličine:**
- Vektor = usmjerena količina (poput napona/struje)
- Svaka riječ postaje niz brojeva
- Slične riječi = slični vektori
- Pretraživanje = pronalaženje najsličnijih vektora

### Backup Slide: API troškovi
**Realni troškovi OpenAI API-ja:**
- 1000 tokena ≈ 0.002 USD
- Jedan odgovor ≈ 100-300 tokena
- Današnja radionica ≈ 2-3 USD ukupno

---

## Presenter Notes - Generalni savjeti

**Interakcija s učenicima:**
- Postaviti pitanja na početku svakog slajda
- Koristiti elektrotehničke analogije
- Ohrabriti pitanja tijekom prezentacije

**Timing management:**
- Maksimalno 20 minuta za prezentaciju
- Ostaviti 2-3 minute buffer za pitanja
- Ako kasni, preskočiti backup slideove

**Tesla tema:**
- Stalno vraćati na Tesla/energiju vezu
- Koristiti Tesla kao primjer kroz sve slideove
- Napomenuti 170. godišnjicu rođenja