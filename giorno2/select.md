1. Selezionare tutti gli studenti nati nel 1990 (160)
- da students:
```sql
    SELECT * FROM `students` WHERE YEAR(`date_of_birth`) = 1990;
```

2. Selezionare tutti i corsi che valgono più di 10 crediti (479)
- da courses
```sql 
    SELECT * FROM `courses` WHERE `cfu` > 10;
```

3. Selezionare tutti gli studenti che hanno più di 30 anni
- da students
```sql 
    SELECT *
    FROM `students`
    WHERE DATEDIFF(CURDATE(), `date_of_birth`) / 365 > 30;
```

4. Selezionare tutti i corsi del primo semestre del primo anno di un qualsiasi corso di
laurea (286)
- da students
```sql 
    SELECT * FROM `courses` 
    WHERE `period` LIKE 'I %' AND `year` LIKE '1';
```

5. Selezionare tutti gli appelli d'esame che avvengono nel pomeriggio (dopo le 14) del
20/06/2020 (21)
- da exams
```sql 
    SELECT * FROM `exams` 
    WHERE `date` = '2020-06-20' 
    AND HOUR(`hour`) >= '14';
```

6. Selezionare tutti i corsi di laurea magistrale (38)
- degrees
```sql 
    SELECT * FROM `degrees` 
    WHERE `level` like 'magistrale'
```

7. Da quanti dipartimenti è composta l'università? (12)
- degrees
```sql 
    SELECT COUNT(`name`) AS `numero_dipartimenti` 
    FROM `departments`;
```

8. Quanti sono gli insegnanti che non hanno un numero di telefono? (50)
```sql 
    SELECT COUNT(*) AS `numero_professori_senza_telefono` 
    FROM `teachers`
    WHERE `phone` IS NULL;
```