# Тестовое задание от Делимобиля

## UPD 2018-12-16

Использован Map для хранения автомобилей, отдельный класс Car для описания автомобиля и методов фильтрации и обновления.


## Текст задания

Есть [rest метод](https://api.delitime.ru/api/v1/cars?with=fuel,model) со списком машин и различными данными

Необходимо реализовать вебсокет на бэкэнде, который будет получать список машин с реста и отправлять их клиенту (список машин обновляется каждую секунду).
На фронте реализовать отрисовку автомобилей на яндекс карте маркерами (данные получать с вебсокета), с возможностью зума и скрола по карте. 

Желательно передавать по вебсокету только изменение данных (чтобы не гонять весь список) и только по тем машинам, которые попадают в видимую область.

## Запуск решения

Выполнить в консоле:

```bash
git clone https://github.com/r1000ru/delimobil-test.git
cd delimobil-test
npm install
npm start
```

И открыть в браузере ссылку [http://127.0.0.1:8080](http://127.0.0.1:8080)


### Структура проекта


Основным модулем проекта является файл `delimobil.js`. Он связывает между собой три модуля:
 - `api.js` - отвечающий за получение информации c другого бэкенда, в данном случае - только списка автомобилей
 - `filter.js` - отвечающий за фильтрацию информации из списка автомобилей
    - `car.js` - экземпляр авто с возможностью проверки местонахождения в координатах
 - `connection.js` - отвечающий вебсокет-сервер, использующий:
    - `connection.js` - отвечающий за конкретное подключение и дополнительную фильтрацию


> Так как в задании, помимо WebSocket API, необходимо отдавать еще и HTML-страницы, я использовал общий http-сервер, как для веб-сокетов, так и для отдачи статики (с помощью модуля `node-static`). В реальности, конечно, отдачу статики возлагать на NodeJS нет необходимости, с этим прекрасно справится Nginx.



