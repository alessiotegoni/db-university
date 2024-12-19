## Risultati delle query

### 1. Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```sql
SELECT s.* 
FROM students AS s
JOIN degrees AS d
ON s.degree_id = d.id
WHERE d.name LIKE '%Economia%';
```

### 2. Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```sql
SELECT d.* 
FROM degrees AS d
JOIN departments AS dp
ON d.department_id = dp.id
WHERE dp.name LIKE '%Neuroscienze%' AND d.level = 'magistrale';
```

### 3. Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```sql
SELECT c.* 
FROM courses AS c
JOIN course_teacher AS ct
ON c.id = ct.course_id
WHERE ct.teacher_id = 44;
```

### 4. Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```sql
SELECT s.name, s.surname, s.email, d.name AS degree_name, dp.name AS department_name
FROM students AS s
JOIN degrees AS d
ON s.degree_id = d.id
JOIN departments AS dp
ON d.department_id = dp.id
ORDER BY s.surname, s.name;
```

### 5. Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```sql
SELECT d.name AS degree_name, c.name AS course_name, CONCAT(t.name, ' ', t.surname) AS teacher_name
FROM degrees AS d
JOIN courses AS c
ON d.id = c.degree_id
JOIN course_teacher AS ct
ON c.id = ct.course_id
JOIN teachers AS t
ON ct.teacher_id = t.id;
```

### 6. Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (5)
```sql
SELECT DISTINCT t.*
FROM teachers AS t
JOIN course_teacher AS ct
ON t.id = ct.teacher_id
JOIN courses AS c
ON ct.course_id = c.id
JOIN degrees AS d
ON c.degree_id = d.id
WHERE d.department_id = 5;
```

### 7. BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo. Successivamente, filtrare i tentativi con voto minimo 18
```sql
SELECT es.student_id, es.exam_id, COUNT(*) AS attempts, MAX(es.vote) AS max_vote
FROM exam_student AS es
WHERE es.vote >= 18
GROUP BY es.student_id, es.exam_id;
```
