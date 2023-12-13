# Selezionare tutti gli studenti iscritti al Corso di Laurea in Economia
```sql
    SELECT `students`.`name`, `students`.`surname`, `students`.`fiscal_code` AS `matrix`, `degrees`.`name` 
    FROM `students` 
    JOIN `degrees` 
    ON `degrees`.`id` = `students`.`degree_id` 
    WHERE `degrees`.`name` = 'Corso di Laurea in Economia';
```
# Selezionare tutti i Corsi di Laurea Magistrale del Dipartimento di Neuroscienze
```sql
    SELECT `degrees`.`name`, `departments`.`name`
    FROM `degrees` 
    JOIN `departments` 
    ON `departments`.`id` = `degrees`.`department_id` 
    WHERE `departments`.`name` = 'Dipartimento di Neuroscienze' AND `degrees`.`level` = 'magistrale' 
```

# Selezionare tutti i corsi in cui insegna Fulvio Amato (id=44)
```sql
    SELECT `courses`.`name` AS `nome_corso`, `teachers`.`name`, `teachers`.`surname`
    FROM `course_teacher` 
    JOIN `teachers`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
    JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
    WHERE `teachers`.`id` = 44
```

# Selezionare tutti gli studenti con i dati relativi al corso di laurea a cui sono iscritti e il relativo dipartimento, in ordine alfabetico per cognome e nome
```sql
    SELECT `students`.`name`, `students`.`surname`,
    `degrees`.`name`, `departments`.`name`
    FROM `students` 
    JOIN `degrees`
    ON `degrees`.`id` = `students`.`degree_id`
    JOIN `departments`
    ON `departments`.`id` = `degrees`.`department_id`
    ORDER BY `students`.`surname`,`students`.`name` ASC;
```

# Selezionare tutti i corsi di laurea con i relativi corsi e insegnanti
```sql
    SELECT `degrees`.`name` AS `degree`,`courses`.`name` AS `course`, `teachers`.`name` AS `teacher_name`, `teachers`.`surname` AS `teacher_surname`
    FROM `course_teacher` 
    JOIN `courses`
    ON `courses`.`id` = `course_teacher`.`course_id`
    JOIN `teachers`
    ON `teachers`.`id` = `course_teacher`.`teacher_id`
    JOIN `degrees`
    ON `degrees`.`id` = `courses`.`degree_id`
    ORDER BY `degrees`.`name`, `courses`.`name`, `teachers`.`name`, `teachers`.`surname` ASC
```

# Selezionare tutti i docenti che insegnano nel Dipartimento di Matematica (54)
``` sql 
    SELECT DISTINCT `teachers`.`id` AS `teachers_id`, `teachers`.`name` AS `teachers_name`,`teachers`.`surname` AS `teachers_surname`,`departments`.`name`
    FROM `teachers` 
    JOIN `course_teacher`
    ON `course_teacher`.`teacher_id` = `teachers`.`id`
    JOIN `courses`
    ON `course_teacher`.`course_id` = `courses`.`id`
    JOIN `degrees`
    ON `courses`.`degree_id` = `degrees`.`id`
    JOIN `departments`
    ON `degrees`.`department_id` = `departments`.`id`
    WHERE `departments`.`name` = 'Dipartimento di Matematica'
    ORDER BY `teachers`.`surname`, `teachers`.`surname` ASC; 
```

# BONUS: Selezionare per ogni studente il numero di tentativi sostenuti per ogni esame, stampando anche il voto massimo Successivamente, filtrare i tentativi con voto minimo 18
``` sql 
    SELECT `students`.`name`, `students`.`surname`, `courses`.`name` AS `nome_del_corso`,COUNT(`exam_student`.`exam_id`) AS `tentativi`
    FROM `exam_student`
    JOIN `students`
    ON `exam_student`.`student_id` = `students`.`id`
    JOIN `exams`
    ON `exam_student`.`exam_id` = `exams`.`id`
    JOIN `courses`
    ON `exams`.`course_id` = `courses`.`id`
    GROUP BY `students`.`id`, `courses`.`id`
    ORDER BY `students`.`name`, `students`.`surname` ASC;
```