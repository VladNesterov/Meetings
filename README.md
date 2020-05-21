## Задание 1.
Цель задания – необходимо реализовать сервис для постановки встреч.
Детали реализации:
•	Писать код можно на любом языке программирования
•	В качестве хранилища данных можно использовать любую технологию
•	При перезапуске сервера добавленные данные должны сохраняться
•	Визуализация данных в виде пользовательского интерфейса (веб-приложение, мобильное приложение) не требуется – достаточно только обозначенного ниже API, доступного из командной строки. Однако простор фантазии не ограничиваем, покуда соблюдаются основные требования
•	Предоставить инструкцию по запуску приложения. 
•	Финальную версию нужно выложить на github.com
Реализовать методы
Поставить встречу
Отменить встречу
Добавить участников
Удалить участника
Вывести список встреч с участниками

Методы обрабатывают HTTP POST запросы c телом, содержащим все необходимые параметры в JSON.

Задача может быть решена со следующими усложнениями
Проверка валидности эл. почты
Проверка занято/свободно время участников (выдавать предупреждение)
Отправить приглашение на встречу всем участникам в виде емэйл
За 15 минут до встречи отправить напоминание


## Запуск
При помощи программы postman  создаем HTTP POST запросы описанные ниже.
Предварительно нужно добавить участников и встречи в базу данных при помощи запросов.

## Методы API
PUT /meeting/add
    ?meeting=meeting08
    &date=January 1, 1970, 00:00:00
Добавляет встречу в базу данных. Имена митингов уникальны.
Нельзя создать два митинга с одинаковым именем


PUT /show
Показывает все встречи с их участниками 


PUT /member/add/to/meeting
    ?meeting=meeting02
    &members=vova
    &members=vika
Добавляет людей к встрече. 
Если встречи не существует и вы попытаетесь добавить ее, выведется сообщение об ошибке.


PUT /member/delete
    ?meeting=meeting02
    &name=vlad31231
Удаляет человека со встречи. 
При попытке удалить человека не включенного в собрание появится сообщение, 
что нельзя удалить такого человека, так как он не состоит в данном собрании.


PUT /member/add/to/database
    ?name=vlad
    &email=vlad@mail.ru
Все имена уникальны.
Добавляет в базу данных человека, проверят его валидность. 
Если валидация не проходит, выдается сообщение об ошибке. 
По способу добавления в базу данных  можно сказать, что в базе будут только валидные пользователи.


PUT /member/add/to/meeting
    ?meeting=meeting02
    &members=vova
    &members=vika
Добавляет людей к встрече. 
Если встречи не существует и вы попытаетесь добавить в нее человека, выведется сообщение об ошибке.

