# Test Backend Project

Прослойка между фронтом и ТММ

## Локальная разработка

### Испольуем docker-compose

1) Нужно поднять окружение
2) Прогнать миграции (через команды в php контейнере)

Поднять проект:
```bash
# Cобрать образы
docker-compose build

# Поднять контейнеры
docker-compose up -d
```

Убить проект:
```bash
# выключить контейнеры
docker-compose down

# выключить контейнеры и убить вольюмы
docker-compose down -v

```

#### Команды в php контейнере

Чтобы выполнить команду в php контейнере, пишем `docker exec -it project_php <команда>`

Примеры:
```bash
# Прогнать миграции
docker exec -it project_php php artisan migrate


# Установить зависимости composer
docker exec -it project_php composer install
```

#### Настройка XDEBUG
Open project settings in phpstorm: `Preferences | Languages & Frameworks | PHP | Servers`
1) Create the new one with server name `php`, host `localhost:8090` and add mapping for project-root folder (your local path => '/var/www')
