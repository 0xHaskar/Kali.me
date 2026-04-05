<p align="center">
  <img width="600" height="200" src="https://upload.wikimedia.org/wikipedia/commons/4/4e/Docker_%28container_engine%29_logo.svg">
</p>

18 Weird and Wonderful ways I use Docker
Канал: NetworkChuck  
---> https://www.youtube.com/watch?v=RUqGlWr5LBA  
---> https://www.docker.com/products/docker-desktop/  

---

Docker Для Начинающих за 1 Час | Docker с Нуля  
Канал: Vlad Mishustin  
---> https://m.youtube.com/watch?v=lr1rYnUubpQ  

---

Основы Docker. Большой практический выпуск. Канал: Артем Матяшов  
--->  https://youtube.com/watch?v=QF4ZF857m44 


----


```bash

sudo docker images --- показать все докер images

sudo docker rmi название_докера -- удаления образа докера

sudo docker container rm айди_контейрена или название_контейнера --- удалить контейнер

sudo docker ps -- показать активные контейрены

sudo docker ps -a --- показать все контейнеры

sudo docker pull название_докера --- скачать докер

sudo docker system prune -a --- удалить все не активные контейнеры

sudo docker exec -it айди_докера bash --- попасть в консоль bash контейнера docker

sudo docker build -t название путь_файла --- сбилдить докер контейнер

Например: sudo docker build -t project .

sudo docker run --name новое_название старое_название --- запуск нового контейнера с другим названием на основе старого

sudo docker stop айди-контейнера или название --- остановить контейнер

sudo docker rm название --- удалить контейнер

```

---

Docker — тот самый инструмент, который упрощает жизнь этичным хакерам.   
Раньше для стендирования определенной версии конкретного приложения необходимо было станцевать с бубном.   
Сейчас это можно сделать одной командой. Пользуйтесь!  
---> https://dockercheatsheet.com/
