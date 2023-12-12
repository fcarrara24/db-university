1. Contare quanti iscritti ci sono stati ogni anno
- da students
```sql 
    SELECT COUNT(*) AS `immatricolazioni_annuali` FROM `students` 
    GROUP BY YEAR(`enrolment_date`);
```

2. Contare gli insegnanti che hanno l'ufficio nello stesso edificio
- da teachers
```sql 
    SELECT `office_address` ,COUNT(*) AS `numero_uffici` FROM `teachers` 
    GROUP BY (`office_address`);
```

3. Calcolare la media dei voti di ogni appello d'esame
- da exams
```sql 
    SELECT `exam_id`, AVG(`vote`) AS `average_score` FROM `exam_student` 
    GROUP BY (`exam_id`);
```

4. Contare quanti corsi di laurea ci sono per ogni dipartimento
```sql 
    SELECT `department_id`, COUNT(`name`) AS `number_of_courses` FROM `degrees` 
    GROUP BY (`department_id`);
```