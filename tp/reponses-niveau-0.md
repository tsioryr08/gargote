## Partie schema relationnel
# 1.
categorie(**id**,libelle)
plat(**id**,nom,prix,#id_categorie)
commande(**id**,date_commande,numero_table)
commande_ligne(**id**,#id_commande,#id_plat,quantite,prix_unitaire)

# 2.
La table 'commande_ligne' contient une colonne prix_unitaire pour que si il y a une variation de prix , les anciennes commandes restent justes et le nouveau prix peut etre utilise. Si on pense plus loin, c'est pour eviter d'avoir un faux chiffre d'affaires pour le gargotte de Bao
