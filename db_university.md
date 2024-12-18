
# SQL Queries Documentation

## 1. Selezionare tutti gli studenti nati nel 1990

### Query:

```sql
SELECT * 
FROM students AS s 
WHERE YEAR(s.date_of_birth) = 1990;
```

## 2. Selezionare tutti i corsi che valgono più di 10 crediti

### Query:

```sql
SELECT * 
FROM courses AS c
WHERE c.cfu > 10;
```

## 3. Selezionare tutti gli studenti che hanno più di 30 anni

### Query:

```sql
SELECT *
FROM students AS s
WHERE TIMESTAMPDIFF(YEAR, s.date_of_birth, CURDATE()) > 30;
```

## 4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di laurea

### Query:

```sql
SELECT * 
FROM courses AS c
WHERE c.period = "I semestre" AND c.year = 1;
```

## 5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del 20/06/2020

### Query:

```sql
SELECT *
FROM exams AS e
WHERE DATE(e.date) = '2020-06-20' AND TIME(e.hour) > '14:00:00';
```

## 6. Selezionare tutti i corsi di laurea magistrale

### Query:

```sql
SELECT *
FROM degrees AS d
WHERE d.name LIKE "%Magistrale%";
```

## 7. Da quanti dipartimenti è composta l'università?

### Query:

```sql
SELECT COUNT(*) AS departments_length
FROM departments;
```

## 8. Quanti sono gli insegnanti che non hanno un numero di telefono?

### Query:

```sql
SELECT *
FROM teachers AS t
WHERE t.phone IS NULL;
```

## 9. Inserire nella tabella degli studenti un nuovo record con i propri dati

### Query:

```sql
INSERT INTO students (
    degree_id,
    name,
    surname,
    date_of_birth,
    fiscal_code,
    enrolment_date,
    registration_number,
    email
) VALUES (
    75,
    'Mario', 
    'Rossi',
    '1995-05-15',
    'RSSMRA95E15F205Z',
    '2023-10-01', 
    '123456',
    'mario.rossi@example.com'
);
```

## 10. Cambiare il numero dell’ufficio del professor Pietro Rizzo in 126

### Query:

```sql
UPDATE teachers AS t
SET t.office_number = 126
WHERE t.name = "Pietro" AND t.surname = "Rizzo";
```

## 11. Eliminare dalla tabella studenti il record creato precedentemente al punto 9

### Query:

```sql
DELETE FROM students
WHERE students.id = 5002;
```

