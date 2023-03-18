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

Nous allons créer une nouvelle fonctionnalité. Pour cela, on va se mettre sur une nouvelle branche. Vérifions d'abord où nous sommes placés en faisant :&#x20;

```sh
git branch
```

La commande est censé nous répondre :&#x20;

```sh
* main
```

Main étant le nom de la branche et l'étoile signifie qu'on est placé dessus. Ajoutons notre nouvelle branche "fonctionnalite" et vérifions si elle est bien créée.

```sh
git branch fonctionnalite
git branch
```

Et vous obtrenez le résultat suivant :&#x20;

```sh
  fonctionnalite
* main
```

La branche a bien été créée mais nous sommes toujours sur "main". Déplaçons nous sur le branche "fonctionnalite" et vérifions.

```sh
git checkout fonctionnalite
git branch
```

L'étoile est placée devant "fonctionnalite". Nous pouvons voir dans notre dossier que rien à changé. Mais lorsque vous ferrez des ajout dans le dossier, ils seront fait uniquement dans la branche "fonctionnalite". Si vous revenez dans "main", il n'y aura que le `fichier1.txt`.

Ajoutons un fichier nommé `fonction.txt` et ajoutons du texte :&#x20;

{% code title="fonction.txt" %}
```
Ma fonction
```
{% endcode %}

Ajoutez-la dans l'espace de stage puis faites un commit. Éditez le fichier1.txt pour appeller  notre soi-disante fonction :&#x20;

{% code title="fichier1.txt" %}
```
Contenu
fonction()
```
{% endcode %}

Ajoutez-le de nouveau dans l'espace de stage puis faites un nouveau commit.



Imaginons que nous avons un problème à régler dans la branche "main". Placez-vous dedans en refaisant :&#x20;

```sh
git checkout main
```

Vous pouvez voir dans votre dossier qu'il ne reste plus que le `fichier1.txt` avec comme contenu "Contenu". L'appel a la fonction a également disparu. Rassurez-vous, votre code n'est pas perdu, il est toujours là mais sur la branche "fonctionnalite".&#x20;

Créez un fichier `serveur.txt` vide. Ajoutez le à l'espace de stage et faites un commit.

Disons que notre nouvelle fonctionnalité est terminée et que nous voulons l'ajouter à la branche "main". Pour cela, nous allons faire un **merge**. Il s'agit d'une fusion des deux branches. Nous allons ainsi garder les changements de la branche "main" (serveur.txt) mais également ajouter ceux de la branche "fonctionnalite" (fonction.txt et appel de celle-ci). Vérifiez avant tout que vous êtes bien dans la branche "main" et faites :&#x20;

```
git merge fonctionnalite -m "Commentaire de merge"
```

Regardez de nouveau votre dossier. Les trois fichiers des deux branches se retrouvent dans "main". SI vous regardez de plus près, nous avons notre fonction et elle est appelée dans notre `fichier1.txt`.

Bravo, vous venez de réussir votre premier merge sur Git.
