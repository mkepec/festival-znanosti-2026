# Plan prezentacije - GenAI u praksi (20 minuta)

## Ciljana publika
- **3E razred elektrotehničke škole (10 učenika)**
- **Uzrast:** 17-18 godina
- **Predznanje:** Osnovni pojmovi elektrotehnike, programiranje (vjerojatno C/Python)
- **Kontekst:** Tema ENERGIJA + Nikola Tesla

## Struktura prezentacije (20 min)

### 1. Uvod i motivacija (3 min)
- **Hook:** "Tesla je sanjao o bežičnom prijenosu energije - danas AI može 'bežično' pristupiti znanju"
- Kratka veza Tesla-AI-energia
- Što ćemo danas napraviti

### 2. Što je GenAI? (5 min)
- **Analogija s elektrotehničkim pojmovima:**
  - LLM kao "inteligentni transformator" koji pretvara pitanja u odgovore
  - Token kao "naponski impuls"
  - Model kao "crna kutija" s inputima i outputima
- ChatGPT demo - postavljanje pitanja o Tesli
- Problem: "Kako ChatGPT zna o Teslinim patentima ako su nastali 2023?"

### 3. Problem s "pamćenjem" AI modela (3 min)
- **Datum izreza znanja (knowledge cutoff)**
- **"Halucinacije"** - kada AI izmišlja odgovore
- **Potreba za vanjskim znanjem**

### 4. Rješenje: RAG arhitektura (7 min)
- **R**etrieval = dohvaćanje relevantnih dokumenata
- **A**ugmented = obogaćivanje pitanja s kontekstom
- **G**eneration = generiranje odgovora na temelju konteksta

**Vizualna analogija s elektrotehničkim sklopom:**
- Dokumenti = "kondenzatori" (pohranjuju informacije)
- Vektorska baza = "komutator" (odabire relevantne informacije)
- LLM = "pojačalo" (obrađuje i daje izlaz)

### 5. Što ćemo graditi danas (2 min)
- **n8n workflow** - vizualni alat za povezivanje komponenti
- **Teslini patenti** kao baza znanja
- **OpenAI API** za generiranje odgovora
- **Monitoring** potrošnje resursa u realnom vremenu

## Ključne poruke za učenike
1. **AI nije magija** - to su složeni matematički modeli
2. **Podaci su ključni** - AI je dobar koliko su dobri podaci koje koristi
3. **Energetska cijena** - svaki AI odgovor troši energiju
4. **Praktična primjena** - RAG omogućuje AI specijalizaciju

## Priprema za radionicu
- **Transition:** "Sada kada znamo teoriju, idemo to napraviti sami!"
- Kratko objašnjenje kako će funkcionirati hands-on dio