
## Démo 1 - Augmenter le solde de votre compte

### Détails

#### Outils a utiliser : **Burp Suite**

1 - Se connecter à l'application à partir de http://localhost:8888/login

2 - Cliquez sur **Shop** dans la barre de navigation pour visiter http://localhost:8888/shop

3 - Le solde initial disponible est de 100 $. Essayez de commander l'article de 10 $ dans la boutique en utilisant le bouton Acheter et observez la demande envoyée.

4 - En observant la requête POST **/workshop/api/shop/orders**, on constate que le crédit a été réduit de 10 $ et que le solde disponible maintenant est de 90 $.

5 - Avec ces connaissances, nous pouvons essayer d'envoyer la requête POST capturée **/workshop/api/shop/orders** à Repeater.

6 - Essayez de changer la valeur de `quantity` dans le corps de la requête en une valeur négative et envoyez la requête. On peut observer que le solde disponible a augmenté et que la commande a été passée.

7 - Pour augmenter le solde de 1000 $ ou plus, indiquez une valeur appropriée dans la "quantité" ( exemple : -100 ) et envoyez la demande. On peut observer que le solde disponible a maintenant augmenté de 1000 $ ou plus.





## Démo 2 - Modifier la valeur d'une proprièté interne de la vidéo personnelle

### Détails

#### Outils a utiliser : **Burp Suite**

1 - Se connecter à l'application à partir de http://localhost:8888/login

2 - Cliquez sur **Profile** dans la barre de navigation pour visiter http://localhost:8888/my-profile

3 - On televerse une vidéo de moins de 10 MB. Ensuite on modifie le nom de la vidéo.

4 - On observe la requete PUT **/identity/api/v2/user/videos/32**, on constate la valeur du parametre `video_name` est attibuée à la valeur saisie.

5 - Ainsi, nous pouvons essayer d'envoyer la requete PUT **/identity/api/v2/user/videos/32**,  à Repeater.

6 - Essayez de copier la propriete `conversion_params` et sa valeur. 
