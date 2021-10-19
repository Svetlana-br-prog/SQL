#### В DBeaver подключиться к БД
```
Host: 159.69.151.133
Port: 5056
DB: qa_db_22_x
User: user_22_x
Pass: *********
```
![Схема БД]()
***
-  Создайте базу из представленной картинки.
      - У каждой таблицы должно быть поле id
      - id автоинкрементальный и является первичным ключом
```
CREATE TABLE salary (
id serial PRIMARY KEY,
monthly_salary int NOT NULL
);
```
```
CREATE TABLE roles (
id serial PRIMARY KEY,
role_title VARCHAR(50) NOT NULL
);
```
```
CREATE TABLE roles_salary (
id serial PRIMARY KEY,
id_role int NOT NULL,
id_salary int NOT NULL,
FOREIGHN KEY (id_role)
	REFERENCES roles (id),
FOREIGHN KEY (id_salary)
	REFERENCES salary (id)
);

```
```
CREATE TABLE employees_roles (
id serial PRIMARY KEY,
id_role int NOT NULL,
id_employee int NOT NULL,
FOREIGHN KEY (id_role)
	REFERENCES roles (id),
FOREIGHN KEY (id_employee)
	REFERENCES employees (id)
);
```
```
CREATE TABLE employees (
id serial PRIMARY KEY,
employee_name VARCHAR(50) NOT NULL
);
```
```
CREATE TABLE claim (
id serial PRIMARY KEY,
service_id int NOT NULL,
employee_id int NOT NULL,
claim_date date,
sales_manager int NOT NULL,
FOREIGHN KEY (service_id)
	REFERENCES Service (id),
FOREIGHN KEY (employee_id)
	REFERENCES employees (id)
);
```
```
CREATE TABLE Service (
id serial PRIMARY KEY,
service_title VARCHAR(50) NOT NULL,
price int NOT NULL
);
```
```
CREATE TABLE materials (
id serial PRIMARY KEY,
suppliers_id int NOT NULL,
material_title VARCHAR(50) NOT NULL,
amount int NOT NULL,
price int NOT NULL,
FOREIGHN KEY (suppliers_id)
	REFERENCES Suppliers (id)
);
```
- Заполните таблицы данными. Не менее 10 строк в каждой таблице
```
INSERT INTO salary(id, monthly_salary) VALUES(default, 1200),(default, 1500),
(default, 1100),(default, 1800),(default, 2100),(default, 3200),(default, 1050);
```
|id |monthly_salary|
|---|--------------|
|1  |1200          |
|2  |1500          |
|3  |1100          |
|4  |1800          |
|5  |2100          |
|6  |3200          |
|7  |1050          |

```
INSERT INTO roles(id, role_title) VALUES(default, 'Installer'),(default, 'Builder'),
(default, 'Carpenter'),(default, 'Fitter'),(default, 'Decorator'),(default, 'Hoistman'),
(default, 'Slinger');
```
|id |role_title|
|---|----------|
|1  |Installer |
|2  |Builder   |
|3  |Carpenter |
|4  |Fitter    |
|5  |Decorator |
|6  |Hoistman  |
|7  |Slinger   |

```
INSERT INTO roles_salary(id, id_role, id_salary) VALUES(default, 5, 6),(default, 2, 7),
(default, 7, 5),(default, 6, 3),(default, 1, 4),(default, 3, 1),(default, 4, 2);
```
|id |id_role|id_salary|
|---|-------|---------|
|1  |5      |6        |
|2  |2      |7        |
|3  |7      |5        |
|4  |6      |3        |
|5  |1      |4        |
|6  |3      |1        |
|7  |4      |2        |

