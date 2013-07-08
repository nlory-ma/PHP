TD2
===

Dans ce TD, nous allons travailler avec **PHP** et un serveur web qui nous permettra
de faire la "paserelle" entre les données **HTTP** et **PHP**.

Avant de commencer, vous pouvez installer un serveur sur une machine personelle. Sous Debian/Ubuntu,
vous pouvez installer les paquets ``apache2``  et ``libapache2-mod-php5``.

Sous Windows, il est préférable d'utiliser un outil tel que **WAMP**, que vous pourrez trouver
sur le site `wampserver.com <http://www.wampserver.com/>`_.

Les fichiers relatifs à ce TD sont disponibles dans l'archive `td2.zip <../files/td2.zip>`_.


Exercice 1 : Les commodités de PHP
----------------------------------

Comme vu en dans le chapitre HTTP, les variables GET sont passées en paramètre d'une page comme ceci:

.. important::

    http://www.domain.com/path/to/resource.php?**a=1337&b=42**

Ces variables peuvent être récupérées à l'aide du tableau ``$_GET``.

.. step::
    **#-. Factorisation**

    Examniez le code fournit dans le dossier ``exercice1/``, il est constitué de plusieurs pages HTML, ce qui est problématique,
    car le code des en-têtes contenant le style et le menu est à chaque fois recopié! A l'aide de PHP, créez une unique page web
    qui contiendra toutes ces pages.

    Vous pourrez utiliser les variables GET pour que le contenu de la page soit modifié en fonction du paramètre passé
    dans l'URL.

.. step::
    **#-. Evolution**

    Rajouter des pages à ce site pourrait devenir pénible, car la page principale **PHP** que vous avez créé va grossir et grossir.
    Quelle(s) solution(s) pourrait t-on utiliser pour pouvoir utiliser plusieurs fichiers tout en évitant la duplication de code&nbsp;? Appliquez
    et testez votre idée sur cet exemple. Apellez votre encadrant pour qu'il vérifie votre code.

Exercice 2 : Les formulaires
----------------------------

Les formulaires représentent une très grande partie du développement d'un site web. 

.. step::
    **#-. Compréhension**

    Lisez et testez le script ``exercice2/form.php`` de l'archive. Comment est detecté le fait que des données ont été
    postées ? A quoi correspond ce test vis à vis du protocole HTTP ? Pourquoi la fonction `htmlspecialchars() <http://php.net/htmlspcialchars>`_
    est utilisée ici ?

.. step::
    **#-. Ajout d'un champ**

    Ajoutez un champ ``nom`` au formulaire. Lorsque le formulaire est soumis, si les deux champs sont remplis,
    la page devra indiquer: ``"Vous vous nommez [Prénom] [Nom]"``.

.. step::
    **#-. Un peu de validation**

    Ajoutez maintenant un champ ``email``. N'oubliez surtout pas comment fonctionne le protocole **HTTP**, même en
    utilisant le type de champ HTML5 ``email``, le client pourra toujours transmettre des données arbitraires via une
    requête ``POST``. C'est pour cela qu'il <u>faut impérativement</u> vérifier coté serveur que l'adresse fournie est
    bien formée, vous pourrez utiliser la fonction **PHP** `filter_var() <http://php.net/filter_var>`_.

Exercice 3 : Sécurisation
-------------------------

.. step::
    Le dossier ``exercice3/`` contient une page web dont l'accès devrait être sécurisé. A l'aide d'un formulaire et
    des sessions **PHP**, sécurisez l'accès à la page pour que les utilisateurs présents dans le fichier ``users.php``
    puissent s'idientifier avec leurs mots de passe. Pour inclure ``users.php``, vous pourrez utiliser la notation::

        <?php

        // Notation spéciale dans le cas ou le fichier 
        // inclus contient un "return"
        $users = include('users.php');

.. step::
    Implémenter ensuite une fonction de déconnexion.