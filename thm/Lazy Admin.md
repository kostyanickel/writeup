## Базовое сканирование
![image](https://github.com/user-attachments/assets/8c21f1bb-7d79-451b-a7db-f117b4ec4e10)

## Проверим веб
![image](https://github.com/user-attachments/assets/2bc550c1-f97a-4959-8eed-a72a0fffd1a2)
## Поиск директорий привел к каталогу content
![image](https://github.com/user-attachments/assets/053149e7-99ca-4b72-8e3e-617448595780)

Это простая CMS SweetRice, на которую есть уязвимости
![image](https://github.com/user-attachments/assets/50ad120b-d9b2-4f6e-87a5-48320fbc9be0)
## Воспользуемся уязвимостью Backup Disclosure
![image](https://github.com/user-attachments/assets/bcc66026-4cee-44bc-84e8-697f9389c395)

Как говорится в PoC - нужно перейти на страницу /inc/mysql_backup
Так как директория SweetRice на хосте расположена в /content/ - переходим в /content/inc/mysql_backup

![image](https://github.com/user-attachments/assets/9b76e0f4-c186-4689-a8e7-8ca0c0132850)

Скачиваем файл и проверяем на наличие чувствительной информации. Находим креды manager:Password123
## Логинимся в CMS по адресу /content/as/
![image](https://github.com/user-attachments/assets/ac3e8cbe-631b-4036-8083-2b0975372ec5)

Переводим website status в Running
## Воспользуемся уязвимостью Arbitrary File Upload
Перепишем исходный код PoC'a, используя директорию /content/
Используя reverse shell от PentestMonkey на php, используем расширение php5 для обхода ограничения загрузки исполняемых файлов
### Запускаем PoC
![image](https://github.com/user-attachments/assets/8917da42-c94b-4ecc-ab06-af5e13210b29)
### прослушиваем порт, указанный в revers shell и переходим в директорию /content/attachment/
![image](https://github.com/user-attachments/assets/f31bdc1d-491f-4ee8-8c60-d16a2a2abfef)

Открываем rev.php5 и получаем обратный шелл
![image](https://github.com/user-attachments/assets/08b2da70-bf9a-4f4b-b8dd-4062d9253128)
## переходим в /home/itguy и забираем первый флаг
![image](https://github.com/user-attachments/assets/286e5739-b3d3-4873-98ce-703debbac49f)
## Priv-esc
### в домашней директории itguy видим файл backup.pl, а также использование файла /etc/copy.sh, к которому есть доступ для редактирования
![image](https://github.com/user-attachments/assets/91b42a04-2f56-435f-a600-190122b034ba)
### содержимое файла /etc/copy.sh
![image](https://github.com/user-attachments/assets/146802b6-1212-4319-b144-501990dfc9d7)

В файле содержится реверс шелл, поменяем содержимое файла на свой IP адрес
![image](https://github.com/user-attachments/assets/88b430ce-3c5e-4ad3-a05e-8f14c0fac990)
### Проверим вывод команды sudo -l
![image](https://github.com/user-attachments/assets/a3e96a45-f080-43db-b78e-aaf9b4c818e1)

Мы можем запускать backup.pl с sudo без пароля. Запустим прослушивание на 5554 порту и запустим backup.pl
### Получаем рутовый revers shell
![image](https://github.com/user-attachments/assets/e2f0f6f4-8c37-43db-841d-ba4989931b1b)

root flag
![image](https://github.com/user-attachments/assets/a11144bb-dfa3-4ee3-af37-7202288c2002)

