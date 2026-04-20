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


## Partie 2