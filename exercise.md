# Una query per domarle tutte

```sql
select (select count(*) from teachers where phone is not null) as nati_nel_1990,(select count(cfu) FROM courses WHERE cfu > 10) as cfu_maggiore_di_10,(select count(*) from students where timestampdiff(YEAR,date_of_birth,curdate())>=30) as maggiore_di_30_anni, (SELECT
count(*) FROM courses WHERE courses.period LIKE "I semestre" AND courses.year=1) as primo_semestre_primo_anno, (SELECT count(*) FROM exams WHERE
exams.date="2020-06-20" AND HOUR(exams.hour)>=14) as data_esame_pomeriggio, (SELECT count(*) FROM departments) as departments ,(SELECT count(*) FROM teachers WHERE phone IS NOT NULL) as insegnanti_no_cell;
```

## Selezionare tutti gli studenti nati nel 1990 (160)

```sql
SELECT count(*) AS Totale FROM students WHERE YEAR(date_of_birth)=1990;
```

```sql
SELECT concat("tot"," =  ",count(*)) AS Totale
FROM students
WHERE YEAR(date_of_birth)=1990;
```

```sql
SELECT count(*) AS Totale
FROM students
WHERE date_of_birth
BETWEEN "1990-01-01" AND "1990-12-31";
```

```sql
SELECT count(*) AS Totale
FROM students
WHERE date_of_birth >= "1990-01-01" AND date_of_birth <= "1990-12-31";
```

```sql
SELECT count(*) AS Totale FROM students WHERE date_of_birth LIKE "1990%";
```

## Selezionare tutti i corsi che valgono più di 10 crediti (479)

```sql
SELECT count(cfu) AS Totale FROM courses WHERE cfu > 10;
```

## Selezionare tutti gli studenti che hanno più di 30 anni

```sql
SELECT count(*) AS Totale
FROM students
WHERE timestampdiff(YEAR,date_of_birth,curdate())>=30;
```

## Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea (286)

```sql
SELECT count(*) AS Totale
FROM courses
WHERE courses.period LIKE "I semestre" AND courses.year=1;
```

```sql
SELECT count(*) AS Totale
FROM courses
WHERE substr(courses.period,2,1)=' ' AND courses.year=1;
```

## Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020 (21)

```sql
SELECT count(*) AS Totale
FROM exams
WHERE exams.date="2020-06-20" AND HOUR(exams.hour)>=14;
```

## Selezionare tutti i corsi di laurea magistrale (38)

```sql
SELECT count(*) AS Totale
FROM degrees
WHERE degrees.level LIKE "magistrale";
```

```sql
SELECT count(*) AS Totale
FROM degrees
WHERE substr(degrees.level,1,3)="mag";
```

## Da quanti dipartimenti è composta l'università? (12)

```sql
SELECT count(*) AS Totale FROM departments;
```

## Quanti sono gli insegnanti che non hanno un numero di telefono? (50)

```sql
SELECT count(*) AS Totale FROM teachers WHERE phone IS NOT NULL;
```
