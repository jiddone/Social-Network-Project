
# 📺 Twitch Community Detection

**Studente**: Gianluca Ferrari  
**Matricola**: 248004

## 📝 Descrizione

Il progetto si concentra sull'individuazione di comunità all'interno della piattaforma Twitch, analizzando un grafo non orientato di utenti basato sulla lingua portoghese. Sono stati sperimentati e confrontati diversi approcci di **community detection** su un grafo reale estratto dal dataset "Twitch Social Networks".

---

## 📊 Dataset

- Dataset: [Twitch Social Networks](https://github.com/benedekrozemberczki/datasets)
- Linguaggio scelto: **Portoghese**
- **Nodi**: 1912  
- **Archi**: 31.299  
- **Attributi dei nodi**: giorni di streaming, contenuti per adulti, visualizzazioni, partnership con Twitch, ecc.

---

## 📈 Metriche del Grafo

- Transitività: 0.1309
- Clustering medio: 0.3198
- Bridge: 116
- Lunghezza media cammini: 2.53
- Densità: 0.0171
- Nessuna componente isolata

---

## 🧪 Metodi di Community Detection

### 🔹 Distance-Based  
- **Agglomerative Hierarchical Clustering**
  - *Simple linkage*: restituisce un solo cluster
  - *Complete linkage*: restituisce 23 cluster

### 🔹 Degree-Based  
- **Clique Percolation Method**
  - k = 16  
  - 124 clique individuate, 172 archi ε

### 🔹 Modularity-Based  
- **Metodo di Louvain**
  - Implementato con libreria `community`
  - Risultato: 6 comunità

### 🔹 Label Propagation-Based  
- Algoritmo semi-sincrono (Cordasco & Gargano, 2010)
- 6 comunità ottenute

### 🔹 Attribute-Based  
- Basato sulla **similarità degli attributi** (no struttura del grafo)
- Archi filtrati con soglia di similarità > 0.9
- Clustering effettuato con **K-means**, K=3 (trovato con elbow method)

---

## 📊 Analisi dei Risultati

Per ogni metodo sono state calcolate:
- Medie degli attributi numerici
- Mode per attributi binari

📌 **Insight chiave**:
- L’approccio **attribute-based** ha individuato una comunità composta solo da **streamer partner**, data la loro rarità.
- Gli streamer con contenuti adulti hanno in media più giorni di streaming, ma **visualizzazioni nella media**.
- Il metodo **modularity-based (Louvain)** ha restituito comunità equilibrate e significative.

---

## 📁 Struttura del progetto

```text
twitch-community-detection/
│
├── data/                  # Dataset originale (edges + target)
├── preprocessing/         # Script di pulizia e costruzione del grafo
├── detection_methods/     # Implementazione dei vari metodi di CD
├── analysis/              # Statistiche e confronto
└── README.md              # Questo file
```

---

## 🚀 Requisiti

- Python 3.x
- NetworkX
- Scikit-learn
- Pandas, NumPy, Matplotlib

```bash
pip install -r requirements.txt
```

---

## 📜 Licenza

Distribuito sotto licenza **MIT**.

---

## 📬 Contatti

Per domande o suggerimenti:

**Gianluca Ferrari**  
📧 Email: gianluca.ferrari@email.com
