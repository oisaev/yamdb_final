
![Изображение](https://yastatic.net/q/logoaas/v2/Яндекс.svg?circle=white&color=fff&first=black) ![Изображение](https://yastatic.net/q/logoaas/v2/Практикум.svg?color=fff)

# YaMDb

![workflow](https://github.com/oisaev/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### Адрес:
http://158.160.27.5/

### Описание
Учебный проект Яндекс Практикум.

YaMDb собирает **отзывы** пользователей на **произведения**. Сами произведения в YaMDb не хранятся, здесь нельзя посмотреть фильм или послушать музыку.

Полное описание проекта доступно в репозитории:
https://github.com/AlexBatanov/api_yamdb

### Технологии
- Python 3.9
- Django 3.2
- DRF
- JWT

### Развертывание

Проект автоматически развертывается на Yandex Cloud при помощи workflow, написанном для GitHub Actions при пуше в ветку Master. При развертывании используется:
- Платформа контейнеризации Docker совместно с инструментом развертывания мультиконтейнерных приложений Docker Compose
- Веб сервер Nginx
- СУБД PostgreSQL

Для ручного развертывания необходимо выполнить следующие действия:

Перед развертыванием проекта необходимо в директории **infra** создать и заполнить **.env** файл по следующему шаблону:
```
SECRET_KEY='p&l%385148kslhtyn^##a1)ilz@4zqj=rq&agdol^##zgl9(vs' # секретный ключ Django (установите свой)
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql
DB_NAME=postgres # имя базы данных
POSTGRES_USER=postgres # логин для подключения к базе данных
POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)
DB_HOST=db # название сервиса (контейнера)
DB_PORT=5432 # порт для подключения к БД
```
Далее, в той же директории **infra** выполнить команду для сборки контейнеров и их запуска:
```
docker-compose up -d --build
```
Выполнить миграции:
```
docker-compose exec web python manage.py migrate
```
Собрать статику:
```
docker-compose exec web python manage.py collectstatic --no-input
```
Скопировать файл с данными **fixtures.json** внутрь контейнера командой:
```
docker cp fixtures.json infra-web-1:/app/
```
И загрузить данные в базу:
```
docker-compose exec web python manage.py loaddata fixtures.json
```
Это создаст суперпользователя с **login:** admin **password:** admin и добавит тестовые данные в таблицы


### Авторы YaMDb

Студенты Яндекс Практикум программы Python-разработчик плюс, когорта 19+
- Александр Батанов в роли тимлида
- Константин Гашев в роли разработчика
- Олег Исаев в роли разработчика