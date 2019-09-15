### SEMAINE 1 : exercice sur les models 


# THEME: MAGAZINE

### Models

* Categorie

* Article

* Commentaire

* User


### Creations des champs:

```python
from django.db import models
from django.contrib.auth.models import User

class Categorie(models.Model):
    titre =  models.CharField(max_length=255)
    description =  models.TextField()
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    image = models.ImageField(upload_to='categorie', blank=True)
    
    
    
class Article(models.Model):
    categorie_id =  models.ForeignKey(Categorie,on_delete=models.CASCADE, related_name="categorie_post")
    description =  models.TextField()
    date_add =  models.DateTimeField(auto_now_add=True)
    date_update =  models.DateTimeField(auto_now=True)
    status =  models.BooleanField(default=True)
    photo = models.ImageField(upload_to ='article', blank=True)
    
    
class Commentaire(models.Model):
    article_id =  models.ForeignKey(post,on_delete=models.CASCADE, related_name="post_a_commenter")
    user_id =  models.ForeignKey(User,on_delete=models.CASCADE, related_name="user_qui_a_commenter")
    contenu =  models.TextField()
    date_comment =  models.DateTimeField(auto_now_add=True)
    status =  models.BooleanField(default=True)
    
    
class User:
    ""nous allons utilser celui de django pour plus de securité"" 
 ```  
### Explication :
* User:
> j'ai importer le models User de django 
>je l'utilise au cas ou un internaute voudrais commenter il va devoir s'inscrire""

* Categorie:
>le model categorie est utilisé pour les categorie d'article puisque 
>nous sommes sur un magazine il y aura plusieur categorie d'info par exemple : Sport,Mode etc.


* Article:

>pour chaque categorie il y'a des sujet bien precis que l'admin voudra publier en fonction 
>de  la categorie , j'ai appelé ce models la article pour faire reference a se sujet .

* Commentaire:
>pour les commentaire sur les article il prends les User en foreigkey et ausi l'article 
>pour specifié qui a commenter et qu'elle article (info) il a commenter 

