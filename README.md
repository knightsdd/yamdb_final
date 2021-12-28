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

### Как запустить проект:

Клонировать репозиторий и перейти в каталог infra:

```
git clone git@github.com:knightsdd/infra_sp2.git
```

```
cd infra
```

Cоздать окружение

```
nano .env
```
И прописать в нем переменные в соответствии с шаблоном
```
DB_ENGINE=django.db.backends.postgresql
DB_NAME=postgres
POSTGRES_USER=postgres
POSTGRES_PASSWORD=your_secur_password
DB_HOST=db
DB_PORT=5432
SECRET_KEY=yOuR_sEcReT_Key_vErY-Long!#%
DEBUG=
DOMAIN_NAME=your_domain
EMAIL_SENDER=your@ema.il
```

Проверьте конфигурацию nginx в диреткории `nginx` файл `default.conf`

Запустить сборку контейнеров при помощи команды

```
docker-compose up
```

После успешного запуска выполнить миграции

```
sudo docker-compose exec web python manage.py migrate
```

Создать суперпользователя

```
sudo docker-compose exec web python manage.py createsuperuser
```

Собрать статичные файлы

```
sudo docker-compose exec web python manage.py collectstatic --no-input
```

Зайти в панель администратора по адресу http://localhost/admin/

Описание эндпоинтов можно найти в файле redoc http://localhost/redoc/

### Приятнонго использовани!

