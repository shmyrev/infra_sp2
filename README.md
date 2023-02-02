
# api_yamdb

## Описание проекта:

Проект YaMDb собирает отзывы пользователей на произведения. Произведения делятся на категории: «Книги», «Фильмы», «Музыка».\
Учебный проект, предназначенный для отработки навыков и применение теории при командной
разработки API для веб приложения YaMDb, базируемых на фреймворке Django и модуле Django Rest Framework.\
Для обеспечения контороля прав доступа в проекте используется модуль JWT-токен.

## Установка и запуск проекта:

Клонировать репозиторий и перейти в него в командной строке:

```
https://github.com/shmyrev/infra_sp2.git
```

```
cd infra_sp2/
```

Переходим в папку с файлом docker-compose.yaml:

```
cd infra/
```

Создаем .env файл:

```
nano .env
```

Вносим эти данные:

```
DB_ENGINE=django.db.backends.postgresql # указываем, что работаем с postgresql

DB_NAME=postgres # имя базы данных

POSTGRES_USER=postgres # логин для подключения к базе данных

POSTGRES_PASSWORD=postgres # пароль для подключения к БД (установите свой)

DB_HOST=db # название сервиса (контейнера)

DB_PORT=5432 # порт для подключения к БД
```

Запускаем docker compose командой:

```
docker-compose up -d --build
```

Запускаем миграцмм:

```
docker-compose exec web python manage.py migrate
```

Создаем суперпользователя:

```
docker-compose exec web python manage.py createsuperuser
```

Создаем статику:

```
docker-compose exec web python manage.py collectstatic --no-input
```

Заполнение базы тестовыми данными:

```
docker-compose exec web python manage.py loaddata fixtures.json
```

Создаем дамп базы данных:

```
docker-compose exec web python manage.py dumpdata > fixtures.json
```

Останавть контейнер:

```
docker-compose down -v
```


## Примеры использования API:

```
Дитальное описание и примеры работы API проекта представлены в 
документации: http://localhost/redoc/ в формате ReDoc.
```

Получение произведений:

```
GET /api/v1/titles/
```

Добавление произведения (только администратор):

```
POST /api/v1/titles/
```

В параметрах передавать json

```
{
    "name": "Название произведения",
    "year": 1990,
    "description": "Описание произведения",
    "genre": [
    "fantasy"
    ],
    "category": "films"
}
```

## Используется:

```
Python 3.10 Django 3.2 Simple JWT
```

