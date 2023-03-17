# Commits, branches et merges

Nous allons voir dans cette leçon comment créer notre premier projet avec git, sauvegarder notre code et créer des nouvelle branches.

Créons tout d'abord un dossier pour notre projet de test. Ici : MonProjet

Rendez-vous dans le dossier dans votre Terminal / Invite de commande et initialiser le dossier en tant que projet git.

```sh
cd <emplacement du dossier>
git init
```

Un dossier `.git` va s'ajouter dans "MonProjet" (celui-ci n'est pas forcément visible).

Ajoutons un premier fichier nommé `fichier1.txt` dans notre dossier. À sa création, le fichier est placé dans le répertoire de travail mais n'est pas enregistré par git.

Éditons notre fichier en ajoutant du contenu simple :&#x20;

{% code title="fichier1.txt" %}
```
Contenu
```
{% endcode %}

Retournez dans votre Terminal / Invite de commande et observons à quoi ressemble le projet git pour le moment.

```sh
git status
```

La commande renvoie normalement :&#x20;

```
On branch main

No commits yet

Untracked files:
    (use "git add <file>...") to include in what will be committed
            fichier1.txt
            
nothing added to commit but untracked files present (use "git add" to track)
```

La commande nous indique que nous sommes placés dans la branche main et que nous avons aucun commit (nous reviendrons sur cette notion un peu plus tard). La commande détecte qu'il y a un fichier qui n'est pas traqué par Git et que pour l'ajouter, il faut faire "git add". Nous allons donc bouger virtuellement notre fichier de notre répertoire de travail à l'espace de stage (projet git).

```sh
git add fichier1.txt
git status
```

Maintenant, le fichier est ajouté à l'espace de stage et nous allons l'ajouter en faisant un commit.

```sh
git commit -m "Commentaire de commit"
```

Le commentaire est très important pour savoir les changements qui ont été effectués.

La commande vous retourne le nom du commit, son hash et vous indique qu'un fichier a été inséré. Votre premier commit a été réalisé avec succès. Voici le schéma de toutes les étapes :&#x20;

<figure><img src=".gitbook/assets/stage et commit.png" alt=""><figcaption><p>Schéma des étapes</p></figcaption></figure>

Voici à quoi ressemble pour le moment notre projet :&#x20;

