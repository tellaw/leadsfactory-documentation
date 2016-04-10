# Méthode : getLead

Méthode utilisable pour récupérer des données de la lead’s. Cette méthode retourne un objet JSON contenant le détail d’un lead.

## Route d'appel

|Attribut | Description |
|---------|-------------|
|Route | /lead/{id}/{key} |
|Identifiant de route | Aucun |

## Parametres

|Attribut | Description |
|---------|-------------|
|id | Identifiant de la lead à charger |
|apikey | Code de sécurité de l’API. |

## Valeur de retour :

|Type | Description |
|-----|-------------|
|Json | Données encodées en JSON de la lead’s |

# Méthode : validateEmail

Méthode POST.

Cette méthode permet de déclarer un email comme validé à la lead’s.
Route d’appel :


## Route d'appel

|Attribut | Description |
|-----|-------------|
|Route | /email/validate |
|Identifiant de route | Aucun |
 
## Paramètre :

| Attribut | Description |
|-----|-------------|
| email | Email à déclarer comme valide|
 
## Valeurs de retour :

| Type | Description |
|-----|-------------|
| Json | Information sur l’action de validation |

# Méthode : getLeads

Méthode POST.

Méthode utilisable pour récupérer des données de la lead’s. Cette méthode retourne plusieurs objets JSON contenant le détail d’un lead.
Route d’appel :

## Route d'appel

| Attribut | Description |
|-----|-------------|
| Route | /leads |
| Identifiant de route | Aucun |
 
## Paramètre :

| Attribut | Description |
|-----|-------------|
| datemin | Date de début (date de création) : Format Y-m-d |
| datemax | Date de fin (date de création) : Format Y-m-d |
| Email | Possibilité de filtrer les lead’s par email |
| form | Possibilité de filtrer les lead’s par formulaire source |
 
## Valeur de retour :

| Type | Description |
|-----|-------------|
| Json | Données encodées en JSON des leads |
 

# Méthode : postLead

Méthode permettant d’injecter un lead’s dans la lead’s factory en méthode POST.

Attention, l’utilisation de cette méthode n’enregistre pas de pages vues. Vous risquez donc d’avoir des statistiques faux.
Route d’appel :

## Route d'appel

| Attribut | Description |
|-----|-------------|
| Route | /lead/post |
| Identifiant de route | Aucun |
 
## Paramètre :

| Attribut | Description |
|-----|-------------|
| content | Json de la lead’s à enregistrer |
 
## Valeur de retour :

| Type | Description |
|-----|-------------|
|boolean | 1 si succès & 0 en cas d’erreur. |

 
## Le JSON doit contenir des valeurs remarquables :

| Nom | Description | Obligatoire |
|-----|-------------|-------------|
| utmcampaign | Code action associé à la lead’s | non |
| firstName | Prénom | Oui |
| lastName | Nom | oui |
| phone | Téléphone | Non |
| email | Email | Non |
| formCode | Code technique du formulaire lié. | oui |

 
