### Работа приложения:

1. Создаётся класс сервера
1. Сервер запускается
1. Сервер прослушивает сокет _localhost:14905_
2. Сервер начинает слушать клиента с таймаутом в 5 секунд.
3. Полученный ответ парситься
    * Сперва считывается первая строка, из которой достаётся имя метода, версия, а также url строка
    * Парситься url строка в адрес и словарь параметров
    * Читаются заголовки до строки окончания загоолвков
    * При наличии заголовка "Content-Length" читается указанное кол-во байтов как тело и парсится как и параметры url строки - в словарь
4. Данные сохраняются в класс Зароса
5. Запрос прочитывается и, в зависимости от метода, выполняются алгоритмы описаные ниже
6. Ответ отправляется пользователю

В случае ошибки при выполнении сервер всегда вернёт ответ 400

#### Обработка POST запроса:

1. Из тела прочитываются параметры "discipline" и "mark"
2. В файл "grades.txt" добавляется строка в виде строки html-таблицы из 2-ух столбцов
3. Создаётся класс Ответа (204, 'Created')

#### Обработка GET запроса:

1. Из url прочитывается параметр "discipline"
2. Открывается шаблонный html-файл
3. Открывается файл "grades.txt" и с него считываются все строки, содержание "discipline"
4. В шаблонном html-файле заменяется плейсхолдер на отфильтрованное содержимое "grades.txt"
5. В ответе создаются заголовки "Content-Length" и "Host"
6. В ответ добавляется тело в виде отредактированного шаблона
7. Создаётся класс Ответа (200, "ОК", headers, body)