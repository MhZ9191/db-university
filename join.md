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

## Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)

```sql
select cou.* from teachers as tea inner join course_teacher as ct on tea.id=ct.teacher_id inner join courses as cou on ct.course_id=cou.id where tea.id=44 limit 10;
```

## Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome

```sql
select stu.name,stu.surname,deg.name as dep_name,dep.name as department_name from students as stu inner join degrees as deg on stu.degree_id=deg.id inner join courses as cou on deg.id=cou.degree_id inner join departments as dep on dep.id=deg.department_id group by stu.name order by stu.name,stu.surname limit 10;
```

## Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti

```sql
select deg.name as degree_name,cou.name as course_name,concat(tea.name," ", tea.surname) as teacher_name  from degrees as deg inner join courses as cou on deg.id=cou.degree_id inner join course_teacher as ct on ct.course_id=cou.id inner join teachers as tea on tea.id=ct.teacher_id order by degree_name limit 10 ;
```

## Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)

```sql
select dep.name,concat(tea.name," ",tea.surname) as teacher from departments as dep inner join degrees as deg on dep.id=deg.department_id inner join courses as cou on cou.degree_id=deg.id inner join course_teacher as ct on ct.course_id=cou.id inner join teachers as tea
on ct.teacher_id=tea.id where dep.name like "%Matematica%" group by teacher;
```

## BONUS

```sql
select concat(stu.surname," ",stu.name) as student,count(stu.id) as tentativi, MAX(vote) as voto_massimo from students as stu inner join exam_student as es on stu.id=es.student_id inner join exams as exa on es.exam_id=exa.id group by stu.id having voto_massimo<=18 limit 10;
```
