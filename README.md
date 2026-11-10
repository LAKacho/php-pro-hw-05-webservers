# ДЗ 5. PHP WebServers: проверка скобок и балансировка

HTTP-приложение принимает POST-параметр `string`, проверяет корректность круглых скобок и возвращает `200 OK` либо `400 Bad Request`. Перед двумя независимыми связками Nginx + PHP-FPM работает Nginx load balancer. PHP-сессии общие и хранятся в Redis.

## Запуск

```bash
docker compose up --build -d
curl -i -X POST http://localhost:18005/ --data-urlencode 'string=(()()())'
curl -i -X POST http://localhost:18005/ --data-urlencode 'string=)('
```

Автономный тест алгоритма:

```bash
php tests/BracketValidatorTest.php
```

Остановка: `docker compose down`.
