
## базовое сканирование


## apache-tomcat

![image](https://github.com/user-attachments/assets/f9f9831a-2c1f-40ca-a9e7-6958ab0a319f)

Эксплуатация уязвимостей не привела к результату, ищем креды

## aria2

![image](https://github.com/user-attachments/assets/e617ffd6-c65b-4241-b26b-910527669f0a)

## Path traversal in aria2

`curl --path-as-is http://10.10.56.113:8888/../../../../../../../../../../../../../../../../../../../../opt/tomcat/conf/tomcat-users.xml`

![image](https://github.com/user-attachments/assets/905f5e21-f679-4291-a7bb-d0563f5757d5)

manager-script означает, что мы можем деплоить приложения через API

Создаем war реверсшелл

![image](https://github.com/user-attachments/assets/e2b55643-4988-4427-ab9c-69f25a0d30a0)

Загружаем на сервер

![image](https://github.com/user-attachments/assets/c28ef0e2-1f8d-4bfe-95bc-341d64735b26)

Запускаем прослушиваение порта и переходим на страницу myapp

![image](https://github.com/user-attachments/assets/731b3d07-762c-4ad2-a712-a55e5dba8737)


Первый флаг находим в /opt/tomcat

![image](https://github.com/user-attachments/assets/5eef6d97-be6a-435a-9e04-d6f051426ca5)

## linpeas

![image](https://github.com/user-attachments/assets/e90d5f21-cef2-418e-a5e2-ab79cfc82a65)

