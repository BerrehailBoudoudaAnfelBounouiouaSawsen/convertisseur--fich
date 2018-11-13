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

##Coté Serveur: 

Back-end :Spring webflux

##Coté Client

Front-end(client):materiel design boostrap+promise(async javascript)

*La conversion doit etre online et a la fin y'aura un envoi d'email qui contient l'URL de ficher apres sa conversion

*Limite de conversion (max=2)

On a utilisé un web service qui existe déja qui travaille avec le REST 

#Les exemples de code source HTML permettant d’utiliser l’API Web REST. Vous pouvez enregistrer les codes source dans un fichier html et le tester:
<html>
<head>
    <title>Test REST Web API</title>
</head>
<body>
    
    <form action="#" method="post" enctype="multipart/form-data" name="conversionform" id="conversionform">
         
         <p>API Key: <input id="key" name="key" type="text" /></p>
        
        <p>Local file: <input id="file" name="file" type="file" /></p>
        
        <p>Target format:
             
             <select name="targetformat" id="targetformat"">
                
                <option value="pdf" selected >PDF</option>
                
                <option value="docx">DOCX</option>
               
               <option value="doc">DOC</option>
                
                <option value="rtf">RTF</option>
                
                <option value="pptx">PPTX</option>
               
               <option value="epub">EPUB</option>
               
               <option value="html">HTML</option>
               
               <option value="txt">TXT</option>
               
               <option value="jpg">JPG</option>
               
               <option value="tif">TIFF</option>
               
               
               <option value="png">PNG</option>
           
           </select>
        
        </p>
        
        <p><input type="button" value="Convert" onclick="convertpdfform()" /></p>
        
        <p><span id="resulttext">Conversion Results: </span></p>
    
    
   </form>

<script src="/js/jquery.js"></script>

<script src="/js/jquery.form.js"></script>

<script type="text/javascript">
 
 $(document).ready(function() {
  });
 
 function showResponse(responseText, statusText, xhr, $form)  {
  
  resulttext.innerHTML=responseText;
  }
  function showError(responseText, statusText, xhr, $form)  {
  }
  function convertpdfform() {
   
   options = {
    
    success:       showResponse, 
    
    error:         showError,
      
      url:       "//s2.aconvert.com/convert/api-win.php",
    };
   
   $('#conversionform').ajaxForm(options);
   
   $('#conversionform').ajaxSubmit(options);
   
   return false;
  }
</script>
</body>
</html>
 ce qui nous reste c'est bien comment avoir le resultat de la convertion
