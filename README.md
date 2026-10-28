# DecisionLab Morgiane — Allocation de Capital Immobilier (Zillow Group)

Ce projet propose une stratégie quantitative d'allocation de capital basée sur l'analyse prédictive des prix de l'immobilier aux États-Unis (données Zillow). 

L'objectif est d'optimiser l'engagement d'un portefeuille de 10 000 000 \$ en arbitrant entre opportunités à fort potentiel et conservation de liquidités.

---

Ce TD sert d'épreuve de substitution pour la second note du cours de Python pour la Data Science

---

## Synthèse & Pitch (Conseil d’Administration) aussi noté en markdown en fin de notebook

### Méthode & Validation
* **Modèle retenu :** Régression linéaire (`MODEL = "linear"`), surpassant la baseline zéro et la stratégie momentum.
* **Erreur de validation (2019) :** **MAE de 1,28 point de pourcentage** (RMSE de 1,57 point).
* **Atout :** Réduit l'erreur de plus de 25 % par rapport au momentum et évite les erreurs de prédiction extrêmes.

### Allocation & Gestion du Cash
* **Capital engagé :** **2 000 000 \$** alloués sur la zone la plus performante (**Phoenix, AZ — ID `394976`**).
* **Cash conservé :** **8 000 000 \$ (80 % du budget)**.
* **Raison économique :** Avec une marge de sécurité fixée à **0,2 point**, le modèle ne sélectionne que les marchés rentables net de tous frais (achat, vente, portage). Le cash protège le portefeuille des zones secondaires à faible rendement net.

### Limites des métriques passées (MAE)
La MAE mesure une précision statistique passive mais n'intègre pas :
1. Les **coûts d'arbitrage et de portage** réels.
2. Le **risque de liquidité** (impossibilité de revendre au prix ZHVI théorique en cas de tension).
3. L'**asymétrie des pertes** (une surestimation engendre une perte de capital réelle).

### Facteurs d'invalidation
* **Choc macroéconomique :** Une hausse des taux d'intérêt impactant le pouvoir d'achat et la valeur ZHVI.
* **Hausse des frais :** Un surcoût de portage absorbant la marge de +0,2 point.
* **Retournement local :** Enrayement de la dynamique sur la zone ciblée (Phoenix).

---

## Structure du Dépôt

```text
.
├── 01_etudiant.ipynb            # Notebook Jupyter complet (exploration, modélisation & décision)
├── README.md                    # Présentation du projet et pitch
└── submissions/
    └── submission_morgiane.json # Fichier d'export de la stratégie
