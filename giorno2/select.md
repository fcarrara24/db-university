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

