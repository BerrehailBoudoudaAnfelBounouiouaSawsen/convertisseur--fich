# convertisseur--fich
Application de Conversion documents 

L'application pemettra a un utilisateur de convertire un document d'un Format vers un autre format. et a fin de la realisation de cette application on va les decomposer en un ensemble de sous services (web service )qui sont :

-Service qui permet d'uploadera un document ou plutot un fichier dans web service
-Service qui permet de la conversion de document (Appél d'un web service)
-serice qui permet de retourner les notification acompagné de URL au client

ce Fichier sera modifier en fure et a mesure en cours de la realisation de cette application pour montrer toute etape qui a ete faite acompagnons de toute capture necessaire pour bien demontrer son developpement et sa mise en oeuvre 

## Developement:

##Serveur : Spring webflux (netry reactive):apres son demarrage ce serveur va creer une map(cle,value) dont la clé=adress du client (ip ou nom du pc) et value=nombre de conversion (max=2)

 **Pour notre Serveur on l'a fait avec Spring webflux(asynchrone+nion-blocking) et langage de programmation Kotlin

**L'application dispose de 3 repetoire qui sont :Bean ,Service ,util

![repertoire](https://user-images.githubusercontent.com/25961912/48957708-29d25c00-ef0f-11e8-809b-12fd670b5e07.PNG)

**Le repertoire Bean:
de sa part contient deux classes:

**classe Convertion predicat:condition de la conversion :c'est une map sa clé est le port sa valeur est nombre de conversion

**classe EmailReponseModel: la réponse que le client reçoit dans son mail ça contient url de fichier

**Le Repertoire Service:
classe RouterHandler : classe composant of springboot :comment gerer les URL
/check permission :deja predefini en detail en bas 


**un serveur qui travaille avec REST il reponds sur 3 url de client:
URL=/checkPermission :quand le client demande url(http://ip:/checkPermission) serveur reçoit la requette et il verra ip de client et il consulte map pour voir si il est arrivé au max ou pas encore (si c'est pas encore il fera nombre conversion+1) et il envoi au client message"grant" ou message "denied"

**URL=/convert : serveur reçoit ce lien avec url de fichier apres conversion +email de client apres il envoi un email a cet adress

**url=http://ip:1999 page index.html le serveur va l'envoyer au client qui se connecte avec lui

**Repertoire Util: different lien proposers par l'application 


**coté design un dossier s'appel design contient 3 repertoires qui sont :

1)**CSS(stylesheet)
2)js:fichier script (material kit-ui +bootstrap+quelques tools comme waitMe+toaststr)
3)asset:les icones+les images

**Fichier de configuration de serveur(application.yml) contient port de serveur=9999 +mon email

##Client: interface web (index.html)+les evenements(click sur boutton ou lien ou ...)
on l'a fait avec html5+css3+materiel kit ui+promise (asycnhrone javascript)+jquery

**Client apres sa connexion il choisit un fichier  + format de conversion +email(facultatif) et il va cliquer sur le bouton "Convert" ares il va recevoir :
message=denied-->afficher un message jeune indique arrivéé au limit(2) et ajouter ce message au Service Log (calcule de la durée d'excution de chaque etape)

**Base de données: on a pas utiliser une base de données parceque une fois il tappe son email apres la conversion l'url de fichier converti sera directement envoyé dans sa boite mail

**Notre convertisseur fichier a 5 formats :jpg ,txt;docx,html,pdf,xls,mp3,bmp,mp4


###Demonstration:

**pour execution de application on aura besoin d'internet et Serveur  Rest gratuit qui se trouve ici http://s2.aconvert.com/convert/api-win.php 
https://www.aconvert.com/

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

**La reception de fichier apres conversion de Format :

**Docx
![docx](https://user-images.githubusercontent.com/25961912/48728823-e6b07a00-ebea-11e8-8864-1acbd931e312.png)

**Mp3
![mp3](https://user-images.githubusercontent.com/25961912/48728905-2a0ae880-ebeb-11e8-8d89-2b3d1b0d09b5.png)

## Déploiement Sur Cloud 

![capture](https://user-images.githubusercontent.com/25961912/48957092-73b94300-ef0b-11e8-822b-ac30124b904f.PNG)

**apres generer jar pour lancer le service soit double clique sur le jar generé ou bien utiliser cmd en tappant cette commande :
C:\Users\Anfel\Desktop>java -jar cloud-convertion-1.0.1.jar
comme ça on a deux solution soit executer notre application de local avec le port 9999 ou bien en acces sur le lien générer apartir de cloud pivotal


**Pour ça on a utilisé le cloud de "Pivotal Web-service": on utilisé espace privé d'un amis pour pouvoir faire l'upload
![cloud](https://user-images.githubusercontent.com/25961912/48956846-1cff3980-ef0a-11e8-9eb2-a659b6d406e5.png)


**a fin de le reussir on a installer la commande CLI pour utiliser le cmd "la commande cf login" ala connexion de site 

![acces to pivotal-cloud](https://user-images.githubusercontent.com/25961912/48956935-88490b80-ef0a-11e8-8136-8e642f919fda.png)

**tapper l'email et le mot de passe tout commme suit:

![cf push -bouilding](https://user-images.githubusercontent.com/25961912/48956995-dd851d00-ef0a-11e8-889d-7d1607bc8835.png)

**Avant de commencer Upload de application sur le cloud on doit disposer d'un fichier yaml qui a les information suivant:

![yml](https://user-images.githubusercontent.com/25961912/48957241-46b96000-ef0c-11e8-82b8-2198c49b5348.png)

**Maintenant avec cmd toujours on accede en chemain la ou il y'a le fichier .yml et on tappe cette commande "cf push" et le resultat sera :
![deployement](https://user-images.githubusercontent.com/25961912/48957304-9861ea80-ef0c-11e8-81dc-05fbbc9f6ca1.png)

![deployement2](https://user-images.githubusercontent.com/25961912/48957317-b2033200-ef0c-11e8-8fb6-2858145d86da.png)
![deployement3](https://user-images.githubusercontent.com/25961912/48957343-e545c100-ef0c-11e8-894b-347ff5e0ad1a.png)

**Et puis on accede notre espace sur Cloud pivotal on l'a trouve la bas 
![pivotal](https://user-images.githubusercontent.com/25961912/48957386-35bd1e80-ef0d-11e8-81e5-af8bd1e8d634.png)

** le lien 
https://anfel-suzi.cfapps.io
 **permet l'acces directe au fichier executable 













