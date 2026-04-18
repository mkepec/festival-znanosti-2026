# Finalni plan radionice - Hands-on RAG s n8n (40 min)

## 🎯 Cilj radionice
Pokazati praktičnu razliku između osnovnog AI chat-a i RAG-enhanced AI-ja kroz vizualni workflow u n8n-u.

**Ključna poruka:** "Ovo je kako firme stvarno koriste AI - s privatnim dokumentima."

---

## 🔧 Tehnička priprema unaprijed

### **n8n setup na Hetzner serveru:**
- **Workflow Template 1:** Osnovni OpenAI chat (sve podešeno)
- **Workflow Template 2:** RAG setup (polupripremljen)
- **Multi-user access** - svaki tim svoj workspace
- **Qdrant vector database** postavljena i testirana

### **Dokumenti za upload:**
- **Tesla patent** - kao glavni primjer
- **Najnovija vijest s stranice njihove škole** - za "wow" faktor na kraju
- **Backup dokumenti** ako nešto ne radi

---

## 📊 Struktura radionice (40 min)

### **Dio 1: Osnovni AI Chat** (15 min)

#### **Demo 1.1: Osnovni chat** (5 min)
- Pokazati n8n kao **vizualni no-code tool** za workflow automatizaciju
- **Objašnjenje:** "U praksi se koristi Python + LangChain, ali ovo je vizualnije"
- Demonstracija: pitanje → OpenAI node → odgovor
- **Naglasiti:** Tok podataka između nodeova je vidljiv

#### **Hands-on 1.2: Dodavanje memorije** (10 min)
**Zadatak učenika:**
- Dodati **Chat Memory node** (ja ću pripremiti upute)
- Podesiti history na 10 poruka (umjesto 3)
- **Test:** Pitati nešto, zatim referencirati prethodno pitanje

#### **Demo 1.3: Sistemski prompt** (margina)
- Pokazati gdzie se upisuje sistemski prompt
- **Primjer:** "Striktno ne izmišljaj ako nemaš točnu informaciju"

### **Dio 2: Problem demonstracija** (5 min)

#### **Test scenarij:**
- Pitati nešto što chat ne može znati
- **Primjer:** "Kad je objavljena najnovija vijest na stranici Tehničke škole u Virovitici?"
- **Očekivani odgovor:** "Nemam pristup trenutnim informacijama..."

**Transition:** "Idemo to popraviti s RAG-om!"

### **Dio 3: Upgrade na RAG** (18 min)

#### **Demo 3.1: RAG nodeovi objašnjenje** (3 min)
- Pokazati nove nodeove koje ćemo dodati
- **Workflow:** Document → Chunking → Embeddings → Vector Store → Retrieval → Enhanced Chat
- **Naglasiti:** Svaki node ima specifičnu funkciju

#### **Hands-on 3.2: Dodavanje RAG komponenti** (10 min)
**Korak po korak (ja vodim na projektoru):**
1. **PDF Input node** - upload dokumenta
2. **Text Splitter node** - chunking parametri
3. **Embeddings node** - OpenAI embeddings
4. **Qdrant Insert node** - spremanje u vector bazu
5. **Query enhancement** - dodavanje retrievala u chat

#### **Test 3.3: Upload i testiranje** (5 min)
**Učenici uploadaju:**
- Tesla dokument (pripremljen)
- **Testiraju:** Specifično pitanje o sadržaju dokumenta
- **Rezultat:** Točan odgovor s citiranim dijelovima

### **Dio 4: Finale - lokalni dokument** (2 min)

#### **Wow faktor:**
- Upload dokumenta s najnovijom viješću s njihove škole
- **Pitanje:** Nešto vrlo specifično što samo taj dokument sadrži
- **Rezultat:** Chat sada "zna" nešto što javni ChatGPT ne može znati

**Zaključak:** "Upravo ste napravili AI sustav koji koriste prave firme!"

---

## 🛠️ Tehnički detalji za pripremu

### **n8n workflow prep:**
1. **Template 1 (Basic Chat):**
   - Manual Trigger
   - OpenAI Chat Model
   - Basic Chat Memory (3 messages)

2. **Template 2 (RAG Ready):**
   - Sve iz Template 1 +
   - Placeholder nodeovi za: PDF Input, Text Splitter, Embeddings, Qdrant
   - **80% gotovo** - učenici samo dodaju veze i testiraju

### **Qdrant setup:**
- Collection kreirana unaprijed
- Test data uploadan za demonstraciju
- Cleanup skripta za reset nakon radionice

### **Backup plan:**
- **Ako n8n ne radi:** ChatGPT + copy/paste Tesla dokument
- **Ako API limit:** prebaci na Ollama lokalni model
- **Ako nema interneta:** offline demo s pripremljenim screenshotovima

---

## 🎯 Learning outcomes

**Učenici će razumijeti:**
1. **Razliku između osnovnog chata i RAG-a** - praktično
2. **Kako vizualni workflow alati rade** - n8n kao primjer
3. **Zašto firme koriste RAG** - privatni dokumenti
4. **Osnovne komponente RAG pipeline-a** - chunking, embeddings, vector storage

**Praktične vještine:**
- Dodavanje nodeova u n8n
- Upload i processing dokumenata
- Testiranje i debug workflow-a

---

## 📝 Materijali za pripremu

### **Za učenike:**
- **Step-by-step upute** s screenshotovima
- **Access credentials** za n8n workspace
- **Test pitanja** za svaki dio radionice

### **Za mene:**
- **Projector demo script** - točan redoslijed koraka
- **Troubleshooting guide** - česti problemi i rješenja
- **Timing kontrole** - checkpoint-ovi za svaki dio

---

## 🔄 Flow kontrola

### **Timing checkpoints:**
- **15 min mark:** Osnovni chat radi kod svih
- **25 min mark:** RAG nodeovi dodani
- **35 min mark:** Tesla dokument testiran
- **40 min mark:** Lokalni dokument finale

### **Ako kasni:**
- Preskočiti detaljno objašnjenje svakog node-a
- Ja radim više demo-a, oni manje hands-on
- Fokus na finale - "wow" rezultat

### **Ako ide brže:**
- Dodatni eksperimenti s chunk size-om
- Multiple dokumenti upload
- Kreativnija pitanja za testiranje

---

## 💡 Success criteria

**Radionica je uspješna ako:**
✅ Svi vide razliku basic chat vs RAG
✅ 80% timova uspješno uploada dokument
✅ Barem 1 "wow" moment s lokalnim dokumentom
✅ Razumiju zašto firme koriste ovakve sustave