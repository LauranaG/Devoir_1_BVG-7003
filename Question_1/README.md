# Question 1 — Initialiser et configurer Git/GitHub

Ce guide décrit comment préparer le dépôt du devoir, enregistrer les changements avec Git, les synchroniser avec GitHub et exécuter l'analyse de la tâche 3. Les tâches 2 et 4 sont des livrables textuels; elles ne nécessitent pas de commande d'exécution.

## 1. Prérequis

- Un compte GitHub et Git installé. Vérifiez l'installation dans un terminal :
  ```bash
  git --version
  ```
- R version 4.0 ou supérieure et Rscript. Vérifiez que R est accessible :
  ```bash
  R --version
  Rscript --version
  ```
- Pour compiler le rapport, les paquets R `dplyr`, `tidyr`, `rmarkdown` et `knitr`.

Sur macOS, Git peut être installé avec Homebrew (`brew install git`) ou les outils en ligne de commande Xcode. Sur Windows ou Linux, utilisez l'installateur ou le gestionnaire de paquets recommandé par votre système.

## 2. Configurer son identité Git

Configurez le nom et l'adresse associés à vos futurs commits. Remplacez les exemples par vos propres informations; cette configuration globale ne se fait qu'une fois par ordinateur :

```bash
git config --global user.name "Votre nom"
git config --global user.email "vous@example.com"
git config --global init.defaultBranch main
```

Vérifiez les valeurs :

```bash
git config --global --list
```

L'adresse courriel devrait être celle associée à GitHub, ou l'adresse privée fournie par GitHub si vous ne souhaitez pas publier votre adresse personnelle dans les commits.

## 3. Récupérer et initialiser le dépôt du devoir

### Méthode recommandée : cloner le dépôt GitHub

Dans GitHub, utilisez **Code** pour copier l'URL HTTPS du dépôt (ou de votre fork), puis exécutez :

```bash
git clone https://github.com/VOTRE-NOM/Devoir_1_BVG-7003.git
cd Devoir_1_BVG-7003
git status
git remote -v
```

Le clonage initialise automatiquement le dépôt local, crée la branche par défaut et configure le dépôt distant nommé `origin`. Ne relancez pas `git init` dans un dépôt cloné. Pour l'URL HTTPS, authentifiez-vous avec la méthode proposée par Git/GitHub; le mot de passe du compte GitHub ne peut pas être utilisé comme mot de passe Git.

### Si vous devez partir d'un dossier local neuf

Utilisez cette méthode uniquement si vous n'avez pas déjà cloné le dépôt. Depuis le dossier du devoir :

```bash
git init -b main
git add .
git commit -m "Initialisation du devoir"
git remote add origin https://github.com/VOTRE-NOM/Devoir_1_BVG-7003.git
git push -u origin main
```

Si le dépôt GitHub contient déjà des commits (par exemple un README créé en ligne), clonez-le plutôt que de créer un historique indépendant. Cela évite d'avoir deux historiques à réconcilier.

## 4. Enregistrer et synchroniser son travail

Depuis la racine du dépôt, vérifiez les fichiers modifiés, ajoutez ceux à enregistrer, puis créez un commit :

```bash
git status
git add Question_1/README.md
git commit -m "Documenter la configuration Git"
```

Adaptez le chemin après `git add` aux fichiers réellement modifiés. Pour ajouter tous les changements non ignorés, vous pouvez utiliser `git add .` après avoir vérifié `git status`.

Récupérez les changements en ligne avant de publier vos commits, puis poussez la branche `main` :

```bash
git pull origin main
git push origin main
```

Si Git signale des conflits pendant le `pull`, ouvrez les fichiers concernés, choisissez le contenu à conserver et retirez les marqueurs `<<<<<<<`, `=======` et `>>>>>>>`. Ensuite, enregistrez la résolution avec `git add` et `git commit`, puis relancez `git push origin main`. Vérifiez à la fin avec `git status`; idéalement, la branche indique qu'elle est à jour avec `origin/main` et qu'il n'y a aucun changement non enregistré.

## 5. Installer les paquets R et exécuter l'analyse

Ouvrez R ou RStudio et installez les dépendances une seule fois :

```r
install.packages(c("dplyr", "tidyr", "rmarkdown", "knitr"))
```

Dans un terminal, placez-vous à la racine du dépôt cloné et compilez le rapport :

```bash
cd chemin/vers/Devoir_1_BVG-7003
Rscript -e "rmarkdown::render('code/Devoir1.Rmd', output_file = 'Devoir1.md')"
```

La commande exécute les étapes de l'analyse de la tâche 3 et produit ou met à jour `code/Devoir1.md` ainsi que les trois figures PNG dans `figures/`. Le script lit les données dans `data/2_Data_RNASeq_Cannabis_Sex.csv`; gardez la structure des dossiers du dépôt pour que ses chemins relatifs fonctionnent.

Dans RStudio, ouvrez `code/Devoir1.Rmd` depuis le dépôt et cliquez sur **Knit**. Si une dépendance manque, installez-la avec `install.packages("nom_du_paquet")`, puis relancez la compilation.

Après l'exécution, vérifiez les fichiers générés avec `git status`. Si le rapport ou les figures ont changé et doivent faire partie du devoir, ajoutez-les, créez un commit, puis synchronisez avec GitHub selon les commandes de la section précédente.
