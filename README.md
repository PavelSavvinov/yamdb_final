# Проект тестирование полноценного deploy django docker пакета через GitHub Actions

## Автор:

Саввинов Павел <br>
GitHub страница: https://github.com/PavelSavvinov <br>
Проект развренут по адресу: http://84.201.162.122/ <br>
Автризация: http://84.201.162.122/admin <br>
Документация: http://84.201.162.122/redoc/ <br>

## Описание проекта:

Данный проект предназначен для тренировки работы с технологией docker, docker-compose, GitHub Actions, Nginx, Django, Postgres, Telegram bot для запуска, и деплоя шаблона сайта api_yamdb через удаленный ОС linux сервер на Yandex Cloud.

## Как запустить проект:
### Внутри локального компьютера:

Клонировать репозиторий через командную строку:<br>
`git@github.com:PavelSavvinov/yamdb_final.git` <br>
Cоздать и активировать виртуальное окружение: <br>
`python -m venv venv` <br>
`source venv/bin/activate`<br>
Установить зависимости из файла requirements.txt:<br>
`pip install -r requirements.txt`<br>
Выполнить миграции:<br>
`python manage.py migrate`<br>
Запустить проект:<br>
`python manage.py runserver`<br>

### Внутри локального компьютера через docker:

** ВАЖНО!!! Должен быть установлен docker ** <br>

Клонировать репозиторий через командную строку:<br>
`git@github.com:PavelSavvinov/yamdb_final.git` <br>
Запустить консоль внутри папки проекта, после перейти в папку infra: <br>
`cd infra` <br>
Узнать версию docker: <br>
`docker --version` <br>
Запуск docker-compose, разворачиваем сайт: <br>
`docker-compose up -d --build` <br>
Выполнить миграции: <br>
`docker-compose exec web python manage.py migrate` <br>
Создать superuser: <br>
`docker-compose exec web python manage.py createsuperuser` <br>
Собрать все static: <br>
`docker-compose exec web python manage.py collectstatic --no-input ` <br>
Выполнить следующие команды:<br>
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
Для загрузки готовых данных в БД:<br>
`docker-compose exec web python manage.py loaddata fixtures.json`<br>
Остановка docker-compose: <br>
`docker-compose down -v ` <br>

### Полноценный деплой проекта через GitHub Actions: <br>

** ВАЖНО!!! Должен быть установлен docker и аккаунт в docker hub ** <br>

Запустить консоль внутри папки проекта, после перейти в папку \api_yamdb: <br>
`cd api_yamdb` <br>
Локально создать образ с нужным названием и тегом: <br>
`docker build -t dreamcrusader/yamdb_final . ` <br>
Авторизоваться через консоль: <br>
`docker login` <br>
Загрузить образ на DockerHub: <br>
`docker push dreamcrusader/yamdb_final` <br>
Сделать push проекта на GitHub: <br>
```
git add .
git commit -m "ver 1.0"
git push
```
После деплоя проекта на основной сервер, заходим на сервер через ssh соединение, и выполнить следующие команды:<br>
```
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
Для загрузки готовых данных в БД:<br>
`docker-compose exec web python manage.py loaddata fixtures.json`<br>

[![Django-app workflow](https://github.com/PavelSavvinov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/PavelSavvinov/yamdb_final/actions/workflows/yamdb_workflow.yml)

