# Descriptif fonctionnel: appli C

Ce document a pour but de vous présenter les différentes fonctionnalités de notre application C.


# API
Pour chaque requête, notre API fera l'intermédiaire que ce soit entre notre programme et l'API OpenFoodFact mais aussi avec notre base de donnée. Cette API sera donc interrogé dans chaque fonctionnalité de notre application C (sauf pour l'interface graphique bien sûr) puisqu'une clé sera émise par celle-ci à la connexion d'un utilisateur et cette clé devra être transmise à chaque requête auquel cas l'utilisateur sera considéré comme déconnecté.
# Fonctionnalitées

| Fonctions |Description  | 
|--|--|
|Interface graphique| L'interface graphique sera codée à l'aide de GTK. Les widget mis à disposition par cette bibliothèque permettront de mettre en place les boutons et les champs nécessaires à l’interaction homme-machine pour notre application. |
|Connexion| Il sera demandé d'entrer son mail ainsi que son mot de passe, si celui-ci n'est pas valide , une note s'affichera pour en informer l'utilisateur. L'API sera interrogé par la fonction via la lib CURL et celle-ci retournera une clé API qui devra être stocké dans une variable tout au long de l'exécution de l'application C. Si cette clé n'est pas stocké, l'utilisateur sera considéré comme déconnecté. La variable est initialisée à 0 et gardera donc la même valeur si la clé n'a pas été stocké. L'utilisateur pourra créer au préalable son compte voir le supprimer sur l'application web. |
| Création d'une liste| Chaque jour, l'utilisateur doit pouvoir utiliser une nouvelle liste vierge qui sera sa lise de produit à ramasser du jour. Une nouvelle liste sera donc créé pour l'utilisateur si il se connecte à un jour différent de sa dernière connexion. Sinon il pourra ajouter des produits à sa liste du jour. |
| Ajout d'un produit à la liste| Une fois connecté et la liste créé ou non selon la dernière connexion de l'utilisateur, il sera possible à l'utilisateur d'ajouter un nouveau produit en rentrant le code en dessous du code barre ainsi que la quantité de produit du même type. Le code du produit ainsi que sa quantité sera envoyé à notre API par le biais de la lib CURL puis notre API requêtera l'API OpenFoodFact pour obtenir le produit correspondant au code produit saisi. On obtiendra un JSON en résultat qui devra être parsé par une lib dédié à cette fonctionnalité. |
| Suppression d'un produit à la liste| Comme pour la création, une requête est envoyée à l'API via CURL qui supprimera ensuite la-dite liste de notre base de donnée correspondant à l'utilisateur connecté|
| Envoie de la liste|  Les résultats ayants été parsés à chaque réponse de notre API nous avons plus qu'à envoyer cette liste par le biais d'une requête transmise par notre API à la base de données. Si une liste du jour existait déjà, la liste envoyée sera concaténé à la première liste du jour.|



