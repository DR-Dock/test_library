# test_library
### 1. База данных (ER модель).
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D1%81%D1%85%D0%B5%D0%BC%D0%B0.png" alt="">

Authors(авторы) – содержит id, имя, фамилию, отчество.

Students(читатели) - содержит id, имя, фамилию, отчество.

Books(книги) - содержит id, название, id автора(передается из таблицы авторов),год публикации, издательство.

Rentals(прокат книг) – содержит id проката, id книги(передается из таблицы с книгами),id читателя(передается из таблицы читателей), дата выдачи, дата возврата если уже вернули.

SQl код базы находится в файле "library_db.txt", так же там есть тестовые данные. Для написания базы данных использовался MySQL.
### 2. Самый популярный автор за год.
Запрос находится в файле "популярный автор за год.txt". Для демонстрации данного запроса реализована форма в приложении на странице с авторами.
Алгоритм запоса:
* В отдельное представление R1, взять id книг всех прокатов за интересующий год.
* В представление R2, объединить R1 с таблицей книг, взять id авторов из неё и имена книг.
* Сгруппировать по  id авторов и посчитать частотность каждого автора функцией COUNT, положить всё в представление R3.
* В представление R4 положить id автора, частотность которого максимальна.
* Вывести автора, который соответствует полученному id.
### 3. Самый злостный читатель.	
Самый злостный читатель – читатель, у которого самое большое время проката какой либо книги, если есть несколько читателей с одинаковым временем, то суммируется время всех прокатов по каждому из таких читателей, далее вычисляется самое максимальное полученное значение. Данный алгоритм реализован в файле index.js(с 147 по 184 строки кода). Так же демонстрация данного алгоритма есть в приложении на странице с читателями. Время вычислялось как разница между датой начала проката и датой возврата, если книгу ещё не вернули, то разница вычисляется между началом проката и текущей датой. Всё время переведено в часы.
### 4. Скриншоты приложения.
* Страница с книгами, имеется поиск по книгам, таблица с основной информацией по каждой книге, кнопка выдачи в прокат или возврат:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B50.PNG" alt="">

* Таблица всех прокатов, отображена вся основная информация: кто брал, какую книгу, когда взял, когда вернул, если не вернул, то кнопка возврата:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B51.PNG" alt="">

* Страница со всеми читателями библиотеки, сверху отображено ФИО злостного студента:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B52.PNG" alt="">

* Страница с авторами, сверху имеется форма, в которую можно вписать год, как результат получить ФИО самого популярного автора за этот год:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B53.PNG" alt="">

* Страница с читателем и всеми его прокатами:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B54.PNG" alt="">

* Страница с книгой и всеми прокатами по ней:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B55.PNG" alt="">

* Страница с книгами одного конкретного издательства:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B56.PNG" alt="">

* Страница с подтверждением о возврате книги:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B57.PNG" alt="">

* Страница с формой выдачи книги:
<img src="https://github.com/DR-Dock/test_library/blob/main/images/%D0%BF%D1%80%D0%B8%D0%BB%D0%BE%D0%B6%D0%B5%D0%BD%D0%B8%D0%B58.PNG" alt="">

### 5. Инструкция развертывания:
* Установить node.js
* Склонировать репозиторий
* Выполнить команду "npm install" в папке с проектом 
* Установить MySQL server, открыть консоль MySQL, создать базу данных library_db, войти в неё и скопировать всё содержимое из файла library_db.txt. Для изменения параметров коннекта к базе, смотреть файл index.js  261 – 268 строки кода.
* Запустить приложение (node index.js)
