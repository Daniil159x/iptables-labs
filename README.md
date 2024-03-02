# Iptables Labs

Репозиторий с тасками и песочницей для экспериментов с iptables.

## Запуск playground

**Под WSL не работает. Нужно настоящее ядро.**

Playground состоит из двух контейнеров: router и client.  
Поднимаем так:  
```bash
cd playground
docker compose up --build -d
```
Если не убирать -d, команда зависнет.

Теперь заходим на роутер и играем:
```bash
docker compose exec router bash
iptables -I INPUT -p tcp --dport 1337 -j DROP
```

Чтобы обращаться к роутеру в той же сети, то это делать надо из контейнера клиента:
```bash
docker compose exec client bash

# must connection refused
curl http://router:8080

# must connection timeout
curl http://router:1337
```