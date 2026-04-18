# Brainstorming: Radionica za Festival znanosti 2026

## Glavna ideja: "Digitalni Tesla: Kako AI razmišlja o energiji?"

### 1. Tehnički koncept (The Stack)
- **Modeli:** Ollama (Llama 3, Mistral ili slično - lokalno zbog privatnosti i brzine).
- **Orkestracija:** n8n ili Dify (vizualni workflow za lakše razumijevanje).
- **Vektorska baza:** Qdrant (za RAG pipeline).
- **Observability:** Prometheus/Grafana (za prikaz potrošnje resursa servera).

### 2. Struktura radionice (45-60 min)
- **Uvod (10 min):** Što je GenAI, a što RAG? Zašto AI troši puno energije?
- **Hands-on RAG (30 min):**
    - Sudionici biraju dokument (npr. "Teslini patenti" ili "Vodič za solarnu energiju").
    - Prolazak kroz vizualni n8n/Dify workflow: Chunking -> Embedding -> Qdrant.
    - Testiranje: Postavljanje pitanja "Digitalnom Tesli".
- **Green AI / Observability Demo (10-15 min):**
    - Prikaz u realnom vremenu: koliko CPU/GPU snage (i indirektno energije) troši jedan odgovor chatbota.
    - Diskusija o održivosti AI tehnologija.

### 3. Ciljane skupine i prilagodba
- **S3 (Srednja škola) / ST (Studenti):** Primarna ciljana skupina za hands-on radionicu. Potrebno je osigurati jasne upute (step-by-step) kako bi mogli samostalno ili u timovima proći kroz workflow.
- **S0/S1/S2 (Osnovna škola):** Za njih bi radionica vjerojatno trebala biti više u formi "pokazne vježbe" ili pojednostavljenog sučelja, jer bi samostalna izrada RAG-a mogla biti prezahtjevna.

### 4. Tehnički resursi i infrastruktura (Hetzner Server)
- **Ollama:** Lokalno serviranje modela (Llama 3, Mistral, itd.).
- **Alati za orkestraciju:** Dify ili n8n (vizualno sučelje za workflowe).
- **Vektorska baza:** Qdrant (za pohranu i pretragu embeddinga).
- **External APIs:** Pripremljeni API ključevi za javne modele (OpenAI, Anthropic) kao fallback ili za usporedbu.
- **Observability:** Prometheus/Grafana stack za praćenje resursa.

### 5. Format radionice
1. **Teorijski dio (Predavanje):** Uvod u osnovne koncepte (LLM, RAG, vektori, energetska učinkovitost AI modela).
2. **Praktični dio (Hands-on):** Rad u timovima uz pripremljene upute ("radna bilježnica"). Svaki tim dobiva pristup sučelju (n8n/Dify) i zadatak da izradi/konfigurira svoj pipeline.

---
## Dodatne note:
- Razmisliti o "Gamifikaciji": Tko može napraviti najprecizniji RAG s najmanje resursa?
- Poveznica s Viroviticom: Možemo ubaciti dokumente o energetskim projektima u VPŽ.
