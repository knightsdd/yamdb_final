![deploy](https://github.com/knightsdd/yamdb_final/actions/workflows/yamdb_workflow.yml/badge.svg)

### YamDb
YamDb - api для сервиса поиска и оценки различных произвдений (книг, фильмов, музыки). 
Функционал предусматривает:
- регистрация на сервисе;
- создание произедений с их описанием;
- указание категории и жанра произведения;
- создание отзыва с оценкой (от 1 до 10) о произведении (не более одного отзыва на каждое произведение для пользователя);
- создание комментариев к отзыву;
- получение информации о произведени, его отзывах и рейтинге;
- просмотр комментариев к отзыву.

### Инструкция по запуску локально
Сервис запускается в docker контейнерах через docker compose.
1. В диреткории infra создайте файл .env по шаблону:
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
DB_HOST=db
DB_PORT=5432
```
2. Поднимите контейрены командой:
```docker compose up```
3. Выполните миграции командой
```docker compose exec -T web python manage.py migrate```
4. Соберите статику
```docker-compose exec -T web python manage.py collectstatic --no-input```
5. Создайте суперпользователя командой
```docker compose exec web python manage.py createsuperuser```
6. Добавить данные для тестов командой
```docker-compose exec -T web python manage.py load_category --path './static/data/category.csv'```
Список доступных команд для загрузки тестовых данных:
- ```load_category```
- ```load_comment```
- ```load_genre```
- ```load_review```
- ```load_title```
- ```load_user```

Сервис доступен по локальному адресу http://127.0.0.1
Админ панель http://127.0.0.1/admin
Спецификация api http://127.0.0.1/redoc

### Инструкция для запуска на сервере
Запуск на сервере осуществляется через workflow GitAction
