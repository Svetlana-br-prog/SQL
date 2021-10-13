#### В DBeaver подключиться к БД
```
Host: 159.69.151.133
Port: 5056
DB: qa_sql_train_db
User: user_22_x
Pass: ********
```
***
- Вывести все поля и все строки:  
```
SELECT*FROM qa_users 
```
- Вывести всех студентов в таблице:

```
SELECT username 
FROM qa_users 
```

- Вывести только id пользователей
```
SELECT user_id
FROM qa_users
```

- Вывести только имя пользователей
```
SELECT username 
FROM qa_users 
```
- Вывести только email пользователей
```
SELECT email
FROM qa_users 
```
- Вывести имя и email пользователей
```
SELECT username, email
FROM qa_users qu 
```
- Вывести id, имя, email и дату создания пользователей
```
SELECT user_id, email, created_on
FROM qa_users 
```
- Вывести пользователей где password 12333
```
SELECT * FROM qa_users 
WHERE password = '12333'
```
- Вывести пользователей которые были созданы 2021-03-26 00:00:00
```
SELECT * FROM qa_users 
WHERE created_on = '2021-03-26 00:00:00'
```
- Вывести пользователей где в имени есть слово Аnnа
```
SELECT * FROM qa_users 
WHERE username LIKE '%Anna%'
```
- Вывести пользователей где в имени в конце есть 8
```
SELECT * FROM qa_users 
WHERE username LIKE '%8%'
```
- Вывести пользователей где в имени в есть буква а
```
SELECT * FROM qa_users 
WHERE username LIKE '%a%'
```
- Вывести пользователей которые были созданы 2021-07-12 00:00:00
```
SELECT * FROM qa_users 
WHERE created_on = '2021-07-12 00:00:00'
```
- Вывести пользователей которые были созданы 2021-07-12 00:00:00 и имеют пароль 1m313
```
SELECT * FROM qa_users 
WHERE created_on = '2021-07-12 00:00:00' AND password = '1m313'
```
- Вывести пользователей которые были созданы 2021-07-12 00:00:00 и у которых в имени есть слово Andrey
```
SELECT * FROM qa_users 
WHERE created_on = '2021-07-12 00:00:00' AND username LIKE '%Andrey%'
```
- Вывести пользователей которые были созданы 2021-07-12 00:00:00 и у которых в имени есть цифра 8
```
SELECT * FROM qa_users  
WHERE created_on = '2021-07-12 00:00:00' AND username LIKE '%8%'
```
- Вывести пользователя у которых id равен 10
```
SELECT * FROM qa_users  
WHERE user_id = '10'
```
- Вывести пользователя у которых id равен 53
```
SELECT * FROM qa_users  
WHERE user_id='53'
```
- Вывести пользователя у которых id больше 40
```
SELECT * FROM qa_users 
WHERE user_id > 40
```
- Вывести пользователя у которых id меньше 30
```
SELECT * FROM qa_users  
WHERE user_id < 30
```
- Вывести пользователя у которых id меньше 27 или больше 88
```
SELECT * FROM qa_users 
WHERE user_id < 27 OR user_id > 88
```
- Вывести пользователя у которых id меньше либо равно 37
```
SELECT * FROM qa_users 
WHERE user_id <= 37
```
- Вывести пользователя у которых id больше либо равно 37
```
SELECT * FROM qa_users 
WHERE user_id >= 37
```
- Вывести пользователя у которых id больше 80 но меньше 90
```
SELECT * FROM qa_users 
WHERE user_id > 80 AND user_id < 90
```
- Вывести пользователя у которых id между 80 и 90
```
SELECT * FROM qa_users  
WHERE user_id BETWEEN 80 AND 90
```
- Вывести пользователей где password равен 12333, 1m313, 123313
```
SELECT * FROM qa_users 
WHERE password IN ('12333', '1m313', '123313')
```
- Вывести пользователей где created_on равен 2020-10-03 00:00:00, 2021-05-19 00:00:00, 2021-03-26 00:00:00
```
SELECT * FROM qa_users 
WHERE created_on IN ('2020-10-03 00:00:00', '2021-05-19 00:00:00', '2021-03-26 00:00:00')
```
- Вывести минимальный id
```
SELECT MIN(user_id)
FROM qa_users 
```
- Вывести максимальный id
```
SELECT MAX(user_id)
FROM qa_users 
```
- Вывести количество пользователей
```
SELECT COUNT(*) FROM qa_users 
```
- Вывести id пользователя, имя, дату создания пользователя. Отсортировать по порядку возрастания даты добавления пользоватлеля.
```
SELECT user_id, username, created_on
FROM qa_users
ORDER BY created_on
```
- Вывести id пользователя, имя, дату создания пользователя. Отсортировать по порядку убывания даты добавления пользоватлеля.
```
SELECT user_id, username, created_on 
FROM qa_users 
ORDER BY created_on DESC
```