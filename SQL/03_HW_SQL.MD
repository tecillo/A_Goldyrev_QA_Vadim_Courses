HW_3 SQL

Подключитесь к своей базе данных
SQL запросы и скрин диаграммы выгрузить на GitHub

Таблица с базами и пользователями - https://docs.google.com/spreadsheets/d/1cMpfCPcXeVyczGGhxjaM03gDoBp2pC8gx3oAE_SasTs/edit?usp=sharing

 1. Создайте базу из представленной картинки.
      - У каждой таблицы должно быть поле id
      - id автоинкрементальный и является первичным ключом
 2. Заполните таблицы данными. Не менее 10 строк в каждой таблице
 3. Добавить таблицу Suppliers с полями id, name
 4. Добавить 10 строк поставщиков в таблицу Suppliers
 5. Обновить таблицу Materials. Добавить поле suplier_id которое связано с полем id в таблице Suppliers
 6. Обновить таблицу Employees. Добавить varchar поле surname на 50 символов.
 7. Обновить таблицу Salary. Добавить varchar поле currency на 7 символов


create table employees (id serial primary key, employee_name varchar(100));
insert into employees (employee_name) values('Grigoriy Leps'), ('Alexandr Rybak'), ('Pavel Volya'), ('Alena Lanskaya'), ('Tom Hardy'), ('Nicolas Cage'), ('Bred Pit'), ('2pac Shakur'), ('Albert Einshtein'), ('Slavik Sidorov');


create table roles (id serial primary key, role_title varchar(50));
insert into roles (role_title) values('Master of none'), ('Master of cookies'), ('Master of ceremony'), ('Cookie apprentice'),('Ceremony apprentice'), ('None apprentice'), ('Mr. president'), ('The first lady'), ('Apprentice of the apprentices'), ('Master of masters');


create table Service (id serial primary key, service_title varchar(50), price_$ numeric);
insert into Service (service_title, price_$) values ('Cookie ceremony', 750), ('Cookie party', 1200), ('Cookie weekend', 3000), ('Cookie VIP', 7600), ('Cookie light', 250), ('Cookie night', 1500), ('Cookie cleaning', 100), ('Cookie wedding', 5000), ('Cookie funeral', 2500), ('Cookie moovie', 500);


create table materials (id serial primary key, material_title varchar(50), amount int, price int);
insert into materials (material_title, amount, price) values ('Cookie t-shirt', 1000, 5), ('Cookie box', 5000, 3), ('Cookie baloons', 1000, 1), ('Cookie hats', 1000, 7), ('Cookie coffin', 2, 500), ('Cookie dress', 1, 1000), ('Cookie lamp', 50, 25), ('Cookie castle', 1, 10000), ('Cookie cake', 1, 15), ('Cookie ice cream', 150, 2);


create table salary (id serial primary key, monthly_salary int);
insert into salary (monthly_salary) values (500), (700), (900), (1200), (3000), (4000), (5000), (7000), (10000), (1000000);

create table employees_roles (id serial primary key, id_role int, id_employee int, foreign key (id_role) references roles (id), foreign key (id_employee) references employees(id));
insert into employees_roles (id_role, id_employee) values (1,1), (2,4), (3,8), (4,7), (5,6), (6,5), (7,10), (8,3), (9,2), (10,9);

create table roles_salary (id serial primary key, id_role int, id_salary int, foreign key (id_role) references roles (id), foreign key (id_salary) references salary (id)); 
insert into roles_salary (id_role, id_salary) values (9,1), (6,2), (4,3), (5,4), (8,5), (1,6), (2,7), (3,8), (10,9), (7,10);

create table claim (id serial primary key, service_id int, employee_id int, material_id int, claim_date date, sales_manager int, foreign key (service_id) references service (id), foreign key (employee_id) references employees (id), foreign key (material_id) references materials (id), foreign key (sales_manager) references employees (id));  
insert into claim (service_id, employee_id, material_id, claim_date, sales_manager) values (1, 9, 2, null, 1), (2, 9, 2, null, 1), (3, 9, 2, null, 1), (4, 9, 2, null, 1), (5, 9, 2, null, 1), (6, 9, 2, null, 1), (7, 9, 2, null, 1), (8, 9, 2, null, 1), (9, 9, 2, null, 1), (10, 9, 2, null, 1);

create table Suppliers (id serial primary key, name varchar(50));
insert into Suppliers (name) values ('Vasia'), ('Kolia'), ('Petia'), ('Zina'), ('Sasha'), ('Dima'), ('Egor'), ('Polina'), ('Sveta'), ('Alladin');

alter table materials add column supplier_id int;
alter table materials add foreign key (supplier_id) references suppliers (id);
update materials set supplier_id = 3 where id = 3;
update materials set supplier_id = 4 where id = 4;
update materials set supplier_id = 5 where id = 5;
update materials set supplier_id = 6 where id = 6;
update materials set supplier_id = 7 where id = 7;
update materials set supplier_id = 8 where id = 8;
update materials set supplier_id = 9 where id = 9;
update materials set supplier_id = 10 where id = 10;
select * from materials m;

alter table employees add surname varchar (50);

alter table salary add currency varchar (7);
update salary set currency = 'USD' where id > 0;
