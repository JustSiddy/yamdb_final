# Yamdb_Final
Проект Yamdb создан для сбора отзывов пользователей на разные произведения.
Произведения разделены на категории (пример: "Фильма", "Музыка", "Кино")
Каждое произведение разделено на жанры (пример: "Массовое кино", "Рэп", "Сказка")
Только администратор может создавать новые жанры.

![Django-app workflow](https://github.com/justsiddy/yamdb_final/actions/workflows/yamdb_workflow.yaml/badge.svg)

## Настрока и запуск сервера в контейнере:
1) Клонировать репозиторий:
``` 
git clone https://github.com/JustSiddy/yamdb_final.git
```
2) Переидти в папку:
``` 
cd infra
```
3) Создать файл .env и заполнить ее переменными окружения, для стабильной работы приложения. 
Пример содержимого файла:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
4) Развернуть контейнер:
``` 
docker-compose up -d --build
```
5) Сделать миграции, создать суперпользователя, собрать статику:cd
``` 
docker-compose exec web python manage.py migrate
docker-compose exec web python manage.py createsuperuser
docker-compose exec web python manage.py collectstatic --no-input
```
6) Загрузить базу данных из копии:
``` 
docker-compose exec web python manage.py loaddata ../infra/fixtures.json 
```

## Документация Redoc:
Запустите проект локально и переидите на страницу http://158.160.23.137/redoc/

## Стек:
```
Python 3.7
Django
Docker
PostgresSQL
Nginx
Gunicorn
```

## Автор
- [Расули Саид](https://github.com/JustSiddy)
