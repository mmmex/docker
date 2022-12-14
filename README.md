### Docker otus homework

```
1. Создайте свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx)

2. Определите разницу между контейнером и образом. Вывод опишите в домашнем задании.

3. Ответьте на вопрос: Можно ли в контейнере собрать ядро?

4. Собранный образ необходимо запушить в docker hub и дать ссылку на ваш репозиторий.

5. Создайте кастомные образы nginx и php, объедините их в docker-compose.

6. После запуска nginx должен показывать php info.

7. Все собранные образы должны быть в docker hub
```

### 1. Создайте свой кастомный образ nginx на базе alpine. После запуска nginx должен отдавать кастомную страницу (достаточно изменить дефолтную страницу nginx)

* Запуск контейнера: `docker run -d -p 8080:80 --name nginx krdr/nginx`

* Проверка: `curl localhost:8080`

### 2. Определите разницу между контейнером и образом. Вывод опишите в домашнем задании.

Разница в том, что образ является основой для контейнера и не может быть изменен (read only), в отличие от контейнера который является экземпляром образа где производится запуск приложения, создавая при этом новый слой доступный для записи (copy-on-write).

### 3. Ответьте на вопрос: Можно ли в контейнере собрать ядро?

Сборка ядра в контейнере возможна, и даже вообще любая сборка проекта в контейнере из исходного кода удобный вариант для последующей доставки. [Ссылка на проект](https://github.com/a13xp0p0v/kernel-build-containers)

### 4. Собранный образ необходимо запушить в docker hub и дать ссылку на ваш репозиторий.

[Dockerfile образа nginx](docker/nginx/Dockerfile)

[Ссылка на репозиторий docker hub](https://hub.docker.com/r/krdr/nginx)

### 5. Создайте кастомные образы nginx и php, объедините их в docker-compose.

[Dockerfile образа php](docker/php-fpm/Dockerfile)

[Dockerfile образа nginx](docker/nginx/Dockerfile)

[Файл docker-compose.yml](docker-compose.yml)

### 6. После запуска nginx должен показывать php info.

* Клонируем проект: `git clone https://github.com/mmmex/docker.git`

* Переходим в папку: `cd docker`

* Запускаем сборку: `docker-compose up -d`

* Проверяем: `curl localhost:8080/index.php`

### 7. Все собранные образы должны быть в docker hub

[Образ php-fpm на docker hub](https://hub.docker.com/r/krdr/php-fpm)

[Образ nginx на docker hub](https://hub.docker.com/r/krdr/nginx)