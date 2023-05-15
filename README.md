<h1>Проект тестирование docker-compose</h1><br>
Описание проекта:<br>
Данный проект предназначен для тренировки работы с технологией docker, для контейнеризации django проекта api_yamdb.<br>
<br>
Как запустить проект:<br>
Клонировать репозиторий и перейти в него в командной строке:<br>
<br>
git@github.com:PavelSavvinov/infra_sp2.git<br>
cd api_yamdb<br>
Cоздать и активировать виртуальное окружение:<br>
python -m venv venv<br>
source venv/bin/activate
<br>
Установить зависимости из файла requirements.txt:<br>
pip install -r requirements.txt<br>
<br>
Выполнить миграции:<br>
python manage.py migrate<br>
<br>
Запустить проект:<br>
python manage.py runserver<br>

[![Django-app workflow](https://github.com/PavelSavvinov/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)](https://github.com/PavelSavvinov/yamdb_final/actions/workflows/yamdb_workflow.yml)

