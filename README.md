# P8DS
# contexte client (fictif)
Le but final du projet est de développer un robot cueilleur de fruit intelligent. 

# Consignes Openclassroom

Il s'agit de développer dans un environnement Big Data une première chaîne de traitement des données qui comprendra le preprocessing et une étape de réduction de dimension.
Il n’est pas nécessaire d’entraîner un modèle pour le moment.
L’important est de mettre en place les premières briques de traitement qui serviront lorsqu’il faudra passer à l’échelle en termes de volume de données !

# Contraintes
Vous devrez tenir compte dans vos développements du fait que le volume de données va augmenter très rapidement après la livraison de ce projet. Vous développerez donc des scripts en Pyspark et utiliserez par exemple le cloud AWS pour profiter d’une architecture Big Data (EC2, S3, IAM), basée sur un serveur EC2 Linux. La mise en œuvre d’une architecture Big Data sous (par exemple) AWS peut nécessiter une configuration serveur plus puissante que celle proposée gratuitement (EC2 = t2.micro, 1 Go RAM, 8 Go disque serveur).

# Livrables attendus
Un notebook sur le cloud contenant les scripts en Pyspark exécutables (le preprocessing et une étape de réduction de dimension).
Les images du jeu de données initial ainsi que la sortie de la réduction de dimension (une matrice écrite sur un fichier CSV ou autre) disponible dans un espace de stockage sur le cloud.
Un support de présentation pour la soutenance, présentant :
- les différentes briques d'architecture choisies sur le cloud ;
- leur rôle dans l’architecture Big Data ;
- les étapes de la chaîne de traitement.

# Mon approche
Il s'agit d'une preuve de concept visant à nous faire acquérir les connaissances nécessaires pour pouvoir travailler en tant que data scientist avec des ingénieurs spécialisés dans la mise en place d'environnement cloud.

La première étape du projet est de mettre en place une environnement cloud. J'ai choisi Amazon EC2 payant (t2.medium, 4 Go RAM, 30 Go disque serveur, OS = Linux 18.x, 64-bit) car c'est le plus fréquent. J'ai également mis en place un bucket S3.

Puis, pour aller à l'essentiel, j'ai sélectionné arbitrairement 4 catégories de fruits dans le jeux de données et sélectionné à chaque fois deux images random, total = 8 images. Je les ai uploadé sur mon serveur S3.

Enfin, j'ai développé une application Pyspark pour extraire les features. Dans le notebook, on retrouve le code pour déployer l'application avec Spark 3.0 (Utilisation Pandas_UDF), de la lecture des images au format binary dans un spark dataframe, le preprocessing et la réduction de dimension avec PCA et enfin l'export de la dataframe vers le bucket S3.
