#  Détection de fraude par carte de crédit

##  Contexte

Les transactions frauduleuses représentent un risque majeur pour les institutions financières.

Elles entraînent :
- Des pertes financières importantes
- Une dégradation de la confiance des clients
- Des coûts opérationnels élevés

 Il est donc essentiel de mettre en place une détection automatique et rapide.

---

## Problème

Type de tâche : **Classification binaire supervisée**

Variable cible :

- Class = 0 → Transaction légitime  
- Class = 1 → Transaction frauduleuse  

Défi principal :

 Dataset extrêmement déséquilibré (~0,17 % de fraudes)

---

## Données

Source : Kaggle – Credit Card Fraud Detection (ULB)

- 284 807 transactions
- Variables : Time, Amount, V1 à V28, Class
- Aucune valeur manquante
- Doublons conservés (transactions réelles)

---

##  Transformations

###  Transformation logarithmique de la variable Amount

Objectifs :
- Réduire l’asymétrie
- Stabiliser l’apprentissage des modèles

---

###  Transformation temporelle de la variable Time

- Conversion en heures
- Analyse des comportements transactionnels

---

##  Nouvelles variables

- **Amount_per_hour** → Montant rapporté à l’activité horaire  
- **Is_night** → Indicateur de transaction nocturne  

 Permettent de mieux capturer les comportements atypiques.

---

##  Gestion du déséquilibre

Stratégies testées :

- Baseline (pondération des classes)
- SMOTE
- Random Under-Sampling
- **SMOTE + Tomek Links**

 Meilleur compromis observé : **SMOTE + Tomek**

---

##  Modèles testés

1 Modèle Deep Learning / Pré-entraîné  
2️ Logistic Regression pondérée  
3️ **XGBoost**

---

## Résultats (à compléter)

*(Ajoute ici tes métriques finales depuis le notebook)*

Exemple :

- Logistic Regression → ROC-AUC = 0.9707 | PR-AUC = 0.7168 
- XGBoost → ROC-AUC = 0.9816| PR-AUC = 0.8673 

---

##  Conclusion

Ce projet a permis de construire un pipeline complet :

EDA → Transformations → Feature Engineering → Rééquilibrage → Modélisation → Comparaison

 Meilleure approche :

**XGBoost + SMOTE + Tomek Links**

✔ Bonne détection des fraudes  
✔ Faux positifs limités  

---

##  Contenu du dépôt

- Notebook : `detection-fraude-carte-credit.ipynb`
- Présentation : `detection-fraude-carte-credit.pptx`

---

##  Auteurs

-Ahcene Hanafi 
