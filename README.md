# 🧬 Médecin IA

Pipeline NLP modulaire pour l'interprétation automatique de résultats d'analyses biologiques en français.

## Fonctionnalités

- **OCR** : prétraitement d'image (deskew, débruitage, CLAHE, binarisation) + EasyOCR (français)
- **NER biomédical** : CamemBERT-bio + couche CRF pour extraire les biomarqueurs et leurs valeurs
- **Base normative** : seuils min/max par biomarqueur construits à partir du dataset (`normes_v2.json`)
- **Matching flou** : rapprochement des noms de biomarqueurs (thefuzz)
- **RAG** : interprétation en langage naturel avec LLaMA-3.3-70B via l'API Groq
- **Interface** : application Streamlit

## Structure

```
medecin-ia/
├── medecin-ia.ipynb   # notebook principal (conçu pour Kaggle)
├── requirements.txt
├── .gitignore
└── README.md
```

## Données

Dataset : [Diagnostic Pathology Test Results](https://www.kaggle.com/datasets/pareshbadnore/diagnostic-pathology-test-results) (Kaggle).
Le dataset n'est pas inclus dans ce repo : télécharge-le depuis Kaggle et adapte les chemins `/kaggle/input/...` du notebook.

## Installation

```bash
git clone https://github.com/Ou-rkia/medecin-ia.git
cd medecin-ia
pip install -r requirements.txt
```

## Clé API Groq

La clé n'est **jamais** stockée dans le code. Définis-la dans ton environnement :

```bash
# Linux / macOS
export GROQ_API_KEY="ta_cle"

# Windows (PowerShell)
$env:GROQ_API_KEY="ta_cle"
```

Sur Kaggle, utilise *Add-ons → Secrets*.

## Utilisation

Ouvre `medecin-ia.ipynb` (Kaggle, Colab ou Jupyter local) et exécute les cellules dans l'ordre.
Les chemins `/kaggle/working` et `/kaggle/input` sont à adapter si tu l'exécutes en local.

