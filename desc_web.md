i# Descriptif fonctionnel web

Ce document a pour but de vous présenter les principales fonctionnalités de l'application web.


# API

L'API est interrogé par tous nos services (Site web, application C, Application mobile etc..)
Elle parse une partie de l'API OpenFoodFacts et interroge la base de donnée. L'authentification se fait par le billais d'une clé de session a usage unique, hors mis des clés d'API spécial pour les programmes annexes de traitement.

### - Compte

| Fonction | Description |  Usage |  Methode | Route  |
|--|--|--|--|--|
| Connexion | L'utilisateur peut se connecter en utilisant son adresse email et son mot de passe  l'API lui renvois un token qui permet de l'identifier tout le long de sa session.|  @param string => [USER_EMAIL]  <br/> @param string => [USER_PASSWORD} <br/> @return string [API_KEY]|  POST  | /login
| Inscription | L'utilisateur peut créer un compte avec un email et un mot de passe, puis un tableau d'information le concernant| @param string => [USER_EMAIL]<br/> @param string => [USER_PASSWORD] <br />  @param json => [USER_INFORMATIONS]  | POST  | /register
|Information du compte| L'utilisateur peut recuperer les informations de son compte, l'etat de ses adhésions, les mandats de prélevements son adresse email et son adresse postal.| - | - | - 
|Modification du mot de passe| L'utilisateur peut modifier son mot de passe| - | - | - 
|Modification des informations du compte | L'utilisateur peut modifier ses informations : <br /> - IBAN<br /> - Adresse postale <br /> - Numero de telephone| - | - | - 

### - Adhesion
| Fonction | Description |  Usage |  Methode | Route  |
|--|--|--|--|--|
| Adhesion |  L'utilisateur peut ajouter une adhésion a son compte : <br /> - Particulier (Legalement non adhérent, il propose des listes de produits) <br /> - Entreprise (Abonnement en prelevement SEPA de 20E/mois ) <br /> - Membre (Cotisation membre facturé par carte a la creation du compte puis en prelevement SEPA mensuel de 5e/mois) <br /> | -  |  -  | - 
|Mise en pause de l'adhesion| L'utilisateur peut mettre en pause son adhésion, les prevelements sont stoppés| - | - | - 
|Annulation de l'adhesion| L'utilisateur peut mettre annulé son adhésion, **les mandats de prelevements sont supprimés**| - | - | - 
|Mise en pause de l'adhesion| L'utilisateur peut mettre en pause son adhésion, les prevelements sont stoppés| - | - | - 

### - Liste
| Fonction | Description |  Usage |  Methode | Route  |
|--|--|--|--|--|
| Proposition de liste | L'adhérent peut proposer une liste de produit, cette liste est mise en attente et doit etre validé par le staff de l'association. La liste est une chaine JSON contenant le code barre de chaque produit le nom commun et la quantité. l'API ajoute a ce JSON l'identifiant de l'adhérent ayant proposé cette liste.| -  |  -  | - 
| Annulation de liste | Une liste proposé par un adhérent peut etre annulé par celui-ci, cette liste est alors **supprimée de la base de donnée**| -  |  -  | - 
| Acceptation de liste | Le staff de l'association peut valider une liste proposé par un adhérent, la liste est en **attente de recuperation** et l'adresse de l'adhérent est ajouté aux adresses de la futur tournée. L'adhérent est avertit| -  |  -  | - 
| Refus de liste | Le staff de l'association peut refuser une liste, celle-ci prend alors l'etat **refusée** et l'adhérent est avertit.| -  |  -  | - 

### - Fonctionnel 
| Fonction | Description |  Usage |  Methode | Route  |
|--|--|--|--|--|
|Stock| Les tokens spéciaux peuvent recuperer tous les produits de toutes les listes acceptés | . | . | . |
|Route | Les tockens spéciaux peuvent recuperer les addresses de chaque points de passage | . | . | . |

# Plateforme Web

### - Compte
| Fonction | Description | Interface |
|--|--|--|
|Connexion  | L'utilisateur peut se connecter  | API |
| Inscription | L'utilisateur peut créer un compte | API|
| Moodification du mot de passe | L'utilisateur peut modifier son mot de passe | API|
| Moodification des informations du compte | L'utilisateur peut modifier ses informations tels que address, IBAN, numero de telephone. Cette chaine JSON est stockée en base de donnée est est evolutive. | API |

### - Adhesion
| Fonction | Description | Interface |
|--|--|--|
|Adherer  | L'utilisateur peut adherer en renseignant sont IBAN et son forfait (Entreprise, particulier, membre).  | API |
|Mettre en pause l'adhesion| L'utilisateur peut suspendre son adhésion, son mandat de prelevement est conservé pour reprendre l'abonnement. | API |
|Annuler l'adhésion| L'utilisateur peut annuler son adhesion, le mandat de prelevement est supprimé| API |

### - Listes
| Fonction | Description | Interface |
|--|--|--|
| Voir l'etat de ses listes | L'utilisateur peut voir ses listes et leurs états (En attente, refusé ou accepté) | API |
| Annuler des listes| L'utilisateur peut annuler des listes qu'il a proposé | API |

### - Blog
| Fonction | Description | Interface |
|--|--|--|
| Créer un poste| Le staff peut ajouter un poste au blog | MySQL |
| Editer un poste| Le staff peut editer un poste | MySQL |
|Supprimer un poste| Le staff peut supprimer un poste | MySQL |
