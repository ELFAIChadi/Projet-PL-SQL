# Projet-PL-SQL
Réalisation d'une interface en PL/SQL Oracle sur une base de données pour une application permettant à la scolarité de gérer l’occupation des salles d’enseignement durant une année universitaire.

Salle (NoSalle, Categorie, NbPlaces)
UE (CodeUE, NomUE, Formation, HC, HTD, HTP, HCRes, HTDRes, HTPRes)
Groupes (Groupe, Formation, Effectif)
Reservation (NoReservation, NoSalle, CodeUE, Groupe, Formation, Nature, Debut, Duree)
Categorie : Catégorie de la salle = {‘Amphi’ / ‘Salle’ / ‘Salle TP’}.
UE : Unité d’Enseignement.
Groupe = {‘CM’ / ‘CIn’ / ‘TDn’ / ‘TPn’} où n est un numéro d’ordre (si plusieurs groupes).
Formation : {‘L1MI’, ‘L2I’, ‘L3I’, ‘M1I’, …}.
HCRes, HTDRes, HTPRes : Heures d’enseignement réservées (initialement à 0), incrémentées lors des réservations.
Nature : {‘Cours’/ ’TD’ / ’TP’}.
Debut : Date et Heure de début de la réservation.
Duree : Durée de la réservation (en minutes). 


Concevoir un schéma physique de la base de données en tenant compte du maximum des
contraintes d’intégrité.

• Réaliser des opérations en PL/SQL permettant les traitements suivants :
- Saisie et mise à jour des salles, des enseignements, des groupes ;
- Réservation des salles ;
- Recherche/Calcul et affichage des informations répondant à différents besoins.
• Les traitements demandés nécessitent une analyse détaillée :
- Vérifier la cohérence des données vis-à-vis des contraintes d’intégrité ;
- Tenir compte du maximum de situations pour répondre à l’utilisateur ;
- Un jeu de données et des exemples d’exécution sont proposés dans le fichier test pour
expliciter les contraintes d’intégrité et pour tester vos opérations.
• Les traitements demandés seront réalisés sous forme de procédures et de fonctions. Les
procédures doivent être écrites de manière transactionnelle.
• Les procédures et les fonctions à écrire sont les suivantes


Les Procédure et fonctions demandés:

MajGroupe (Gpe in varchar2, Forma in varchar2, Eff in number)
- Tous les paramètres sont obligatoires ;
- Si le groupe de la formation (Gpe, Forma) n’existe pas il est ajouté, Effectif doit
être positif ;
- Si le groupe de la formation existe et Eff est positif, Effectif du groupe est
remplacé par Eff, sinon le groupe est supprimé ainsi que toutes ses réservations.
L3 Informatique – Bases de Données 2 – K. Chelghoum 3
ReservationsGroupe (Gpe in varchar2, Forma in varchar2)
- Recherche et affiche la liste chronologique des réservations d’un groupe d’une
formation (Gpe, Forma) ou de tous les groupes d’une formation si Gpe est omis.
La liste est présentée avec les informations suivantes : Début, Fin (Début+Durée),
CodeUE, NomUE, Nature, NoSalle, Gpe ;
- Si le groupe ou la formation n’existe pas, on affiche un message d’erreur ;
- Si la liste est vide, on affiche le message « Pas de réservation pour ce groupe ou
cette formation ».
EstLibre (Gpe in varchar2, Forma in varchar2, Debut in date, Duree in
number) return boolean
- Retourne ‘Vrai’ si le groupe est libre au créneau indiqué et ‘Faux’ sinon ;
- Si le groupe n’existe pas, on affiche un message d’erreur. 
