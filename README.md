![Main Taski workflow](https://github.com/Stepan22042004/kittygram_final/actions/workflows/main.yml/badge.svg)
#  Как работать с репозиторием финального задания

## Что нужно сделать

Настроить запуск проекта Kittygram в контейнерах и CI/CD с помощью GitHub Actions

## Как проверить работу с помощью автотестов

В корне репозитория создайте файл tests.yml со следующим содержимым:
```yaml
repo_owner: ваш_логин_на_гитхабе
kittygram_domain: полная ссылка (https://доменное_имя) на ваш проект Kittygram
taski_domain: полная ссылка (https://доменное_имя) на ваш проект Taski
dockerhub_username: ваш_логин_на_докерхабе
```

Скопируйте содержимое файла `.github/workflows/main.yml` в файл `kittygram_workflow.yml` в корневой директории проекта.

Для локального запуска тестов создайте виртуальное окружение, установите в него зависимости из backend/requirements.txt и запустите в корневой директории проекта `pytest`.

## Чек-лист для проверки перед отправкой задания

- Проект Taski доступен по доменному имени, указанному в `tests.yml`.
- Проект Kittygram доступен по доменному имени, указанному в `tests.yml`.
- Пуш в ветку main запускает тестирование и деплой Kittygram, а после успешного деплоя вам приходит сообщение в телеграм.
- В корне проекта есть файл `kittygram_workflow.yml`.
### Как заполнить env:

```
POSTGRES_DB=kittygram
POSTGRES_USER=kittygram_user
POSTGRES_PASSWORD=kittygram_password
DB_NAME=kittygram
SECRET_KEY=django-insecure-cg6*%6d51ef8f#4!r3*$vmxm4)abgjw8mo!4y-q*uq1!4$-89$django-insecure-cg6*%6d51ef8f#4!r3*$vmxm4)abgjw8mo!4y8mo!4y-q*uq1!4$-89$
DEBUG=False
ALLOWED_HOSTS=127.0.0.1,localhost,kittyyandex.zapto.org,84.201.179.197
```


### Как запустить проект:

Запустите Docker Compose с этой конфигурацией на своём компьютере. Название файла конфигурации надо указать явным образом, ведь оно отличается от дефолтного. Имя файла указывается после ключа -f

```
docker compose -f docker-compose.production.yml up
```
Сразу же соберите статику:
```
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
```
```
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/.
```

Примените миграции:

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
```

### Стек использованных технологий
### Язык программирования и фреймворк:
  Python: основной язык программирования.
  Django: основной веб-фреймворк.
  Django REST Framework (DRF): расширение Django для создания RESTful веб-сервисов.
### База данных:
  SQLite: проще в настройке, хороша для начального этапа разработки и тестирования.
### Аутентификация и авторизация:
  Django Rest Framework Simple JWT: библиотека для работы с JWT в DRF.
### Документация API:
  ReDoc: генератор статической документации.
### Тестирование:
  Pytest: для написания тестов.
  pytest-django: для расширения Pytest функционалом для Django.
### Автоматизация развёртывания:
  Docker
### Информация об авторах
Герасимов Степан
