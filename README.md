# Documentation du Projet des requêtes SQL de l'application :

## Afficher la liste des livres avec leur statut :
SELECT titre, isbn, statut FROM livres ;

## Ajouter un livre au catalogue :
INSERT INTO livres (titre, isbn, pageCount, publiéDate_dt_txt, thumbnailUrl, shortDescription, longDescription, statut) VALEURS ('Nouveau Livre', '1234567890', 200, '2023-01-01', 'url_image', 'Description courte.. .', 'Description longue...', 'Disponible');

## Supprimer un livre du catalogue s'il n'est pas emprunté :
DELETE FROM livres WHERE ID = [ID_Livres] AND status = 'Disponible';

## Afficher la fiche descriptive d'un livre enregistré en BDD :
SELECT * FROM livres WHERE ID = [ID_Livres];

## Modifier le statut d'un livre (Disponible/Prêt) :
UPDATE livres SET status = 'emprunts' WHERE ID = [ID_Livres];

## Afficher la liste de tous les utilisateurs avec leurs informations :
SELECT * FROM Utilisateurs ;

# Afficher les informations d'un utilisateur et les livres qu'il a éventuellement empruntés :
SELECT utilisateurs.*, livres.title, livres.publishedDate_dt_txt FROM utilisateurs 
LEFT JOIN emprunts ON utilisateurs.ID = emprunts.ID_Utilisateurs 
LEFT JOIN livres ON emprunts.ID_Livre = livres.ID 
WHERE utilisateurs.ID = [ID_Utilisateurs];
