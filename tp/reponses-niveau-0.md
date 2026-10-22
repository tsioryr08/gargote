## Partie schema relationnel
# 1.
categorie(**id**,libelle)
plat(**id**,nom,prix,#id_categorie)
commande(**id**,date_commande,numero_table)
commande_ligne(**id**,#id_commande,#id_plat,quantite,prix_unitaire)

# 2.
La table `commande_ligne` contient une colonne `prix_unitaire` pour conserver le prix du plat au moment de la commande. Ainsi, si le prix du plat change plus tard dans la table plat, les anciennes commandes restent correctes. Si on veut aller plus loin, cela permet egalement de calculer le chiffre d'affaires reel de la gargote de Bao, sans utiliser les nouveaux prix pour les anciennes commandes.
**Exemple concret** : En janvier, le Mi sao coute 6 500 Ar. Un client en commande 2. En fevrier, Bao augmente le prix a 8 000 Ar.
- plat.prix = 8 000 Ar (nouveau prix).
- commande_ligne.prix_unitaire = 6 500 Ar (ancien prix).

Ainsi, l'ancienne commande reste correcte : le client a paye 13 000 Ar, et non 16 000 Ar.

# 3.
Quand on supprime une commande, toutes ses lignes sont automatiquement supprimees grace a l’instruction `ON DELETE CASCADE` definie sur la cle etrangere id_commande de la table `commande_ligne`.

# 4.
- Possibilite que le prix qu'on insere dans la carte soit negatif (-900 ar par exple)
- La quantite de chose qu'on commande peut etre negative (j ai teste via INSERT INTO commande_ligne (id_commande, id_plat, quantite, prix_unitaire)
VALUES (1, 1, -2, 3000);)
- Le numero de table peut etre negatif (test via INSERT INTO commande (numero_table)
VALUES (-5);)
