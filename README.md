# convertisseur--fich
Application de Conversion documents 

L'application pemettra a un utilisateur de convertire un document d'un Format vers un autre format. et a fin de la realisation de cette application on va les decomposer en un ensemble de sous services (web service )qui sont :

-Service qui permet d'uploadera un document ou plutot un fichier dans web service
-Service qui permet de la conversion de document (Appél d'un web service)
-serice qui permet de retourner les notification au client

-service qui permet de recuperer information concernant l'etat de document d'utilisateur
-service de recuperation localisation de fichier apres sa conversion 

ce Fichier sera modifier en fure et a mesure en cours de la realisation de cette application pour montrer toute etape qui a ete faite acompagnons de toute capture necessaire pour bien demontrer son developpement et sa mise en oeuvre 

## Developement:

##Serveur : Spring webflux (netry reactive):apres son demarrage ce serveur va creer une map(cle,value) dont la clé=adress du client (ip ou nom du pc) et value=nombre de conversion (max=2)

**un serveur qui travaille avec REST il reponds sur 3 url de client:
URL=/checkPermission :quand le client demande url(http://ip:/checkPermission) serveur reçoit la requette et il verra ip de client et il consulte map pour voir si il est arrivé au max ou pas encore (si c'est pas encore il fera nombre conversion+1) et il envoi au client message"grant" ou message "denied"

**URL=/convert : serveur reçoit ce lien avec url de fichier apres conversion +email de client apres il envoi un email a cet adress

**url=http://ip:1999 page index.html le serveur va l'envoyer au client qui se connecte avec lui

**Pour notre Serveur on l'a fait avec Spring webflux(asynchrone+nion-blocking) et langage de programmation Kotlin

**coté design un dossier s'appel design contient 3 repertoires qui sont :

1)**CSS(stylesheet)
2)js:fichier script (material kit-ui +bootstrap+quelques tools comme waitMe+toaststr)
3)asset:les icones+les images

**Fichier de configuration de serveur(application.yml) contient port de serveur=9999 +mon email

##Client: interface web (index.html)+les evenements(click sur boutton ou lien ou ...)
on l'a fait avec html5+css3+materiel kit ui+promise (asycnhrone javascript)+jquery

**Client apres sa connexion il choisit un fichier  + format de conversion +email(facultatif) et il va cliquer sur le bouton "Convert" ares il va recevoir :
message=denied-->afficher un message jeune indique arrivéé au limit(2) et ajouter ce message au Service Log (calcule de la durée d'excution de chaque etape)


###Demonstration:

**la page index.html de notre application

![46482013_1244036135737628_1942796965645385728_n](https://user-images.githubusercontent.com/25961912/48727985-920bff80-ebe8-11e8-838e-291fce547b09.jpg)

**le choix de format de fichier et format espérée

![46450881_1848753631889796_9155313173333540864_n](https://user-images.githubusercontent.com/25961912/48728109-e7481100-ebe8-11e8-965b-767ce3713505.jpg)

**le message jeune de depassement de max de conversion 
![46513909_2370488336312464_8805951943542308864_n](https://user-images.githubusercontent.com/25961912/48728172-0e9ede00-ebe9-11e8-9ca8-4c8c0f27aa19.jpg)

**Service Log
![46512274_749363248760702_4457945082791723008_n](https://user-images.githubusercontent.com/25961912/48728238-460d8a80-ebe9-11e8-8ee9-1df92e157433.jpg)

**Lors de conversion
![46446932_347734482710232_846150111120588800_n](https://user-images.githubusercontent.com/25961912/48728287-66d5e000-ebe9-11e8-87c1-849843b5e1fa.jpg)

![46472520_484870858672814_55910866352078848_n](https://user-images.githubusercontent.com/25961912/48728343-8bca5300-ebe9-11e8-8f0e-2c9e7e09682d.jpg)







