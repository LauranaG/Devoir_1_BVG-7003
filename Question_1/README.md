# Question 1 — Cloner le dépôt pour exécuter le devoir

Dans un terminal, clonez le dépôt et placez-vous dans son dossier :

```bash
git clone https://github.com/LauranaG/Devoir_1_BVG-7003.git
cd Devoir_1_BVG-7003
```

Pour générer le rapport et les figures localement, exécutez le script depuis la racine du dépôt :

```bash
Rscript -e "knitr::knit('code/Devoir1.Rmd', output = 'code/Devoir1.md')"
```

Le script utilise les données du dossier `data/` et enregistre les figures dans `figures/`.
