SQL HomeWork 2. Joins

Подключится к
Host: 159.69.151.133
Port: 5056
DB: qa_db_2
User: user_22_x
Pass: 123
 
 1. Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.
	select employees.id, employees.employee_name, employees_salary.monthly_salary from employees, employees_salary where employees_salary.employee_id = employees.id order by id;
	
 2. Вывести всех работников у которых ЗП меньше 2000.
	select employees.id, employees.employee_name, employees_salary.monthly_salary from employees, employees_salary where employees_salary.employee_id = employees.id and monthly_salary < 2000 order by monthly_salary;
	
 3. Вывести все зарплатные позиции, но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
	select * from employees e right join employees_salary es on e.id = es.employee_id where e.id is null;
	
 4. Вывести все зарплатные позиции  меньше 2000 но работник по ним не назначен. (ЗП есть, но не понятно кто её получает.)
	select * from employees e right join employees_salary es on e.id = es.employee_id where e.id is null and monthly_salary < 2000 order by monthly_salary;
	
 5. Найти всех работников кому не начислена ЗП.
	select * from employees e left join employees_salary es on e.id = es.employee_id where es.id is null;
	
 6. Вывести всех работников с названиями их должности.
	select e.id, e.employee_name, r.role_name from employees e left join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id;
	
 7. Вывести имена и должность только Java разработчиков.
	select e.employee_name, r.role_name from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%Java %';
	
 8. Вывести имена и должность только Python разработчиков.
	select e.employee_name, r.role_name from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%Python %';
 
 9. Вывести имена и должность всех QA инженеров.
	select e.employee_name, r.role_name from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%QA %';
	
 10. Вывести имена и должность ручных QA инженеров.
	 select e.employee_name, r.role_name from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%Manual %';
	 
 11. Вывести имена и должность автоматизаторов QA
	 select e.employee_name, r.role_name from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%Automation %';
	 
 12. Вывести имена и зарплаты Junior специалистов
	 select e.employee_name, r.role_name, es.monthly_salary from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id join employees_salary es on e.id = es.employee_id where r.role_name like '%Junior %';
	 
 13. Вывести имена и зарплаты Middle специалистов
	 select e.employee_name, r.role_name, es.monthly_salary from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id join employees_salary es on e.id = es.employee_id where r.role_name like '%Middle %';
	 
 14. Вывести имена и зарплаты Senior специалистов
	 select e.employee_name, r.role_name, es.monthly_salary from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id join employees_salary es on e.id = es.employee_id where r.role_name like '%Senior %';
	 
 15. Вывести зарплаты Java разработчиков
	 select distinct r.role_name, es.monthly_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Java %';
	 
 16. Вывести зарплаты Python разработчиков
	 select distinct r.role_name, es.monthly_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Python %';
	 
 17. Вывести имена и зарплаты Junior Python разработчиков
	 select distinct r.role_name, es.monthly_salary from employees_salary es right join (roles_employees re right join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Junior Python %';
	 
 18. Вывести имена и зарплаты Middle JS разработчиков
	 select distinct r.role_name, es.monthly_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Middle JavaScript %';
	 
 19. Вывести имена и зарплаты Senior Java разработчиков
	 select e.employee_name, r.role_name, es.monthly_salary from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id join employees_salary es on e.id = es.employee_id where r.role_name like '%Senior Java %';
	 
 20. Вывести зарплаты Junior QA инженеров
	 select distinct r.role_name, es.monthly_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Junior%QA %';
	 
 21. Вывести среднюю зарплату всех Junior специалистов
	 select avg(es.monthly_salary) as Averge_Junior_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%Junior%';
	 
 22. Вывести сумму зарплат JS разработчиков
	 select sum(es.monthly_salary) as SUM_JS_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%JavaScript%';
	 
 23. Вывести минимальную ЗП QA инженеров
	 select min(es.monthly_salary) as Min_QA_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%QA%';
	 
 24. Вывести максимальную ЗП QA инженеров
	 select max(es.monthly_salary) as Max_QA_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%QA%';
	 
 25. Вывести количество QA инженеров
	 select count(e.id) as QA_Engineers_quantity from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%QA%';
	 
 26. Вывести количество Middle специалистов.
	 select count(e.id) as Middle_specialists_quantity from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%Middle%';
	 
 27. Вывести количество разработчиков
	 select count(e.id) as Developers_quantity from employees e join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id where r.role_name like '%dev%';
	 
 28. Вывести фонд (сумму) зарплаты разработчиков.
	 select sum(es.monthly_salary) as dev_salary from employees_salary es join (roles_employees re join roles r on re.role_id = r.id) on es.employee_id = re.employee_id where r.role_name like '%dev%';
	 
 29. Вывести имена, должности и ЗП всех специалистов по возрастанию
	 select e.employee_name, r.role_name, es.monthly_salary from employees e left join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id left join employees_salary es on e.id = es.employee_id order by monthly_salary;
	 
 30. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП от 1700 до 2300
	 select e.employee_name, r.role_name, es.monthly_salary from employees e left join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id left join employees_salary es on e.id = es.employee_id where monthly_salary between 1700 and 2300 order by monthly_salary;
	 
 31. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП меньше 2300
	 select e.employee_name, r.role_name, es.monthly_salary from employees e left join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id left join employees_salary es on e.id = es.employee_id where monthly_salary < 2300 order by monthly_salary;
	 
 32. Вывести имена, должности и ЗП всех специалистов по возрастанию у специалистов у которых ЗП равна 1100, 1500, 2000
	 select e.employee_name, r.role_name, es.monthly_salary from employees e left join (roles_employees re join roles r on re.role_id = r.id) on e.id = re.employee_id left join employees_salary es on e.id = es.employee_id where monthly_salary in('1100','1500','2000') order by monthly_salary;
	 
 
