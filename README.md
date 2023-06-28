# mysql-schema-design
e-commerce Database in MySQL — schema
![Alt text](https://github.com/Ganeshk750/mysql-schema-design/blob/master/table-pic.PNG)
#### CREATE TABLE 
````
CREATE TABLE employee (
emp_id INT PRIMARY KEY,
first_name VARCHAR(40),
last_name VARCHAR(40),
birth_day DATE,
sex VARCHAR(1),
salary INT,
super_id INT,
branch_id INT);

CREATE TABLE branch (
branch_id INT PRIMARY KEY,
branch_name VARCHAR(40),
mgr_id INT,
mgr_start_date DATE,
FOREIGN KEY(mgr_id) REFERENCES employee(emp_id) ON DELETE SET NULL
);

CREATE TABLE client (
client_id INT PRIMARY KEY,
first_name VARCHAR(40),
last_name VARCHAR(40),
branch_id INT,
FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE SET NULL);

ALTER TABLE employee 
ADD FOREIGN KEY(branch_id)
REFERENCES branch(branch_id);

ALTER TABLE employee
ADD FOREIGN KEY(super_id)
REFERENCES employee(emp_id);


CREATE TABLE works_with (
emp_id INT,
client_id INT,
total_sales INT,
product_id INT,
PRIMARY KEY(emp_id, client_id),
FOREIGN KEY(emp_id) REFERENCES employee(emp_id) ON DELETE CASCADE,
FOREIGN KEY(client_id) REFERENCES client(client_id) ON DELETE CASCADE
);

CREATE TABLE branch_supplier (
branch_id INT,
supplier_name VARCHAR(40),
supply_type VARCHAR(40),
PRIMARY KEY(branch_id, supplier_name),
FOREIGN KEY(branch_id) REFERENCES branch(branch_id) ON DELETE CASCADE
);
````
#### Insert Data
````
-- Insurance Branch
INSERT INTO employee VALUES(20, 'Finn', 'Müller', '1967-05-12', 'M', 85000, NULL, NULL);
INSERT INTO branch VALUES(1, 'Insurance', 20, '2022-02-06');
UPDATE employee
SET branch_id = 1
WHERE emp_id = 20;
INSERT INTO employee VALUES(21, 'Lucas', 'Schmidt', '1972-08-30', 'M', 200000, 20, 1);
-- Account and Credit Branch
INSERT INTO employee VALUES(22, 'Jonas', 'Fischer', '1983-01-01', 'M', 65000, 22, NULL);
INSERT INTO branch VALUES(2, 'Account', 22, '2022-04-01');
UPDATE employee
SET branch_id = 2
WHERE emp_id = 22;
INSERT INTO employee VALUES(23, 'Ella', 'Weber', '1964-05-22', 'F', 170000, 22, 2);
INSERT INTO employee VALUES(24, 'Ida', 'Wagner', '1970-03-07', 'F', 90000, 22, 2);
INSERT INTO employee VALUES(25, 'Ben', 'Schneider', '1973-08-25', 'M', 72000, 22, 2);
-- Energy and Gas Branch
INSERT INTO employee VALUES(26, 'Oliver', 'Brown', '1989-03-02', 'M', 199000, 26, NULL);
INSERT INTO branch VALUES(3, 'Energy', 26, '2019-02-24');
UPDATE employee
SET branch_id = 3
WHERE emp_id = 26;
INSERT INTO employee VALUES(27, 'Leonie', 'Williams', '1977-07-07', 'F', 80000, 26, 3);
INSERT INTO employee VALUES(28, 'Lea', 'Zimmerman', '1983-12-05', 'F', 62000, 26, 3);
-- BRANCH SUPPLIER
INSERT INTO branch_supplier VALUES(1, 'S_Direkt', 'Insurance');
INSERT INTO branch_supplier VALUES(1, 'Inshared', 'Insurance');
INSERT INTO branch_supplier VALUES(2, 'Deutsche_Bank', 'Credit');
INSERT INTO branch_supplier VALUES(2, 'Commerzbank', 'Credit');
INSERT INTO branch_supplier VALUES(3, 'Ostrom', 'Renewable');
INSERT INTO branch_supplier VALUES(3, 'E.On_Energy', 'Electricity');
-- CLIENT
INSERT INTO client VALUES(10, 'Daniel', 'Maier', 2);
INSERT INTO client VALUES(11, 'Ella', 'Walter', 2);
INSERT INTO client VALUES(12, 'Zhang', 'Wei', 1);
INSERT INTO client VALUES(13, 'Ivan', 'Kirillov', 3);
INSERT INTO client VALUES(14, 'John', 'Smith', 3);
INSERT INTO client VALUES(15, 'Dirk', 'Pelletr', 1);
INSERT INTO client VALUES(16, 'Tobias', 'Roth', 1);
-- WORKS_WITH
INSERT INTO works_with VALUES(20, 10, 23000,1);
INSERT INTO works_with VALUES(21, 11, 500000,2);
INSERT INTO works_with VALUES(22, 12, 119000,3);
INSERT INTO works_with VALUES(22, 13, 3000,4);
INSERT INTO works_with VALUES(28, 14, 120000,5);
INSERT INTO works_with VALUES(22, 15, 6000,6);
INSERT INTO works_with VALUES(20, 15, 6000,7);
INSERT INTO works_with VALUES(25, 16, 55000,8);
INSERT INTO works_with VALUES(21, 11, 40000,9);
````
