# Devoir 1 — oLLMpiques 2026 (BVG-7003)

Ce dépôt rassemble les livrables, les données et le pipeline d'analyse bioinformatique du Devoir 1 du cours BVG-7003. L'analyse principale (Tâche 3) évalue l'expression des gènes candidats *REM16* (`LOC115699937`) et *FT1* (`LOC115696989`) pour la discrimination sexuelle précoce chez *Cannabis sativa* à partir de données transcriptomiques (RNA-Seq) de 138 individus.

## Sommaire
1. [Organisation du dépôt](#1-organisation-du-dépôt)
2. [Prérequis et dépendances](#2-prérequis-et-dépendances)
3. [Reproduire l'analyse (Tâche 3)](#3-reproduire-lanalyse-tâche-3)
4. [Aperçu des résultats et figures](#4-aperçu-des-résultats-et-figures)

---

## 1. Organisation du dépôt

| Question | Description du livrable | Emplacement |
| :---: | :--- | :--- |
| **Tâche 1** | Initialisation et validation du dépôt Git/GitHub | [`Question_1/README.md`](Question_1/README.md) |
| **Tâche 2** | Résumé condensé (250 mots) de Steen *et al.* (2013) sur les rétractations scientifiques | [`Question_2/Abstract.txt`](Question_2/Abstract.txt) |
| **Tâche 3** | Script R Markdown d'analyse de l'expression de *REM16* et *FT1* selon le sexe | [`Question_3/Devoir1.Rmd`](Question_3/Devoir1.Rmd) |
| **Tâche 4** | Proposition méthodologique à haut débit pour le sexage transcriptomique | [`Question_4/Proposition.txt`](Question_4/Proposition.txt) |

```text
Devoir_1_BVG-7003/
├── Question_1/
│   └── README.md                         # Validation de la Tâche 1
├── Question_2/
│   └── Abstract.txt                      # Résumé réduit à exactement 250 mots
├── Question_3/
│   └── Devoir1.Rmd                       # Script d'analyse reproductible (Tâche 3)
├── Question_4/
│   └── Proposition.txt                   # Protocole RT-qPCR à haut débit (max 250 mots)
├── data/
│   └── 2_Data_RNASeq_Cannabis_Sex.csv    # Matrice d'expression normalisée (138 plantes)
├── figures/                              # Figures exportées automatiquement par Devoir1.Rmd
│   ├── Figure1_REM16_boxplot.png
│   ├── Figure2_FT1_boxplot.png
│   └── Figure3_Combined_boxplot.png
└── README.md                             # Documentation principale du dépôt

## Reproduire l'analyse

Ouvrir [`Question_3/Devoir1.Rmd`](Question_3/Devoir1.Rmd) dans RStudio et exécuter les cellules pour générer les tableaux et figures de l'analyse. Vérifier que les chemins vers les fichiers de données correspondent à l'emplacement du projet sur votre ordinateur.
