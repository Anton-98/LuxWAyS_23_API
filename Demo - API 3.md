#### Prise à mains Burp Suite


#####  Execute APP

#### Windows 

git clone https://github.com/Anton-98/LuxWAyS_23_APP.git --config core.autocrlf=input

$ call "%cd%\deploy\docker\build-all.bat"

$ docker-compose -f deploy/docker/docker-compose.yml --compatibility up -d

#### Linux 

git clone https://github.com/Anton-98/LuxWAyS_23_APP.git 

$ deploy/docker/build-all.sh

$ docker-compose -f deploy/docker/docker-compose.yml --compatibility up -d

##### Application : `http://localhost:8888`

1 - Creation de compte

2 - Ouvrir Mailhog : `http://localhost:8025`


##### Burp Suite
1 - Ouvrir le logiciel

2 - Cliquer sur l'onglet **Proxy**, ensuite sur le sous-onglet **Intercept**

3 - Cliquer sur le bouton **Open Browser**

4 - Aller sur l'onglet **HTTP History**

5 - Aller sur le navigateur et taper l'URL http://localhost:8888



## Démo 1 - Augmenter le solde de votre compte

#### Outils a utiliser : **Burp Suite**

### Détails

1 - Se connecter à l'application à partir de http://localhost:8888/login

2 - Cliquez sur **Shop** dans la barre de navigation pour visiter http://localhost:8888/shop

3 - Le solde initial disponible est de **100 $**. Essayez de commander l'article de 10 $ dans la boutique en utilisant le bouton Acheter et observez la demande envoyée.

4 - En observant la requête POST **/workshop/api/shop/orders**, on constate que le crédit a été réduit de 10 $ et que le solde disponible maintenant est de 90 $.

5 - Avec ces connaissances, nous pouvons essayer d'envoyer la requête POST capturée **/workshop/api/shop/orders** à Repeater.

6 - Essayez de changer la valeur de `quantity` dans le corps de la requête en une valeur négative et envoyez la requête. On peut observer que le solde disponible a augmenté et que la commande a été passée.

7 - Pour augmenter le solde de 1000 $ ou plus, indiquez une valeur appropriée dans la "quantité" ( exemple : -100 ) et envoyez la demande. On peut observer que le solde disponible a maintenant augmenté de 1000 $ ou plus.





## Démo 2 - Modifier la valeur d'une proprièté interne de la vidéo personnelle

#### Outils a utiliser : **Burp Suite**

### Détails

1 - Se connecter à l'application à partir de http://localhost:8888/login

2 - Cliquez sur **Profile** dans la barre de navigation pour visiter http://localhost:8888/my-profile

3 - On televerse une vidéo de moins de 10 MB. Ensuite on modifie le nom de la vidéo.

4 - On observe la requete PUT **/identity/api/v2/user/videos/32**, on constate la valeur du parametre `video_name` est attibuée à la valeur saisie.

5 - Ainsi, nous pouvons essayer d'envoyer la requete PUT **/identity/api/v2/user/videos/32**,  à Repeater.

6 - Essayez de copier la proprièté `conversion_params` depuis la reponse et vous le collez sur la requete. Puis modifier la valeur de cette proprièté. On observe que la valeur de la proprièté interne de la vidéo peut être modifier.


## Démo 3 - Visualistion de données à caractere personnelles

### Détails

1 - Sur un navigateur ouvrir Mailhog à partir de l'adresse  http://localhost:8025/

2 - Se connecter à l'application à partir de http://localhost:8888/login

3 - 

4 - 

5 - 

6 - 

7 - 

