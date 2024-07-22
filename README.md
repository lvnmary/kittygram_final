# Kittygram

[![Main Kittygram workflow](https://github.com/lvnmary/kittygram_final/actions/workflows/main.yml/badge.svg)](https://github.com/lvnmary/kittygram_final/actions/workflows/main.yml)

## Описание:
Kittygram — это социальная сеть, созданная специально для любителей кошек. Пользователи могут регистрироваться, загружать фотографии своих питомцев, указывая их имя, цвет, дату рождения и достижения.

## Стек технологий:
- Python
- Django
- API
- Nginx
- Djoser
- Gunicorn 

## Ознакомиться с проектом можно по ссылке:
https://kittygram-lvnmary.ddns.net

## Как запустить проект:
Клонировать репозиторий и перейти в него в командной строке

```
git clone git@github.com:lvnmary/kittygram_final.git
```

Перейти в корневую директорию
```
cd kittygram_final
```

Создать файл .evn для хранения ключей

Запустить docker-compose.production

```
docker compose -f docker-compose.production.yml up
```

Выполнить миграции, сбор статики

```
docker compose -f docker-compose.production.yml exec backend python manage.py migrate
docker compose -f docker-compose.production.yml exec backend python manage.py collectstatic
docker compose -f docker-compose.production.yml exec backend cp -r /app/collected_static/. /static/static/

```

Создать суперпользователя

```
docker compose -f docker-compose.production.yml exec backend python manage.py createsuperuser
```

### Проект Kittygram включает две версии для развёртывания: обыкновенную (для разработки) и прод-версию (для использования на производственных серверах).
Для разработки:
- файл - docker-compose.yml;
- сборка образов локально для backend, frontend и gateway;
- тома: pg_data, static, media;
- локальная отладка и внесение изменений.

Продакшн-версия:
- файл - docker-compose.production.yml;
- готовые образы из Docker Hub: lvnmary/kittygram_backend, lvnmary/kittygram_frontend, lvnmary/kittygram_gateway;
- тома: pg_data_production, static_volume, media;
- стабильная и протестированная версия.

## Автор:
Левина Мария 
https://github.com/lvnmary