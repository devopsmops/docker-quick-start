# Базовые команды Docker

## Образы

Показать все образы
```
docker images
```

Сборка образа из Dockerfile в текущей директории
```
docker build -t mopsDevops:v1 .
```

Изменение имени образа или тэга
```
docker tag mopsDevops:v1 mopsDevops:v2
```

Сохранение образа в файл
```
docker save mopsDevops -o mopsDevops.tar 
```

Загрузка образа из файла
```
docker load -i mopsDevops.tar 
```

Отобразить слои (команды в образе)
```
docker history mopsDevops:v2 --no-trunc
```

Удалить образ
```
docker rmi mopsDevops:v1
```

## Контейнеры
Вывести список всех запущенных контейнеров
```
docker ps
```

Вывести список имен всех запущенных контейнеров
```
docker ps -q
```

Вывести список всех контейнеры на сервере (в том числе остановленных)
```
docker ps –a
```

Запустить контейнер(создаст контейнер, если его еще нет)
```
docker run mopsDevops:v1
```

> Параметры для команды run:
>```
>-d    Запуск контейнера в фоне (daemon)
>-it   Интерактивный режим (запуск shell)
>-rm   Удаление контейнера после остановки
>-p    Проксирование локального порта в порт контейнера
>-e    Добавить переменные окружения
>-v    Подключение volumes в контейнер
>```

Выполнить команду в контейнере
```
docker exec mopDevops:v1 bash
```

```
docker exec mopsDevops:v1 /etc/config.conf
```

## Registry
> Если не указать название Registry, поиск и загрузка образов будет выполняться из общедоступных образов Docker Hub

Скачать образ
```
docker pull nginx:1.19
```

Загрузить образ в Registry
```
docker push my-repo/nginx:1.19
```

## Clean Up
Удаление всех образов, неиспользуемых контейнерами
```
docker image prune -a
```

Удаление всех остановленных контейнеров
```
docker container prune -f
```

Остановка запущенного контейнера
```
docker stop container_name
```
```
docker kill container_name
```

Удаление всех контейнеров
```
docker rm -f $(docker ps -qa)
```

Удаление неименованных образов
```
docker rmi $(docker images -q -f dangling=true)
```