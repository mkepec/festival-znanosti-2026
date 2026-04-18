# Checklist za pripremu radionice

## 2 tjedna prije (do 7. travnja 2026)

### Tehnička infrastruktura
- [ ] **Proxmox server setup**
  - [ ] Povećati resurse na n8n VM (8GB RAM, 4 CPU)
  - [ ] Povećati resurse na Qdrant VM (4GB RAM, 2 CPU)
  - [ ] Testirati performanse pod opterećenjem
  - [ ] Setup backup VM-ova

- [ ] **n8n konfiguracija**
  - [ ] Multi-user setup - kreirati 5 workspace-ova (tim1-tim5)
  - [ ] Pripremiti template workflow za RAG
  - [ ] Testirati sav workflow end-to-end
  - [ ] Kreirati pristupne podatke za učenike

- [ ] **OpenAI API setup**
  - [ ] Provjeriti dostupne kredite (~50 USD potrebno)
  - [ ] Kreirati API ključeve s rate limitima
  - [ ] Testirati API latenciju iz Hrvatske
  - [ ] Setup monitoring za API troškove

- [ ] **Qdrant vector database**
  - [ ] Kreirati kolekcije za svaki tim
  - [ ] Pripremiti cleanup skriptu
  - [ ] Testirati performance s 10 concurrent korisnika

- [ ] **Grafana dashboard**
  - [ ] Kreirati dashboard za monitoring
  - [ ] Metrike: API calls, tokens spent, response time, server resources
  - [ ] Test real-time update funkcionalnosti

### Dokumenti i sadržaj
- [ ] **Tesla PDF dokumenti** (4-5 stranica svaki)
  - [ ] Tesla AC Motor Patent (1888) - jednostavljena verzija
  - [ ] Wireless Power Transmission Paper - ključni dijelovi
  - [ ] Tesla Coil Principles - tehnička objašnjenja
  - [ ] Energy Efficiency Modern Applications - veza s današnjim tehnologijama

- [ ] **Test pitanja**
  - [ ] 15-20 pripremljenih pitanja za testiranje RAG-a
  - [ ] Različite kategorije: tehnička, povijesna, primjena
  - [ ] Pitanja različite složenosti

- [ ] **Backup materijali**
  - [ ] Offline PDF kopije svih dokumenata
  - [ ] Screenshot tutoriali za svaki korak
  - [ ] Video demo workflow-a (5 min)

## 1 tjedan prije (do 14. travnja 2026)

### Testiranje s kolegama
- [ ] **Dry run s Veleučilištem**
  - [ ] Testiranje u informatičkom laboratoriju
  - [ ] Provjera brzine interneta
  - [ ] Test s 5 računala istovremeno
  - [ ] Timing cijele radionice

- [ ] **Feedback loop**
  - [ ] Testirati s nastavnicima informatike
  - [ ] Prilagoditi sadržaj temeljem feedbacka
  - [ ] Optimizirati workflow za brzinu

### Finalni sadržaj
- [ ] **Prezentacija**
  - [ ] Prebaciti markdown u PowerPoint
  - [ ] Dodati Tesla vizuale
  - [ ] Pripremiti animacije za RAG proces
  - [ ] Testirati projector setup

- [ ] **Hands-on materijali**
  - [ ] Step-by-step upute za učenike
  - [ ] Cheat sheet s n8n nodes
  - [ ] Troubleshooting guide
  - [ ] Extra zadaci za brže timove

## 3 dana prije (do 18. travnja 2026)

### Finalna provjera
- [ ] **Svi sustavi online**
  - [ ] n8n dostupan s vanjskim IP-om
  - [ ] Svi workflow template-ovi rade
  - [ ] API ključevi aktivni
  - [ ] Grafana dashboard aktivan

- [ ] **Backup planovi**
  - [ ] Lokalni Ollama model spreman
  - [ ] Jupyter notebook alternativa
  - [ ] Offline prezentacija
  - [ ] Printani materijali

### Organizacijski detalji
- [ ] **Kontakt s Veleučilištem**
  - [ ] Potvrda s organizatorom (Marko Hajba)
  - [ ] Provjera s nastavnikom (Igor Kućan)
  - [ ] Potvrda sobe i opreme
  - [ ] Test računala i pristupnih podataka

## Dan radionice (21. travnja 2026)

### Jutarnja priprema (10:00-12:30)
- [ ] **Infrastruktura check** (10:00-10:30)
  - [ ] Svi serveri online
  - [ ] n8n workspace-ovi dostupni
  - [ ] API pozivi rade
  - [ ] Grafana dashboard funkcionalan

- [ ] **Setup prezentacije** (10:30-11:00)
  - [ ] Test projektora
  - [ ] Backup na USB
  - [ ] Demo workflow pripreman

- [ ] **Laboratorij setup** (11:00-12:30)
  - [ ] Test svih računala
  - [ ] Distribucija pristupnih podataka
  - [ ] Provjera internet brzine
  - [ ] Backup materijali na stolovima

### 30 minuta prije radionice (12:30-13:00)
- [ ] **Final check**
  - [ ] Svi sustavi rade
  - [ ] Backup planovi spremni
  - [ ] Kontakt s nastavnikom
  - [ ] Priprema za učenike

## Post-radionica

### Odmah nakon (14:00-14:30)
- [ ] **Cleanup**
  - [ ] Obrisati user-generated podatke
  - [ ] Reset svih workspace-ova
  - [ ] Prikupiti feedback od učenika/nastavnika

### Tjedan poslije
- [ ] **Dokumentacija**
  - [ ] Što je funkcioniralo, što nije
  - [ ] Metrics analiza (potrošnja API-ja, response times)
  - [ ] Feedback analiza
  - [ ] Prijedlozi za buduće radionice

## Kontakti za pomoć
- **Marko Hajba (organizator):** marko.hajba@vuv.hr
- **Igor Kućan (nastavnik):** (kontakt preko Marka)
- **IT podrška Veleučilišta:** (za slučaj tehničkih problema)

## Emergency kontakti
- **Hetzner podrška:** (za server probleme)
- **OpenAI podrška:** (za API probleme)
- **Personal backup:** Marin mobile (vlastiti broj)

## Budget tracking
- **OpenAI API:** ~30-50 EUR (ovisno o aktivnosti)
- **Hetzner server:** Postojeći trošak
- **Backup materijali:** ~20 EUR (printing, USB)
- **Total budget:** ~70 EUR max