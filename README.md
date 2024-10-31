README Projet Poste 3

Contenu du fichier README.md


Objectif du projet

L’objectif de ce projet est de créer un outil d’extraction d’information météorologique, plus précisément de créer un script Shell qui extrait périodiquement la température actuelle d'une ville donnée ainsi que les prévisions météorologiques pour le lendemain en utilisant le service wttr.in. Ce script enregistre les informations extraites dans un fichier texte, chaque enregistrement apparaissant sur une seule ligne. Ce projet comporte plusieurs variantes qui introduisent des fonctionnalités supplémentaires. Pour améliorer la synchronisation technique de notre projet, nous utilisons GIT pour garder chaque version y compris intermédiaire, et chaque intervention d’un membre du groupe.

La version 1 
La Version 2 permet l’automatisation périodique. Pour rendre l’application plus facile à employer, nous l’avons faites évoluer. Nous avons ajouté quelques éléments. D’abord, nous avons modifier le script pour lui permettre de fonctionner avec une ville par défaut, qui est ici Toulouse, au cas où aucun argument ne serait fourni. Nous avons aussi configuré une tâche cron pour automatiser l'exécution du script et enregistrer les données périodiquement. Et dans le README du projet, nous avons expliqué comment configurer une tâche cron.
La Version 3 

La Version alternative numero 1, permet de récuperer des informations plus complètes sur la météo de la journée en cours.
La Version Alternative Numéro 2, ajoute l'option de creation d'un fichier JSON

Configuration d'une tâche Cron

Pour automatiser la collecte des données météo, vous pouvez utiliser une tâche cron.
Voici les étapes :
    • Ouvrez l’éditeur de tâches cron avec cette commande : crontab -e
    • Modifiez ce fichier pour introduire les tâches à exécuter par cron.
Chaque tâche à exécuter doit être définie par une seule ligne indiquant avec différents champs quand la tâche sera exécutée et quelle commande exécuter pour la tâche. Pour définir l'heure, vous pouvez fournir des valeurs concrètes pour minute (m), heure (h), jour du mois (dom), mois (mon) et jour de la semaine (dow), ou utiliser '*' dans ces champs. Veuillez noter que les tâches seront lancées en fonction de la notion de temps et de fuseaux horaires du système de cron. Par exemple, vous pouvez automatiser l’exécution du script météo à des intervalles réguliers, comme au début de chaque heure :
0 * * * * /Extracteur_Meteo.sh >> /meteo.log 2>&1
Cette tâche exécutera le script périodiquement pour collecter les données météo sans intervention manuelle.
    • Enregistrez les modifications et fermez l’éditeur crontab.
La tâche cron est maintenant configurée et le script s’exécutera automatiquement selon l’intervalle défini.
    • Vérifier l'exécution des tâches cron
Pour vérifier que votre tâche s’exécute comme prévu, consultez le fichier de log défini (log_meteo.txt). Le fichier doit être mis à jour aux intervalles spécifiés avec les informations météo collectées.
