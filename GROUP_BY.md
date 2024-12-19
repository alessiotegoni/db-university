# Query With GROUP BY

## 1. Contare quanti iscritti ci sono stati ogni anno

```sql
SELECT COUNT(*) AS enrolments_count, YEAR(enrolment_date)
FROM students
GROUP BY YEAR(enrolment_date);
```

## 2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio

```sql
SELECT COUNT(*) AS same_office_address_count, office_address
FROM teachers
GROUP BY office_address;
```

## 3. Calcolare la media dei voti di ogni appello d'esame

```sql
SELECT AVG(vote), exam_id
FROM exam_student
GROUP BY exam_id;
```

## 4. Contare quanti corsi di laurea ci sono per ogni dipartimento

```sql
SELECT COUNT(*) AS degrees_count, department_id
FROM degrees
GROUP BY department_id;
