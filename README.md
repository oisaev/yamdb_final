
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
Python 3.9
Django 3.2
DRF
JWT

### Развертывание

Проект автоматически развертывается на Yandex Cloud при помощи workflow, написанном для GitHub Actions при пуше в ветку Master. При развертывании используется:
- Платформа контейнеризации Docker совместно с инструментом развертывания мультиконтейнерных приложений Docker Compose
- Веб сервер Nginx
- СУБД PostgreSQL

### Авторы YaMDb

Студенты Яндекс Практикум программы Python-разработчик плюс, когорта 19+
- Александр Батанов в роли тимлида
- Константин Гашев в роли разработчика
- Олег Исаев в роли разработчика