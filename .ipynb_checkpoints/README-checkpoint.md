# Energy Classification Project — ML + Web App

## 1. Objectif du projet
Ce projet vise à prédire la **classe énergétique** d’un bâtiment à partir de ses caractéristiques techniques
(surface, murs, toit, hauteur, orientation, vitrage, etc.).  
Le modèle ML produit une **classe énergétique** (0 / 1 / 2) qui sert d’aide à la décision.

---

## 2. Structure du repository
- `data/` : dataset (CSV)
- `notebooks/` : notebooks de travail
  - `01_eda_adam.ipynb` : exploration & préparation des données (Adam)
  - `02_knn_aya.ipynb` : modèle KNN + tuning (Aya)
  - `03_svm_malak.ipynb` : modèle SVM + tuning (Malak)
  - `04_decision_tree_malak.ipynb` : arbre de décision + élagage (Malak)
  - `05_comparison.ipynb` : comparaison finale + choix du modèle (Aicha)
- `models/` : modèles sauvegardés (à ajouter pour l’application)
- `app/` : application web (Chadi)
- `report/` : rapports (ML + IA/Éthique)

---

## 3. Données et variable cible
- **Entrées (X)** : caractéristiques techniques du bâtiment (variables du CSV)
- **Sortie (y)** : `energy_class` = classe énergétique (0 / 1 / 2)

---

## 4. Pipeline ML (résumé)
Étapes appliquées (conformes au cours) :
1) Observation / EDA du dataset
2) Split train/test : `test_size=0.2`, `random_state=42`, `stratify=y`
3) Test de plusieurs modèles : KNN, Arbre de décision, SVM
4) Ajustement des hyperparamètres (GridSearchCV pour KNN/SVM, profondeur pour arbre)
5) Évaluation via : Accuracy, Precision, Recall, F1 (macro) + matrice de confusion
6) Choix du modèle final selon performance + généralisation

---

## 5. Modèle final retenu
✅ **SVM linéaire**
- `kernel = "linear"`
- `C = 10`
- Standardisation des features (StandardScaler) dans une Pipeline

Ce modèle a été retenu car il offre le meilleur compromis entre performance et généralisation
(écart train/test raisonnable), comparé au KNN et à l’arbre.

---

## 6. Instructions pour lancer les notebooks (local)
### Environnement
Utiliser Anaconda + Jupyter.

Commandes :
```bash
cd C:\projects\energy-classification-project
conda activate energy-ml
jupyter notebook
