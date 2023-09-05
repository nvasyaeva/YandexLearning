
1. Напишите запрос, с помощью которого можно найти дубли в поле email из таблицы Sfaff.


SELECT *
FROM Staff
GROUP BY email
HAVING COUNT(email) > 1;


2. Напишите запрос, с помощью которого можно определить возраст каждого сотрудника из таблицы Staff на момент запроса.

SELECT staff_id,
	name,
	CURRENT_DATE - CAST(birthday AS date) AS age
FROM staff;


3. Напишите запрос, с помощью которого можно определить должность (Jobtitles.name) со вторым по величине уровнем зарплаты.

SELECT Jobtitles.name
FROM Jobtitles
WHERE Jobtitle_di in
	(SELECT Jobtitle_di
	 FROM Staff
	 ORDER BY salary DESC
	 OFFSET 1
	 LIMIT 1);