# Prihvaćena aktivnost za Festival znanosti 2026

**POTVRĐENO:** 21. travnja 2026, 13:00-14:00 h
**Grupa:** 3E razred Tehničke škole (10 učenika)
**Nastavnik:** Igor Kućan

## 1. Naziv aktivnosti
**"GenAI u praksi: Razgovor s Teslinim patentima pomoću RAG arhitekture"**

## 2. Vrsta događaja
Predavanje (20 min) + Interaktivna radionica (40 min)

## 3. Voditelj(i)
Marin Kepec

## 4. Suradnici
(Po potrebi dodati studente asistente)

## 5. Kratak opis aktivnosti
U ovoj radionici polaznici će naučiti kako od standardnog GenAI modela napraviti stručnjaka za specifičnu temu koristeći RAG (Retrieval-Augmented Generation) tehnologiju. Koristeći vizualni alat n8n, sudionici će izgraditi sustav koji povezuje dokumente o izumima Nikole Tesle s OpenAI modelima putem API poziva te vektorskom bazom podataka. Kroz praktičan rad, prokomentirat će se ključni parametri sustava poput brzine odziva i broja utrošenih tokena, dajući uvid u složenost i resurse potrebne za rad modernih AI sustava.

## 6. Ciljana publika / uzrast
- **S3** (Srednja škola: 2.–4. razred)
- **ST** (Studenti Veleučilišta)
- **S4** (Zainteresirana opća populacija s osnovnim tehničkim predznanjem)

## 7. Trajanje po grupi
60 minuta

## 8. Maksimalan broj sudionika
10-15 (specifično: 10 učenika 3E razreda Tehničke škole)

## 9. Potreban prostor
Informatički laboratorij (učionica s računalima), projektor, stabilna internetska veza.

## 10. Potrebni materijali i oprema
- Računala s pristupom internetu za polaznike.
- Udaljeni poslužitelji s instaliranim alatima: n8n, Qdrant, Ollama, Prometheus/Grafana (osigurava voditelj).
- OpenAI API ključevi za potrebe radionice (osigurava voditelj).
- Pripremljeni PDF dokumenti o Teslinim patentima i energetici.

## 11. Procijenjeni trošak materijala (EUR)
0 EUR (Koristi se vlastita infrastruktura i besplatni/open-source alati. Trošak API tokena snosi voditelj).

## 12. Kratki životopis voditelja
Marin Kepec stručni je specijalist inženjer informacijskih tehnologija s gotovo 20 godina iskustva u enterprise okruženju, trenutno zaposlen kao DevOps inženjer u tvrtki Infobip. Specijaliziran je za cloud tehnologije, automatizaciju i observability sustave, dok na Veleučilištu u Virovitici kao vanjski suradnik prenosi praktična znanja iz područja računalnih mreža i clouda. Aktivno sudjeluje u modernizaciji nastavnih programa kroz integraciju GenAI tehnologija i alata otvorenog koda u edukacijske procese.

---

### Tehničke napomene za pripremu (Interno):
- **Proxmox:** Povećati CPU/RAM resurse na n8n i Qdrant VM-ovima tjedan dana prije.
- **n8n:** Testirati *Multi-user* pristup i izolaciju radnih prostora.
- **Observability:** Podesiti eksport metrika (tokeni, latencija) iz n8n/OpenAI-a u Prometheus/Grafanu za završni demo.
- **Qdrant:** Pripremiti skriptu za automatsko brisanje kolekcija nakon radionice.
