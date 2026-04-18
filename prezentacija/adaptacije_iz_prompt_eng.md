# Adaptacije iz Prompt Engineering prezentacije

## Slideovi koji se mogu direktno iskoristiti/adaptirati

### 1. "Why Now? Perfect Storm" → "Zašto sada Tesla + AI?"
**Originalni sadržaj:** 3 faktora koji su omogućili AI revoluciju
**Tesla adaptacija:**
- **Podaci:** Tesla patenti digitalizirani i dostupni online
- **Algoritmi:** RAG tehnologija omogućava pristup povijesnim dokumentima
- **Računalna snaga:** Cloud serveri mogu procesirati Tesline dokumente u realnom vremenu

### 2. "AI Hierarchy" → "Gdje se nalazi naš Tesla chatbot?"
**Adaptacija za elektrotehničare:**
- AI ⊃ ML ⊃ GenAI ⊃ LLM ⊃ **Tesla RAG bot**
- Vizualno: elektrotehnički blok dijagram umjesto kružnog

### 3. "Problem: Limited Knowledge" → "Zašto ChatGPT ne zna o Teslinim patentima?"
**Direktna adaptacija:**
- Pokazati ChatGPT koji ne zna o specifičnim Teslinim patentima
- Uvesti problem knowledge cutoff-a
- **Rješenje:** RAG s Teslinim dokumentima

### 4. "Before & After Prompts" → "Loš vs. dobar RAG prompt"
**Tesla primjer:**
- ❌ Loš: "Reci mi o Tesla coil"
- ✅ Dobar: "Na temelju Teslinog patenta iz 1891., objasni principe rada Tesla coil-a i navedi specifičnu frekvenciju iz dokumenta"

## Novi slideovi inspirirani originalnom prezentacijom

### 5. "Tesla's Vision vs. Today's Reality" (inspiriran "AI isn't new" slide)
- 1890.: Tesla - bežični prijenos energije
- 2026.: AI - bežični prijenos znanja
- **Pitanje za publiku:** "Kako biste objasnili Tesli što je ChatGPT?"

### 6. "From Patents to Chatbot" (inspiriran "How LLMs Process Text")
**Korak-po-korak s Tesla dokumentima:**
1. 📄 Tesla patent PDF
2. ✂️ Chunking na paragrafe
3. 🔢 Embedding u vektore
4. 🗄️ Storage u Qdrant
5. ❓ Pitanje o Tesla coil-u
6. 🎯 Retrieval relevantnih dijelova
7. 🤖 AI odgovor s kontekstom

### 7. "Energy Cost of AI" (novi, Tesla-themed slide)
**Elektrotehnička perspektiva:**
- Jedan ChatGPT odgovor ≈ 0.2Wh
- Tesla coil demo ≈ 1000W
- **Zaključak:** 1 Tesla demo = 5000 AI odgovora o Tesli! ⚡

## Vizualni elementi za preuzimanje

### Ikonice i simboli:
- 🧠 Brain + ⚙️ Gear za AI objašnjenja
- 📚 Documents → 🤖 AI workflow
- ⚡ Lightning bolt za energiju/Tesla temu

### Boje i style:
- Naranžasta/crna kombinacija iz originalne prezentacije
- Dodati Tesla plavu (electric blue) za branding

### Layout elements:
- "Before & After" split-screen layout
- Timeline format za "How we got here"
- Numbered step process za RAG workflow

## Praktični workshop elementi

### Hands-on struktura (inspirirana original workshop-om):
1. **Setup check** (5 min) - pristup n8n sučelju
2. **Exercise 1:** Basic RAG (15 min) - Tesla PDF → chunks
3. **Exercise 2:** Query optimization (10 min) - različiti prompts
4. **Exercise 3:** Parameter tuning (10 min) - chunk size eksperimenti

### Live demo format:
- **Track 1:** n8n visual workflow (kao Jupyter u originalu)
- **Track 2:** Backup - ChatGPT + copy/paste Tesla tekst (kao free-tier)

## Elektrotehničke analogije (nova dodana vrijednost)

### RAG komponente kao elektronički sklop:
- **PDF dokument** = Kondenzator (pohranjuje podatke)
- **Chunking** = Multiplekser (dijeli signal)
- **Embedding** = A/D konverter (analogno → digitalno)
- **Vector DB** = Memorija (adresabilno pristupište)
- **Retrieval** = Komutator (selektira relevantne signale)
- **LLM** = Pojačalo (obrađuje i pojačava signal)

### Prompt engineering kao "tuning":
- **Temperature** = Gain control
- **Top-p** = Bandwidth filter
- **Max tokens** = Output limiter

## Predložene izmjene našeg template-a

### Dodati iz prompt eng prezentacije:
1. **Slide "Perfect Storm for Tesla AI"** (umjesto generičkog uvoda)
2. **"Knowledge Gap Problem"** s live ChatGPT demo-om
3. **"Vector Magic Explained"** s elektrotehničkim analogijama
4. **"Prompt Quality Matters"** s Tesla prije/poslije primjerima

### Zadržati naš fokus na:
- Tesla tema i 170. godišnjica
- Hands-on n8n workflow
- Energetska svjesnost
- Elektrotehničke analogije