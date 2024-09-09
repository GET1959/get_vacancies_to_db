# get_vacancies_to_db
database course project
## Курсовой проект по теме "Работа с базами данных"
Перед запуском программы в корне проекта надо создать файл database.ini со следующим содержимым:

[postgresql]

host= <указать хост>

user= <указать пользователя>

password= <указать пароль>

port= <указать порт>

Проект состоит из четырех модулей:
* create_db
* db_manager
* interactive
* main

Перечень компаний-работодателей хранится в файле companies.json 

### Модуль create_db

В модуле create_db

Формируется список ID компаний для запроса по API

Отправляется запрос на сайт hh.ru

На основании полученного ответа создается база данных, содержащая 2 таблицы: employers и vacancies

В базу данных не поступают вакансии, не имеющие информации по зарплате.

Для возможности сравнения зарплат вводится величина salary_norm,
позволяющая сопоставлять величину зарплаты независмо от валюты

### Модуль db_manager

В модуле db_manager представлен класс DBManager для работы с базой данных.

Метод get_companies_and_vacancies_count позволяет получить список компаний-работодателей с количеством актуальных вакансий по каждой.

Метод get_all_vacancies предоставляет краткую информацию по всем вакансиям, в том числе ссылку, по которой можно узнать подробности.

Метод get_avg_salary показывает среднюю зарплату по всем найденным вакансиям.

Метод get_vacancies_with_higher_salary предоставляет информацию по вакансиям с зарплатой выше средней.

Метод get_vacancies_with_keyword предоставляет информацию по вакансиям, содержащим ключевое слово, введенное пользователем.

### Модуль interactive

Модуль interactive отвечает за диалог с пользователем.

На основании пользовательского ввода в консоль выводится соответствующая информация из базы данных.

### Модуль main

Модуль main запускает программу.