#### В DBeaver подключиться к БД
```
Host: 159.69.151.133
Port: 5056
DB: qa_db_2
User: user_22_x
Pass: *********
```
***
- Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.
```
SELECT employee_name, employees_salary.monthly_salary
FROM employees 
JOIN employees_salary ON employees_salary.employee_id = employees.id
```
|employee_name|monthly_salary|
|-------------|--------------|
|Dmitry       |2300          |
|Elena        |1500          |
|Alex         |1000          |
|Victor       |1100          |
|Elena        |2100          |
|Anna         |1400          |
|Milana       |1500          |
|Olga         |1700          |
|Sergey       |1750          |
|Vadim        |1750          |
|Anton        |1850          |
|James        |1850          |
|Luna         |2000          |
|Aria         |2200          |
|Valentina    |2800          |
|Henry        |4100          |
|Oliver       |700           |
|David        |1000          |
|Luke         |900           |
|Leo          |1100          |
|Scarlett     |1200          |
|Penelope     |1600          |
|Nora         |1620          |
|Lily         |2350          |
|Dominic      |1900          |

- Вывести всех работников у которых ЗП меньше 2000.
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary ON employees.id = employees_salary.employee_id 
WHERE monthly_salary < 2000
```
|employee_name|monthly_salary|
|-------------|--------------|
|Elena        |1500          |
|Alex         |1000          |
|Victor       |1100          |
|Anna         |1400          |
|Milana       |1500          |
|Olga         |1700          |
|Sergey       |1750          |
|Vadim        |1750          |
|Anton        |1850          |
|James        |1850          |
|Oliver       |700           |
|David        |1000          |
|Luke         |900           |
|Leo          |1100          |
|Scarlett     |1200          |
|Penelope     |1600          |
|Nora         |1620          |
|Dominic      |1900          |

- Вывести все зарплатные позиции, но работник по ним не назначен.(ЗП есть, но не понятно кто её получает.)
```
SELECT employee_name, monthly_salary
FROM employees 
RIGHT JOIN employees_salary ON employees_salary.employee_id = employees.id
WHERE employee_name is Null
```
|employee_name|monthly_salary|
|-------------|--------------|
|NULL             |1700          |
|NULL             |1700          |
|NULL             |2700          |
|NULL             |2300          |
|NULL             |2300          |
|NULL             |1300          |
|NULL             |3000          |
|NULL             |1500          |
|NULL             |1900          |
|NULL             |2000          |
|NULL             |7000          |
- Вывести все зарплатные позиции  меньше 2000 но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
```
SELECT employee_name, monthly_salary
FROM employees 
RIGHT JOIN employees_salary ON employees_salary.employee_id = employees.id
WHERE monthly_salary < 2000 AND employee_name is Null
```
|employee_name|monthly_salary|
|-------------|--------------|
|NULL             |1700          |
|NULL               |1700          |
|NULL               |1300          |
|NULL               |1500          |
|NULL               |1900          |
- Найти всех работников кому не начислена ЗП.
```
SELECT employee_name, monthly_salary
FROM employees 
LEFT JOIN employees_salary ON employees.id = employees_salary.employee_id 
WHERE monthly_salary is Null
```
|employee_name|monthly_salary|
|-------------|--------------|
|Maya         |NULL          |
|Jacob        |NULL          |
|Victor       |NULL          |
|Marcus       |NULL          |
|Erik         |NULL          |
|George       |NULL              |
|Eva          |NULL              |
|Alice        |NULL              |
|Andrey       |NULL          |
|Ellie        |NULL          |
|Vera         |NULL          |
|Max          |NULL          |
|Samantha     |NULL          |
|Sophia       |NULL          |
|Clara        |NULL          |
|Jack         |NULL          |
|Matthew      |NULL          |
|Leonardo     |NULL          |
|Lucy         |NULL          |
|Samuel       |NULL          |
|Violet       |NULL          |
|Anton        |NULL          |
|Allison      |NULL          |
|Alexander    |NULL          |
|Naomi        |NULL          |
|Jordan       |NULL          |
|Lucas        |NULL          |
|Bella        |NULL          |
- Вывести всех работников с названиями их должности.
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
```
|employee_name|role_name                    |
|-------------|-----------------------------|
|Alex         |Middle Python developer      |
|Victor       |Junior Java developer        |
|Elena        |Senior Java developer        |
|Anna         |Junior Manual QA engineer    |
|Sergey       |Middle Java developer        |
|Vadim        |Junior Manual QA engineer    |
|Anton        |Middle Manual QA engineer    |
|Erik         |Senior Manual QA engineer    |
|Elena        |Designer                     |
|Marcus       |Project Manager              |
|Vera         |Sales manager                |
|Dmitry       |Senior Python developer      |
|Andrey       |Senior Python developer      |
|Anton        |Junior Java developer        |
|Victor       |Middle Java developer        |
|George       |Senior Java developer        |
|Max          |Senior Java developer        |
|Oliver       |Junior JavaScript developer  |
|Henry        |CEO                          |
|James        |Junior JavaScript developer  |
|Lucas        |Junior JavaScript developer  |
|Alexander    |Middle JavaScript developer  |
|Sophia       |Middle JavaScript developer  |
|Maya         |Senior JavaScript developer  |
|Jacob        |Senior JavaScript developer  |
|Jack         |Junior Manual QA engineer    |
|Samuel       |Junior Manual QA engineer    |
|Matthew      |Middle Manual QA engineer    |
|David        |Middle Manual QA engineer    |
|Luke         |Senior Manual QA engineer    |
|Leo          |Senior Manual QA engineer    |
|Luna         |Designer                     |
|Aria         |Designer                     |
|Scarlett     |HR                           |
|Penelope     |HR                           |
|Nora         |Sales manager                |
|Lily         |Sales manager                |
|Ellie        |Junior Automation QA engineer|
|Violet       |Middle Automation QA engineer|
|Lucy         |Senior Automation QA engineer|
|Dominic      |Middle JavaScript developer  |
- Вывести имена и должность только Java разработчиков.
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees on employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Java %'
```
|employee_name|role_name            |
|-------------|---------------------|
|Victor       |Junior Java developer|
|Elena        |Senior Java developer|
|Sergey       |Middle Java developer|
|Anton        |Junior Java developer|
|Victor       |Middle Java developer|
|George       |Senior Java developer|
|Max          |Senior Java developer|
- Вывести имена и должность только Python разработчиков.
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Python%'
```
|employee_name|role_name              |
|-------------|-----------------------|
|Alex         |Middle Python developer|
|Dmitry       |Senior Python developer|
|Andrey       |Senior Python developer|

