# Kittygram — социальная сеть для обмена фотографиями любимых питомцев. Это полностью рабочий проект, который состоит из бэкенд-приложения на Django и фронтенд-приложения на React. 
## Использованные технологии: 
- Python 3.9
- Django 3.2.3
- Django REST framework 3.12.4
- JavaScript
 
## Основные возможности 
-   Простая регистрация учетной записи пользователя. 
-   Загрузка фотографий котов с добавлением кратких описаний. 
-   Просмотр фотографий и описаний котов других пользователей. 

## Запуск проекта из образов с Docker hub

Для запуска необходимо на создать папку проекта, например `kittygram` и перейти в нее:

```bash
mkdir kittygram
cd kittygram
```

В папку проекта скачиваем файл `docker-compose.production.yml` и запускаем его:

```bash
sudo docker compose -f docker-compose.production.yml up
```

Произойдет скачивание образов, создание и включение контейнеров, создание томов и сети.

## Запуск проекта из исходников GitHub

Клонируем себе репозиторий: 

```bash 
git clone git@github.com:MihailovAlexander/kittygram.git
```

Выполняем запуск:

```bash
sudo docker compose -f docker-compose.yml up
```

## После запуска: Миграции, сбор статистики

После запуска необходимо выполнить сбор статистики и миграции бэкенда. Статистика фронтенда собирается во время запуска контейнера, после чего он останавливается. 

```bash
sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py migrate

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend python manage.py collectstatic

sudo docker compose -f [имя-файла-docker-compose.yml] exec backend cp -r /app/collected_static/. /static/static/
```
