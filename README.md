# Контекст

Допустим мы хотим разработать сервис-мобильное приложение, где пользователь сможет трекать свои прочитанные книги и учавствовать таким образом в мировом челендже.
Мобильный клиент умеет парсить название книги по фото (верифицируя таким образом, что книга реальная), и получать по стороннему апи ее категорию, 
соответственно на сервере необходимо принимать эту информацию в виде: название, категория, дата старта чтения, дата завершения.

Длинна челенджа год, его суть - прочитать больше всего уникальных книг, но уникальная книга или нет участник узнает в конце.

# Нагрузка

Заранее известно, что в челендже возьмет участие 50 миллионов человек, так же известно что в среднем участник челенджа читает три книги в месяц, 
соответственно к окончанию челенджа в базе ожидается 1.8-2 миллиарда записей, на основе которых потом нужен будет репорт в виде юзер-количество прочитанных уникальных книг. 

Нагрузка планируется плавная, без взрывных скачков. 

Сервер должен отдать ответ на роут приема данных максимально быстро. 

# Задача

1. Юзер может зарегистрироваться по роуту `/user/register`, передавая свою почту и пароль, наша задача его зарегистрировать и вернуть токен для доступа к апи, токен действителен 30. 
Предусмотреть возможность ручной инвалидации раньше. Нельзя зарегистрироваться под уже существующим имейлом, так же имейл и пароль являются обязательными, подтверджения имейла не нужно.

2. Юзер может залогиниться по роуту `/user/login` с той-же парой логин-пароль, получая новый токен, старый удаляется

3. Юзер может используя полученный токен отправить данные (название, категория, дата старта чтения, дата завершения) на роут `/book/send`, получив 201 код если сохранить удалось, 401 если токен невалидный, 500 - при ошибках сервера.
Уникальнось книги определяется сочетанием полей название-категория, если книга не уникальная - она должна все-равно сохранятся для выборок других видов статистики.

# Решение

По технологиям выбор за кандидатом, единственное условие - возможность быстро развернуть решение для теста, инструкции по развертке стоит включить в README.md

Код должен использовать возможности ООП и по возможности соответствовать SOLID и лучшим практикам выбраного фреймворка.

По возможности - покрытие ключевой логики/ее части тестами.

# Критерии оценки

1. Общий сетап (выбранные технологии, подходы)
2. Соответствие решения условиям задачи
3. Качество кода
4. Оптимальность решения под установленый характер нагрузки

Улучшения от себя - приветствуются, ориентировочное время на решение задачи - 3-5 часов



