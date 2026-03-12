<!--
1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di
Neuroscienze
3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui
sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e
nome
5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
6. Selezionare tutti i docenti che insegnano nel Dipartimento di
Matematica (54)
7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti
per ogni esame, stampando anche il voto massimo. Successivamente,
filtrare i tentativi con voto minimo 18.
 -->

# JOIN

## Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia

```sql
SELECT s.name,s.surname FROM students AS s INNER JOIN degrees AS d ON d.id=s.degree_id WHERE d.name="Corso di Laurea in Economia" LIMIT 10;
```

## Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze

```sql
select cou.* from departments as dep inner join degrees as deg on dep.id=deg.department_id inner join courses as cou on cou.degree_id=deg.id where dep.name like "%Neuroscienze" limit 5;
```