```
INSERT INTO employees(id, employee_name) VALUES(default, 'Angeli­na Jolie'),
(default, 'Armand Dou­glas'),(default, 'Char­l­ize Theron'),(default, 'Hen­ry William'),
(default, 'Jes­si­ca Alba'),(default, 'Jensen Ross'),(default, 'Megan Denise');
```
|id |employee_name    |
|---|-----------------|
|1  |Angeli­na Jolie  |
|2  |Armand Dou­glas  |
|3  |Char­l­ize Theron|
|4  |Hen­ry William   |
|5  |Jes­si­ca Alba   |
|6  |Jensen Ross      |
|7  |Megan Denise     |
```
INSERT INTO employees_roles(id, id_role, id_employee) VALUES(default, 5, 6),(default, 2, 7),
(default, 7, 5),(default, 6, 3),(default, 1, 4),(default, 3, 1),(default, 4, 2);
```
|id |id_role|id_employee|
|---|-------|-----------|
|1  |5      |6          |
|2  |2      |7          |
|3  |7      |5          |
|4  |6      |3          |
|5  |1      |4          |
|6  |3      |1          |
|7  |4      |2          |
```
INSERT INTO Service(id, service_title, price)
VALUES(default, 'Installation of elevators', 200), 
(default, 'Construction of buildings and communications', 350),(default, 'Flooring', 150),
(default, 'Assembly and installation of meshes', 750), 
(default, 'Painting the walls', 850), (default, 'Moving building materials', 950),
(default, 'Attach load to crane', 700);
```
|id |service_title                               |price|
|---|--------------------------------------------|-----|
|1  |Installation of elevators                   |200  |
|2  |Construction of buildings and communications|350  |
|3  |Flooring                                    |150  |
|4  |Assembly and installation of meshes         |750  |
|5  |Painting the walls                          |850  |
|6  |Moving building materials                   |950  |
|7  |Attach load to crane                        |700  |

```
INSERT INTO materials(id, suppliers_id, material_title, amount, price) VALUES(default, 3, 'Tackle', 1, 300),(default, 1, 'Bricks', 100, 5000),
(default, 2, 'Timber', 3000, 4500),(default, 7, 'Armature', 2000, 1200),(default, 4, 'Roller', 32, 120),
(default, 5, 'Jenny', 2, 2000),(default, 6, 'Slings', 1200, 800);
```
|id |suppliers_id|material_title|amount|price|
|---|------------|--------------|------|-----|
|1  |3           |Tackle        |1     |300  |
|2  |1           |Bricks        |100   |5000 |
|3  |2           |Timber        |3000  |4500 |
|4  |7           |Armature      |2000  |1200 |
|5  |4           |Roller        |32    |120  |
|7  |6           |Slings        |1200  |800  |
|6  |5           |Jenny         |2     |2000 |

```
INSERT INTO claim(id, service_id, employee_id, claim_date, sales_manager) VALUES(default, 1, 4, '2020-01-12', 321),
(default, 2, 7, '2020-09-21', 430),(default, 3, 1, '2019-04-08', 541),(default, 4, 2, '2015-03-08', 670),
(default, 5, 6, '2019-02-13', 920),(default, 6, 3, '2012-04-16', 720),(default, 7, 5, '2011-03-19', 150);
```
|id |service_id|employee_id|claim_date|sales_manager|
|---|----------|-----------|----------|-------------|
|1  |1         |4          |2020-01-12|321          |
|2  |2         |7          |2020-09-21|430          |
|3  |3         |1          |2019-04-08|541          |
|4  |4         |2          |2015-03-08|670          |
|5  |5         |6          |2019-02-13|920          |
|6  |6         |3          |2012-04-16|720          |
|7  |7         |5          |2011-03-19|150          |

- Добавить таблицу Suppliers с полями id, name

```
CREATE TABLE Suppliers (
id serial PRIMARY KEY,
Suppliers_name VARCHAR(50) NOT NULL 
);
```
- Добавить 10 строк поставщиков в таблицу Suppliers

```
INSERT INTO Suppliers(id, Suppliers_name) VALUES(default, 'Olivia'),(default, 'Ava'),
(default, 'Amelia'),(default, 'Emily'),(default, 'Jessica'),(default, 'Isla'),
(default, 'Isabella');
```
|id |suppliers_name|
|---|--------------|
|1  |Olivia        |
|2  |Ava           |
|3  |Amelia        |
|4  |Emily         |
|5  |Jessica       |
|6  |Isla          |
|7  |Isabella      |

- Обновить таблицу Salary. Добавить varchar поле currency на 7 символов.

```
ALTER TABLE salary ADD currency VARCHAR(7);
```
```
UPDATE salary 
SET currency = 'Euro'
WHERE currency IS NULL;
```
```
UPDATE salary 
SET currency = 'Pound'
WHERE monthly_salary = 1100;
```
```
UPDATE salary 
SET currency = 'Pound'
WHERE monthly_salary = 3200;
```
```
UPDATE salary 
SET currency = 'Yen'
WHERE monthly_salary = 1200;
```
```
UPDATE salary 
SET currency = 'Rouble'
WHERE monthly_salary = 1800;
```

|id |monthly_salary|currency|
|---|--------------|--------|
|2  |1500          |Euro    |
|5  |2100          |Euro    |
|7  |1050          |Euro    |
|1  |1200          |Yen     |
|4  |1800          |Rouble  |
|6  |3200          |Pound   |
|3  |1100          |Pound   |