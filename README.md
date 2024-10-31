termine proprement.
README Projet Poste 3

Objectif du projet

L'objectif de ce projet est de créer un outil d'extraction d'information météorologique, plus précisément un script Shell qui extrait périodiquement la température actuelle d'une ville donnée ainsi que les prévisions météorologiques pour le lendemain, en utilisant le service wttr.in. Ce script enregistre les informations extraites dans un fichier texte, chaque enregistrement apparaissant sur une seule ligne. Le projet comporte plusieurs variantes qui introduisent des fonctionnalités supplémentaires.

Pour améliorer la synchronisation technique du projet, nous utilisons Git pour conserver chaque version, y compris les versions intermédiaires, et pour documenter chaque intervention d'un membre du groupe.

Versions et variantes du script

Version 1 : Extraction des données météorologiques de base

La version 1 du script extrait les données météorologiques de base, à savoir la température actuelle et la prévision pour le lendemain, pour une ville donnée. Les données sont enregistrées dans un fichier texte nommé meteo.txt avec le format suivant :

[Date] - [Heure] - Ville : Température actuelle - Prévision du lendemain

Exemple :

2024-09-24 - 14:30 - Toulouse : Température actuelle : 17°C - Prévision du lendemain : 19°C

Version 2 : Automatisation périodique

La version 2 permet l'automatisation périodique de l'extraction des données météorologiques. Le script fonctionne avec une ville par défaut (Toulouse) si aucun argument n'est fourni. Une tâche cron est configurée pour automatiser l'exécution du script à intervalles réguliers, garantissant une collecte continue des données météorologiques sans intervention manuelle.

Version 3 : Gestion de l'historique des données

La version 3 introduit la gestion de l'historique des données météo, permettant de sauvegarder les données quotidiennement dans des fichiers spécifiques à chaque jour. Chaque exécution du script ajoute les informations dans un fichier nommé selon le format meteo_YYYYMMDD.txt (où YYYYMMDD représente la date du jour). Ce fichier d'historique conserve toutes les données collectées au cours de la journée.


Variante 1 : Ajout d'informations météorologiques supplémentaires

La variante 1 étend la version de base en ajoutant la récupération d'informations supplémentaires telles que la vitesse du vent, le taux d'humidité et la visibilité. Ces informations sont ajoutées au fichier meteo.txt. 

Exemple :

2024-10-31 - 18:38 - Toulouse : Température actuelle : 19°C - Prévision du lendemain : 21°C - Vent : 18 km/h - Humidité : 73% - Visibilité : 10 km

Variante 2 : Option de sauvegarde en format JSON

La variante 2 ajoute la possibilité de sauvegarder les données en format JSON. L'utilisateur peut choisir s'il souhaite créer un fichier JSON grâce à une interaction dans le script (avec un if et une boucle while pour obtenir une réponse valide).

Exemple en format JSON  :
{
  "date": "2024-10-31",
  "Heure": "18:38",
  "Ville": "Toulouse",
  "Température actuelle": "19°C",
  "Prévision du lendemain": "21°C",
  "Vent": "18 km/h",
  "Humidité": "73%",
  "Visibilité": "10 km"
}

Variante 3 : Gestion des erreurs et des logs

La variante 3 améliore la gestion des erreurs et introduit un système de logs. En cas de problème avec la connexion à wttr.in, un message d'erreur est écrit dans un fichier meteo error.log avec un horodatage, ce qui facilite le suivi des incidents et la maintenance.

Exemple :

[2024-10-31 18:38:00] Erreur : Impossible de se connecter à wttr.in pour la ville de Toulouse.
[2024-10-31 18:39:00] Erreur : La ville Toulouse est inconnue ou les données sont manquantes.

Configuration d'une tâche Cron

Pour automatiser la collecte des données météo, vous pouvez utiliser une tâche cron. Voici les étapes :
Ouvrez l’éditeur de crontab en utilisant la commande crontab -e. Cette commande ouvre le fichier de configuration crontab de l'utilisateur actuel dans l'éditeur par défaut.
Ajoutez la ligne de commande cron que vous souhaitez exécuter. Par exemple, pour exécuter le script Extracteur_Meteo.sh tous les jours à 7 h du matin, ajoutez la ligne suivante : 0 7 * * * /home/louane/projet_poste3/Extracteur_Meteo.sh >> /home/louane/projet_poste3/meteo.log 2>&1
Enregistrez et quittez l’éditeur
Pour vérifier la tâche cron et pour être sûr qu’elle est bien enregistrée, en listant toutes les tâches cron de l’utilisateur utiliser la commande  crontab -l. Puis consulter, le fichier meteo.log pour vérifier que votre tâche s'exécute comme prévu. 

Exécution du script :
Exécutez le script en spécifiant la ville si nécessaire (ou par défaut Toulouse sera utilisée). 
Pour cela, tapez la commande :
./Extracteur_Meteo.sh <ville>
Par exemple :
./Extracteur_Meteo.sh Toulouse

Le script va :

- Récupérer les données météorologiques (température actuelle, prévision pour le lendemain, etc.).
- Enregistrer les informations récupérées dans un fichier texte spécifique à la journée (meteo_YYYYMMDD.txt).
- Demander à l'utilisateur s'il souhaite créer un fichier JSON contenant les mêmes informations.

Les principales fonctionnalités du script final sont :

- Extraire la température actuelle, la température prévue pour le lendemain, la vitesse du vent, l'humidité et la visibilité.
- Sauvegarder des données sous forme de fichier texte et possibilité de sauvegarde en format JSON dans un fichier JSON.
- La gestion des erreurs avec le fichier meteo_error.log.
- Automatiser la collecte des données via cron.

Ce script offre un outil complet pour l'extraction, la sauvegarde, et l'analyse des données météorologiques.

