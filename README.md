# SQL-exercices

## Partie 1

### Exercice 1
**Obtenir la liste des 10 villes les plus peuplées en 2012**
```sql
SELECT ville_nom_reel, ville_population_2012
FROM villes_france_free
ORDER BY ville_population_2012 DESC
LIMIT 10;
```
### Exercice 2
**Obtenir la liste des 50 villes ayant la plus faible superficie**
```sql
SELECT ville_nom_reel, ville_surface
FROM villes_france_free
ORDER BY ville_surface ASC
LIMIT 50;
```
### Exercice 3
**Obtenir la liste des départements d’outres-mer, c’est-à-dire ceux dont le numéro de département commencent par “97”**
```sql
SELECT departement_nom_uppercase
FROM departement 
WHERE departement_code >= 970
AND departement_code < 980
```
### Exercice 4
**Obtenir le nom des 10 villes les plus peuplées en 2012, ainsi que le nom du département associé**
```sql
SELECT ville_nom_reel, 
ville_departement
FROM villes_france_free
ORDER BY ville_population_2012 DESC
LIMIT 10
```
### Exercice 5
**Obtenir la liste du nom de chaque département, associé à son code et du nombre de commune au sein de ces département, en triant afin d’obtenir en priorité les départements qui possèdent le plus de communes**
```sql
SELECT departement.departement_nom, departement.departement_code, COUNT(villes_france_free.ville_id) AS nombre_communes FROM departement JOIN villes_france_free ON villes_france_free.ville_departement = departement.departement_code GROUP BY departement.departement_code ORDER BY nombre_communes DESC;
```
### Exercice 6
**Obtenir la liste des 10 plus grands départements, en terme de superficie**
```sql
SELECT departement.departement_nom, departement.departement_code, ROUND(SUM(villes_france_free.ville_surface), 2) AS "departement_surface"
FROM departement
JOIN villes_france_free ON departement.departement_code = villes_france_free.ville_departement
GROUP BY departement.departement_code
ORDER BY departement_surface DESC
LIMIT 10
```
### Exercice 7
**Compter le nombre de villes dont le nom commence par “Saint”**
```sql
SELECT villes_france_free.ville_nom, COUNT(villes_france_free.ville_nom) AS "nom_ville_avec_saint"
FROM villes_france_free
WHERE villes_france_free.ville_nom LIKE "saint%"
```
### Exercice 8
**Obtenir la liste des villes qui ont un nom existants plusieurs fois, et trier afin d’obtenir en premier celles dont le nom est le plus souvent utilisé par plusieurs communes**
```sql
SELECT villes_france_free.ville_nom, COUNT(villes_france_free.ville_nom) AS "nombre_doublon_nom_ville"
FROM villes_france_free
GROUP BY villes_france_free.ville_nom
HAVING COUNT(villes_france_free.ville_nom) >1
ORDER BY nombre_doublon_nom_ville DESC
```
### Exercice 9
**Obtenir en une seule requête SQL la liste des villes dont la superficie est supérieur à la superficie moyenne**
```sql
SELECT villes_france_free.ville_nom, villes_france_free.ville_surface, (SELECT AVG(villes_france_free.ville_surface) FROM villes_france_free) AS surface_moyenne
FROM villes_france_free 
WHERE villes_france_free.ville_surface > (SELECT AVG(villes_france_free.ville_surface) FROM villes_france_free );
```
```sql
SELECT *
FROM `villes_france_free`
WHERE `ville_surface` > (SELECT AVG(`ville_surface`) FROM `villes_france_free`)
```
### Exercice 10
**Obtenir la liste des départements qui possèdent plus de 2 millions d’habitants**
```sql
SELECT departement.departement_nom, villes_france_free.ville_departement, SUM(ville_population_2012) AS population_totale
FROM departement 
JOIN villes_france_free  
  ON departement.departement_code = villes_france_free.ville_departement
GROUP BY departement.departement_nom 
HAVING SUM(ville_population_2012) > 2000000;
```
### Exercice 11
**Remplacez les tirets par un espace vide, pour toutes les villes commençant par “SAINT-” (dans la colonne qui contient les noms en majuscule)**
```sql
UPDATE villes_france_free
SET villes_france_free.ville_nom = REPLACE(villes_france_free.ville_nom,"-", " ")
WHERE villes_france_free.ville_nom LIKE "SAINT-%"
```


## Partie 2

### Exercice 1
**Obtenir l’utilisateur ayant le prénom “Muriel” et le mot de passe “test11”, sachant que l’encodage du mot de passe est effectué avec l’algorithme Sha1.
**
```sql
```
### Exercice 2
**Obtenir la liste de tous les produits qui sont présent sur plusieurs commandes.
**
```sql
```

### Exercice 3
**Obtenir la liste de tous les produits qui sont présent sur plusieurs commandes et y ajouter une colonne qui liste les identifiants des commandes associées.
**
```sql
```

### Exercice 4
**
**
```sql
```

### Exercice 5
**
**
```sql
```

### Exercice 6
**
**
```sql
```

### Exercice 7
**
**
```sql
```

### Exercice 8
**
**
```sql
```

### Exercice 9
**
**
```sql
```

### Exercice 10
**
**
```sql
```

### Exercice 11
**
**
```sql
```
### Exercice 12
**
**
```sql
```

### Exercice 13
**
**
```sql
```

### Exercice 14
**
**
```sql
```