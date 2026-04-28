# Тестовое задание effective mobile

Веб-приложение с nginx reverse proxy и Python backend в Docker-контейнерах.

## Архитектура

```
Пользователь -> nginx:80 -> backend:8080 (Python)
```

- **nginx** - reverse proxy, принимает HTTP-запросы на порту 80 и перенаправляет на backend
- **backend** - Python HTTP-сервер (http.server), обрабатывает запросы внутри сети, не доступен снаружи

## Запуск

```bash
docker compose up -d --build
```

## Проверка

```bash
curl http://localhost
```

Ожидаемый ответ:

```
Hello from Effective Mobile!
```

## Остановка

```bash
docker compose down
```

## Troubleshooting

**Контейнеры не запускаются:**

```bash
docker compose logs backend
docker compose logs nginx
```

**Проверить статус:**

```bash
docker compose ps
docker inspect backend | grep Status
docker inspect nginx | grep Status
```

**Пересобрать с нуля:**

```bash
docker compose down --rmi local
docker compose up -d --build
```

## Используемые технологии

- Python 3.12 (http.server)
- nginx 1.27.5-alpine
- Docker + Docker Compose
