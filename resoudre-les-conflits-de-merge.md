# Résoudre les conflits de merge

Un conflit avec git est une erreur de compilation du code à un ou plusieurs endroits. Cela peut arriver lors d'un merge ou encore d'autres opérations que nous n'avons pas encore vu.

Pour tester, créer un dossier nommé **Conflit** et placez-vous dedans grâce à votre terminal / Powershell.

Initialiser le dossier en tant que projet git et créer un fichier texte 'fichier1.txt' dans lequel on imagine une fonction qui a mal été faite :&#x20;

{% code title="fichier1.txt (main)" %}
```
fonction_mal_faite
```
{% endcode %}

Faites un commit du fichier puis créer une nouvelle branche nommée "amélioration" dans laquelle vous allez vous placer.

Modifiez le fichier1.txt en imaginant que nous avons codé la fonction parfaite.

{% code title="fichier1.txt (amelioration)" %}
```
fonction_parfaite
```
{% endcode %}

Refaites un commit dans la nouvelle branche avec le changement de la fonction. Replacez-vous ensuite dans la branche **main** puis remodifiez la fonction mal faite :&#x20;

{% code title="fichier1.txt (main)" %}
```
fonction_mieux_faite
```
{% endcode %}

Faites un commit. Nos deux versions sont maintenant différentes de celle de base (les deux fonctions sont améliorées). La fonction parfaite étant dans la branche **amelioration**, nous voulons la merge dans la branche principale **main**. Il faut donc se placer sur la branche **main**.

Faites maintenant le merge de la branche **amelioration** vers **main** et il vous répondra qu'il y a un conflit dans le fichier1.txt. Il faut résoudre le conflit nous-même puis commit à nouveau le résultat. Ouvrez le fichier1.txt et regardez le résultat obtenu :&#x20;

{% code title="fichier1.txt (main)" %}
```
<<<<<<<HEAD
fonction_mieux_faite
=======
fonction_parfaite
>>>>>>>amelioration
```
{% endcode %}

Ici, c'est la fonction qui rentre en conflit. Si nous avions une autre partie de code modifié uniquement sur la branche **amelioration**, il aurait été merge avec succès. Nous souhaitons garder que la fonction parfaite. Supprimez le reste pour que notre fichier ressemble à ceci :&#x20;

{% code title="fichier1.txt (main)" %}
```
fonction_parfaite
```
{% endcode %}

Faites de nouveau un commit et votre conflit est maintenant réglé.
