# GROUP BY

## Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT count(id) AS students_for_year,YEAR(enrolment_date) AS year FROM students GROUP BY YEAR(enrolment_date);
```

## Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT count(id) AS numbers_of_teachers,office_address FROM teachers GROUP BY office_address;
```

## Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT exam_id,avg(vote) AS avg_vote FROM exam_student GROUP BY exam_id LIMIT 10;
```

## Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT count(courses.id) AS totale_corsi,departments.name FROM departments INNER JOIN degrees ON departments.id=degrees.department_id INNER JOIN courses ON degrees.id=courses.degree_id GROUP BY departments.name;
```
