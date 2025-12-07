# 🧪 TP Git — **Version 2025**

## Qu'est-ce que Git ?

Git est un logiciel de gestion de versions permettant de suivre l’évolution d’un projet, de conserver un historique et de collaborer efficacement.

Il est utilisé partout : projets étudiants, stages, entreprises, open source…

---

# Installation de Git

## **Linux**

La plupart des distributions possèdent git nativement.

Sinon, installez-le avec le gestionnaire de paquets :

```bash
sudo apt-get install git        # Ubuntu / Debian
sudo dnf install git            # Fedora
sudo pacman -S git              # Arch

```

## **macOS**

Le plus simple est d'installer Git via Homebrew :

```bash
brew install git

```

Vous pouvez aussi l’obtenir via Xcode Command Line Tools (Git est inclus).

## **Windows**

Téléchargez Git for Windows :

👉 https://git-scm.com/download/win

Installez **Git Bash**, l'outil conseillé pour ce TP.

---

Configurez ensuite votre identité Git :

```bash
git config --global user.name "Votre Nom"
git config --global user.email "supermail@gmail.com"

```

---

# Clonage via Token GitHub

GitHub n’autorise plus les mots de passe pour les opérations Git.

Vous devez utiliser un **Personal Access Token (PAT)**.

## 1. Créer un token GitHub

GitHub → Settings → Developer Settings → Fine-grained tokens

Émettre un token avec les permissions :

- **Contents: Read/Write**
- Expiration courte (1–7 jours pour le TP)

Conservez-le ! Vous ne pourrez plus le voir après création.

## 2. Cloner un dépôt avec un token

```bash
git clone https://github.com/<organisation>/<repo>.git

```

Lorsque Git demande :

```
Username: votre identifiant GitHub
Password: collez votre token

```
⚠️ Important : avant de pouvoir push vos modifications, les formateurs devront ajouter manuellement votre compte GitHub en tant que collaborateur sur le dépôt. Il faudra donc demander cette étape explicitement avant de tenter le premier push (lever la main et faites nous un grand sourire on saura de quoi il s'agit ☺️).

---

# Partie 1 : Hello world

*(Les commandes ne sont pas complètes : à vous de trouver les bons arguments.)*

## 1. Cloner le dépôt

```bash
git clone <url-du-repo>
cd <nom-du-repo>

```

## 2. Créer une branche et un dossier

```bash
git switch -c prenom1-prenom2

```

Créer un dossier du même nom et un fichier affichant *Hello world*.

## 3. Partager les modifications

```bash
git add .
git status
git commit -m "feat: add hello world"
git push -u origin prenom1-prenom2

```

Vérifiez sur GitHub que tout apparaît.

## 4. Récupérer sur le second PC

```bash
git fetch
git switch prenom1-prenom2
git pull

```

## 5. Modifier : Hello INSA

L’autre membre modifie → commit → push → pull.

---

# Partie 2 : Travail en parallèle

## 1. Copier *fonctions.py* et faire un commit

Les deux membres doivent avoir la même version avant modifications.

## 2. Commits en parallèle

- A modifie `addition()`
- B modifie `soustraction()`
- chacun push

Le second verra un rejet → il faut rebase :

```bash
git pull --rebase

```

---

## Résolution de conflit

Vous modifiez tous les deux **la même ligne** dans `noms_binome()`.

Git ajoute des marqueurs :

```
<<<<<<< HEAD
...
=======
...
>>>>>>> origin/main

```

Corriger → sauvegarder → puis :

```bash
git add <fichier>
git rebase --continue

```

---

# Partie 3 : Pull requests vers main

## 1. Première PR

Depuis GitHub → **New Pull Request**, bon titre + description.

Demander validation à un admin.

## 2. PR avec conflit

Créer chacun une branche `feat/prenom`.

Modifier la **même ligne** dans `NOMS.txt`.

Les PR entrent en conflit.

En local :

```bash
git fetch
git rebase main

```

Résoudre → `git add` → `git rebase --continue`.

---

# Partie bonus

Créer un jeu de morpion réparti en plusieurs branches de fonctionnalités.
