Принимает HTTP-запросы на порт 80

Перенаправляет их на бекенд (Flask)

Генерирует приветственное сообщение

Хранит и увеличивает счётчик посещений

Гарантирует, что счётчик не сбросится при перезапуске


# Создать сеть
docker network create myapp-network

# Запустить Redis
docker run -d --name redis --network myapp-network redis:alpine

# Запустить Flask
docker run -d --name app --network myapp-network -e REDIS_HOST=redis yourname-flask

# Запустить Nginx
docker run -d --name web -p 80:80 --network myapp-network yourname-nginx


Ссылки на образы: https://hub.docker.com/repository/docker/nastie/myapp-app/general
https://hub.docker.com/repository/docker/nastie/myapp-web/general