- Вывести имена и должность всех QA инженеров.
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%QA%'
```
|employee_name|role_name                    |
|-------------|-----------------------------|
|Anna         |Junior Manual QA engineer    |
|Vadim        |Junior Manual QA engineer    |
|Anton        |Middle Manual QA engineer    |
|Erik         |Senior Manual QA engineer    |
|Jack         |Junior Manual QA engineer    |
|Samuel       |Junior Manual QA engineer    |
|Matthew      |Middle Manual QA engineer    |
|David        |Middle Manual QA engineer    |
|Luke         |Senior Manual QA engineer    |
|Leo          |Senior Manual QA engineer    |
|Ellie        |Junior Automation QA engineer|
|Violet       |Middle Automation QA engineer|
|Lucy         |Senior Automation QA engineer|
- Вывести имена и должность ручных QA инженеров.
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Manual QA%'
```
|employee_name|role_name                |
|-------------|-------------------------|
|Anna         |Junior Manual QA engineer|
|Vadim        |Junior Manual QA engineer|
|Anton        |Middle Manual QA engineer|
|Erik         |Senior Manual QA engineer|
|Jack         |Junior Manual QA engineer|
|Samuel       |Junior Manual QA engineer|
|Matthew      |Middle Manual QA engineer|
|David        |Middle Manual QA engineer|
|Luke         |Senior Manual QA engineer|
|Leo          |Senior Manual QA engineer|
- Вывести имена и должность автоматизаторов QA
```
SELECT employee_name, role_name
FROM employees 
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Automation QA%'
```
|employee_name|role_name                    |
|-------------|-----------------------------|
|Ellie        |Junior Automation QA engineer|
|Violet       |Middle Automation QA engineer|
|Lucy         |Senior Automation QA engineer|
- Вывести имена и зарплаты Junior специалистов
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Junior%'
```
|employee_name|monthly_salary|
|-------------|--------------|
|Victor       |1100          |
|Anna         |1400          |
|Vadim        |1750          |
|Oliver       |700           |
|James        |1850          |
- Вывести имена и зарплаты Middle специалистов
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary on employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Middle%'
```
|employee_name|monthly_salary|
|-------------|--------------|
|Alex         |1000          |
|Sergey       |1750          |
|Anton        |1850          |
|David        |1000          |
|Dominic      |1900          |
- Вывести имена и зарплаты Senior специалистов
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Senior%'
```
|employee_name|monthly_salary|
|-------------|--------------|
|Elena        |2100          |
|Dmitry       |2300          |
|Luke         |900           |
|Leo          |1100          |
- Вывести зарплаты Java разработчиков
```
SELECT monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Java %'
```
|monthly_salary|
|--------------|
|1100          |
|2100          |
|1750          |
- Вывести зарплаты Python разработчиков
```
SELECT monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Python%'
```
|monthly_salary|
|--------------|
|1000          |
|2300          |
- Вывести имена и зарплаты Junior Python разработчиков
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Junior Python%'
```
|employee_name|monthly_salary|
|-------------|--------------|
|             |              |
- Вывести имена и зарплаты Middle JS разработчиков
```
SELECT employee_name, monthly_salary
FROM employees 
LEFT JOIN employees_salary ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Middle JavaScript%'
```
|employee_name|monthly_salary|
|-------------|--------------|
|Alexander    |NULL              |
|Sophia       |NULL              |
|Dominic      |1900          |
- Вывести имена и зарплаты Senior Java разработчиков
```
SELECT employee_name, monthly_salary
FROM employees 
JOIN employees_salary ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%Senior Java %'
```
|employee_name|monthly_salary|
|-------------|--------------|
|Elena        |2100          |
- Вывести зарплаты Junior QA инженеров
```
SELECT monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE 'Junior% %QA%'
```
|monthly_salary|
|--------------|
|1400          |
|1750          |
- Вывести среднюю зарплату всех Junior специалистов
```
SELECT AVG(monthly_salary) AS avg_monthly_salary
FROM employees_salary 
JOIN employees on employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE 'Junior%'
```
|avg_monthly_salary   |
|---------------------|
|1360.00              |
- Вывести сумму зарплат JS разработчиков
```
SELECT SUM(monthly_salary) AS sum_monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%JavaScript%'
```
|sum_monthly_salary|
|------------------|
|4450              |
- Вывести минимальную ЗП QA инженеров
```
SELECT MIN(monthly_salary) AS min_monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%QA%'
```
|min_monthly_salary|
|------------------|
|900               |
- Вывести максимальную ЗП QA инженеров
```
SELECT MAX(monthly_salary) AS max_monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id 
WHERE role_name LIKE '%QA%'
```
|max_monthly_salary|
|------------------|
|1850              |
- Вывести количество QA инженеров
```
SELECT COUNT(role_name) AS count_QA_role_name
FROM roles 
JOIN roles_employees ON roles.id = roles_employees.role_id 
JOIN employees ON employees.id = roles_employees.employee_id  
WHERE role_name LIKE '%QA%'
```
|count_qa_role_name|
|------------------|
|13                |
- Вывести количество Middle специалистов.
```
SELECT COUNT(role_name) AS count_middle_role_name
FROM roles 
JOIN roles_employees ON roles.id = roles_employees.role_id 
JOIN employees ON employees.id = roles_employees.employee_id  
WHERE role_name LIKE 'Middle%'
```
|count_middle_role_name|
|----------------------|
|10                    |
- Вывести количество разработчиков
```
SELECT COUNT(role_name) AS count_developer_role_name
FROM roles 
JOIN roles_employees ON roles.id = roles_employees.role_id 
JOIN employees ON employees.id = roles_employees.employee_id  
WHERE role_name LIKE '%developer'
```
|count_developer_role_name|
|-------------------------|
|18                       |
- Вывести фонд (сумму) зарплаты разработчиков.
```
SELECT SUM(monthly_salary) AS sum_monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id  
WHERE role_name LIKE '%developer'
```
|sum_monthly_salary|
|------------------|
|12700             |
- Вывести имена, должности и ЗП всех специалистов по возрастанию
```
SELECT employee_name, role_name, monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id  
ORDER BY monthly_salary 
```
|employee_name|role_name                  |monthly_salary|
|-------------|---------------------------|--------------|
|Oliver       |Junior JavaScript developer|700           |
|Luke         |Senior Manual QA engineer  |900           |
|David        |Middle Manual QA engineer  |1000          |
|Alex         |Middle Python developer    |1000          |
|Victor       |Junior Java developer      |1100          |
|Leo          |Senior Manual QA engineer  |1100          |
|Scarlett     |HR                         |1200          |
|Anna         |Junior Manual QA engineer  |1400          |
|Elena        |Designer                   |1500          |
|Penelope     |HR                         |1600          |
|Nora         |Sales manager              |1620          |
|Sergey       |Middle Java developer      |1750          |
|Vadim        |Junior Manual QA engineer  |1750          |
|James        |Junior JavaScript developer|1850          |
|Anton        |Middle Manual QA engineer  |1850          |
|Dominic      |Middle JavaScript developer|1900          |
|Luna         |Designer                   |2000          |
|Elena        |Senior Java developer      |2100          |
|Aria         |Designer                   |2200          |
|Dmitry       |Senior Python developer    |2300          |
|Lily         |Sales manager              |2350          |
|Henry        |CEO                        |4100          |
- Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП от 1700 до 2300
```
SELECT employee_name, role_name, monthly_salary
FROM employees_salary 
JOIN employees on employees.id = employees_salary.employee_id
JOIN roles_employees on employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id  
WHERE monthly_salary >= 1700 AND monthly_salary <= 2300
ORDER BY monthly_salary 
```
|employee_name|role_name                  |monthly_salary|
|-------------|---------------------------|--------------|
|Sergey       |Middle Java developer      |1750          |
|Vadim        |Junior Manual QA engineer  |1750          |
|Anton        |Middle Manual QA engineer  |1850          |
|James        |Junior JavaScript developer|1850          |
|Dominic      |Middle JavaScript developer|1900          |
|Luna         |Designer                   |2000          |
|Elena        |Senior Java developer      |2100          |
|Aria         |Designer                   |2200          |
|Dmitry       |Senior Python developer    |2300          |
- Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП меньше 2300
```
SELECT employee_name, role_name, monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id  
WHERE monthly_salary < 2300
ORDER BY monthly_salary 
```
|employee_name|role_name                  |monthly_salary|
|-------------|---------------------------|--------------|
|Oliver       |Junior JavaScript developer|700           |
|Luke         |Senior Manual QA engineer  |900           |
|David        |Middle Manual QA engineer  |1000          |
|Alex         |Middle Python developer    |1000          |
|Leo          |Senior Manual QA engineer  |1100          |
|Victor       |Junior Java developer      |1100          |
|Scarlett     |HR                         |1200          |
|Anna         |Junior Manual QA engineer  |1400          |
|Elena        |Designer                   |1500          |
|Penelope     |HR                         |1600          |
|Nora         |Sales manager              |1620          |
|Sergey       |Middle Java developer      |1750          |
|Vadim        |Junior Manual QA engineer  |1750          |
|James        |Junior JavaScript developer|1850          |
|Anton        |Middle Manual QA engineer  |1850          |
|Dominic      |Middle JavaScript developer|1900          |
|Luna         |Designer                   |2000          |
|Elena        |Senior Java developer      |2100          |
|Aria         |Designer                   |2200          |

- Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП равна 1100, 1500, 2000
```
SELECT employee_name, role_name, monthly_salary
FROM employees_salary 
JOIN employees ON employees.id = employees_salary.employee_id
JOIN roles_employees ON employees.id = roles_employees.employee_id 
JOIN roles ON roles.id = roles_employees.role_id  
WHERE monthly_salary IN (1100, 1500, 2000)
ORDER BY monthly_salary
```
|employee_name|role_name                |monthly_salary|
|-------------|-------------------------|--------------|
|Victor       |Junior Java developer    |1100          |
|Leo          |Senior Manual QA engineer|1100          |
|Elena        |Designer                 |1500          |
|Luna         |Designer                 |2000          |