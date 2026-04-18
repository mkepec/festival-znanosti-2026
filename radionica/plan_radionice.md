# Plan radionice - Hands-on RAG (40 minuta)

## Ciljevi radionice
1. **Praktično iskustvo** s n8n visual workflow
2. **Razumijevanje RAG arhitekture** kroz izgradnju
3. **Osvještavanje energetske potrošnje** AI sustava
4. **Povezivanje s elektrotehničkim znanjem** (Tesla, energija)

## Struktura radionice (40 min)

### Faza 1: Setup i upoznavanje s alatima (8 min)
**Minutaža: 0-8**
- **Pristup n8n sučelju** (2 min)
  - Svaki učenik dobiva URL i pristupne podatke
  - Kratka demonstracija osnovnog sučelja
- **Demo postojećeg workflow-a** (3 min)
  - Pokazati gotov RAG workflow (bez objašnjavanja detalja)
  - Postaviti jedno pitanje i pokazati odgovor
- **Objašnjenje zadatka** (3 min)
  - "Sada ćete sami izgraditi ovakav sustav"
  - Podjela u timove od 2-3 učenika po računalu

### Faza 2: Korak-po-korak izgradnja RAG workflow-a (25 min)
**Minutaža: 8-33**

#### Korak 1: Dodavanje PDF dokumenata (5 min)
- **n8n node: "HTTP Request"** za dohvaćanje PDF-a
- **Teslini patenti:** 3-4 kratka PDF dokumenta (pripremljena)
- **Testiranje:** Provjeriti da li se dokument učitava

#### Korak 2: Tekst processing (8 min)
- **n8n node: "PDF Extract"** - izvlačenje teksta iz PDF-a
- **n8n node: "Text Splitter"** - dijeljenje na manje dijelove (chunks)
- **Parametri za eksperimentiranje:**
  - Chunk size: 500-1000 znakova
  - Overlap: 50-100 znakova
- **Praktični zadatak:** Učenici mijenjaju parametre i vide razlike

#### Korak 3: Kreiranje vektora i storage (7 min)
- **n8n node: "OpenAI Embeddings"**
- **n8n node: "Qdrant Vector Store"**
- **Objašnjenje:** "Pretvaramo tekst u brojeve koje računalo razumije"
- **Analogija:** Poput pretvaranja analognog signala u digitalni

#### Korak 4: Postavljanje pitanja i dobivanje odgovora (5 min)
- **n8n node: "Manual Trigger"** za unos pitanja
- **n8n node: "Qdrant Search"** za pronalaženje relevantnih dokumenata
- **n8n node: "OpenAI Chat Model"** za generiranje odgovora
- **Prvi test:** Postavljanje pitanja o Teslinim izumima

### Faza 3: Eksperimentiranje i optimizacija (5 min)
**Minutaža: 33-38**
- **Timski zadaci:**
  - Tim 1: Optimizirajte chunk size za najbolje rezultate
  - Tim 2: Testirajte različite načine postavljanja pitanja
  - Tim 3: Eksperimentirajte s različitim Teslinim dokumentima
- **Cilj:** Vidjeti kako parametri utječu na kvalitetu odgovora

### Faza 4: Monitoring i energetska svjesnost (2 min)
**Minutaža: 38-40**
- **Grafana dashboard:** Prikaz realnih metrika
  - Broj utrošenih tokena po pitanju
  - Vrijeme odgovora
  - CPU/memorijska potrošnja servera
- **Diskusija:** "Koliko košta jedan odgovor? Kako to utječe na okoliš?"

## Priprema prije radionice

### Tehnička infrastruktura
- [ ] **n8n server** s pripremljenim template workflow-om
- [ ] **Qdrant** vector database
- [ ] **OpenAI API** ključevi s dovoljnim kreditom
- [ ] **Grafana dashboard** za monitoring
- [ ] **Backup plan:** Lokalni Ollama ako OpenAI ne radi

### Dokumenti za RAG
- [ ] **Tesla patent AC motor** (PDF, 2-3 stranice)
- [ ] **Tesla wireless transmission** (PDF, 2-3 stranice)
- [ ] **Tesla coil basics** (PDF, 2-3 stranice)
- [ ] **Energy efficiency principles** (PDF, 2-3 stranice)

### Sučelje za učenike
- [ ] **Multi-user n8n setup** - svaki tim svoj workspace
- [ ] **Jednostavne upute** - step-by-step s screenshotovima
- [ ] **Primjeri pitanja** za testiranje
- [ ] **Quick start template** ako netko zastane

## Backup scenariji
1. **n8n ne radi:** Pripremiti Jupyter notebook s istim funkcionalnostima
2. **API limit:** Prebaciti na lokalni Ollama model
3. **Internet sporih:** Pripremiti offline verziju s lokalnim modelima
4. **Različite brzine rada:** Extra zadaci za brže timove

## Evaluacija uspjeha
- **Svi timovi uspješno postave osnovni RAG**
- **Barem 2 tima eksperimentiraju s parametrima**
- **Učenici postavljaju smislena pitanja o energiji/Tesli**
- **Razumijevanje trade-off-a između brzine i kvalitete odgovora**