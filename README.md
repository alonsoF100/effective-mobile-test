# Effective Mobile Test
Веб приложение: Go + Nginx

## Архитектура
1. Запрос->http://localhost:80
2. Nginx принимает запрос на порту 80
3. Nginx проксирует запрос на backend:8080
4. Nginx добавляет заголовки:
  - Host
  - X-Real-IP
  - X-Forwarded-For
  - X-Forwarded-Proto
5. Backend (Go) обрабатывает запрос на /
6. Backend отвечает: Hello from Effective Mobile! (status:200ok)
7. Nginx возвращает ответ

## Запуск
```
docker-compose up -d
```

## Проверка работы
```
curl http://localhost
```
Вывод:
```
Hello from Effective Mobile!
```

## Проверка заголовков
```
curl -I http://localhost
```
Вывод:
```
HTTP/1.1 200 OK
Server: nginx/1.29.5
Date: Wed, 04 Mar 2026 15:02:36 GMT
Content-Type: text/plain; charset=utf-8
Content-Length: 28
Connection: keep-alive
```