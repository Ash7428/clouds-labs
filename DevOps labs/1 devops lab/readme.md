# Лабораторная №1
## Задание
Настроить nginx по заданному тз:
* Должен работать по https c сертификатом
* Настроить принудительное перенаправление HTTP-запросов (порт 80) на HTTPS (порт 443) для обеспечения безопасного соединения.
* Использовать alias для создания псевдонимов путей к файлам или каталогам на сервере.
* Настроить виртуальные хосты для обслуживания нескольких доменных имен на одном сервере.

## nginx installation on ubuntu wsl 
<img width="967" height="846" alt="image" src="https://github.com/user-attachments/assets/7f53626c-70a0-4b73-a0fd-b94ec9c8de70" />
active and running
<img width="963" height="873" alt="image" src="https://github.com/user-attachments/assets/cfaaf3c1-a0c4-4308-8cd6-69d42f3dee31" />

not a fake not a fake, есть свой веб сервер ураа
<img width="789" height="524" alt="image" src="https://github.com/user-attachments/assets/c9f863cf-9831-4334-9cfc-58c1ea7ef6fc" />

## создание сайтов
Создаю локальные сайты
```
ashra@LAPTOP-CONT63IE:~$ sudo mkdir -p /var/www/project1.local/html                          ashra@LAPTOP-CONT63IE:~$ sudo mkdir -p /var/www/project2.local/html
```

<img width="950" height="162" alt="image" src="https://github.com/user-attachments/assets/1622cebd-09c5-4a30-b013-76626d83d794" />

Редактирую файл с хостами, присваиваю для проеджектов один и тот же адрем, чтобы они обслуживались на одном сервере 
<img width="920" height="512" alt="image" src="https://github.com/user-attachments/assets/f0ed9395-a23f-434d-9b77-af9acfc317a0" />

## Настройка конфигов 
Это нужно, чтобы определить имя сервера для каждого проекта, через какой порт сервер будет слушать запросы и куда перенаправлять 
server 1
<img width="926" height="702" alt="image" src="https://github.com/user-attachments/assets/97ffa37f-d3ff-41f6-85da-54dde87ccaae" />


sites availeble
<img width="1256" height="118" alt="image" src="https://github.com/user-attachments/assets/50214efa-cca9-4067-baab-f45d9f235bc1" />


саздала самоподписные сертификаты
<img width="1920" height="436" alt="image" src="https://github.com/user-attachments/assets/e9c54645-7ecf-4a5d-94b6-f46d32ed083e" />

## Запуск сайтов 
перезапускаю систему
<img width="776" height="127" alt="image" src="https://github.com/user-attachments/assets/41097c5f-ca55-4af6-a02d-fa4fd3c61531" />
господи лишь бы не фейк. октрывается урааа
<img width="957" height="675" alt="image" src="https://github.com/user-attachments/assets/9d2f6263-157a-41ed-8e69-83212baf46c6" />
<img width="948" height="750" alt="image" src="https://github.com/user-attachments/assets/87bb3dd5-69b0-47b4-b9b6-9a9542ca4807" />

## alias
после первоначальной настройки сайта добавим к нему папку media чтобы картинка была смешная. В начале если перейти по адресу смешной картинки не было.. и никакой не было. ЧТо естественно, потому что в корневой папке указана иная дериктория (/var/www/project1.local/html/), и поиск папки media происходит внутри нее, хотя на самом деле она хранится в другом месте. Используем alias, чтобы создать псевдоним к папке media и получить доступ к мему:
<img width="1916" height="918" alt="image" src="https://github.com/user-attachments/assets/0723e512-4740-4aec-b1c5-fded799cb2d5" />

# Вывод
так как я работала в wsl, а запускала сайты в браузере винды, то мне пришлось также прописывать домены в виндоуском файле. а могла бы с виртуал бокс делать и не мучится с локальными зависимостями....
