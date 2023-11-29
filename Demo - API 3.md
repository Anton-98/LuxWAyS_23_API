
## Démo 1 - Augmenter le solde de votre compte

### Détails

#### Outils a utiliser : **Burp Suite**

1 - Se connecter à l'application à partir de http://localhost:8888/login

2 - Cliquez sur **Shop** dans la barre de navigation pour visiter http://localhost:8888/shop

3 - Le solde initial disponible est de 100 $. Essayez de commander l'article de 10 $ dans la boutique en utilisant le bouton Acheter et observez la demande envoyée.

4 - En observant la requête POST /workshop/api/shop/orders, on constate que le crédit a été réduit de 10 $ et que le solde disponible maintenant est de 90 $.

5 - Avec ces connaissances, nous pouvons essayer d'envoyer la requête POST capturée **/workshop/api/shop/orders** à Repeater.

6 - Essayez de changer la valeur de `quantity` dans le corps de la requête en une valeur négative et envoyez la requête. On peut observer que le solde disponible a augmenté et que la commande a été passée.
7 - Pour augmenter le solde de 1000 $ ou plus, indiquez une valeur appropriée dans la "quantité" (par exemple : -100 ou moins) et envoyez la demande. On peut observer que le solde disponible a maintenant augmenté de 1000 $ ou plus.
