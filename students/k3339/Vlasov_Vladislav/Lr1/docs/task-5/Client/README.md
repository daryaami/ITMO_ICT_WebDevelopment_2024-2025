### Работа приложения:

1. Клиент подключается по сокету _localhost:14905_
2. Клиент отправляет шаблонное сообщение POST или GET

### Структура сообщений:

#### POST
Содержит заголовки "Host" и "Content-Length"
Содержит тело в виде url параметров

#### GET
Содержит заголовок "Host"
Содержит параметры в url 