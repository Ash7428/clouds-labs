# Лабораторная №2
## Задание
* Написать “плохой” Dockerfile, в котором есть не менее трех “bad practices” по написанию докерфайлов.
* Написать “хороший” Dockerfile, в котором эти плохие практики исправлены.
### 1. Первым шагом я установила докер с помощью команд:
```
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo
"deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu
$(. /etc/os-release && echo "$VERSION_CODENAME") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt update
sudo apt install docker-ce
```
установка докера
<img width="958" height="986" alt="image" src="https://github.com/user-attachments/assets/f1b7a1ad-f496-427a-a9a9-7812e5617dcc" />

<img width="960" height="986" alt="image" src="https://github.com/user-attachments/assets/5e772670-2caf-4943-b366-fd9d9c33ee6f" />

<img width="960" height="646" alt="image" src="https://github.com/user-attachments/assets/72ec96f2-3d47-4510-8709-723deea1d996" />


<img width="932" height="614" alt="image" src="https://github.com/user-attachments/assets/73501cb1-f0d0-48ff-9f9a-e7970dfb4eeb" />

### 2. Далее написала докерфайлы.
Использовала команды
`sudo docker build -t <название контейнера> .`
`sudo docker run <название контейнера>`

<img width="1092" height="909" alt="image" src="https://github.com/user-attachments/assets/6c2786f7-a4d7-48c1-916c-c49ca596e59c" />

работают!

<img width="855" height="73" alt="image" src="https://github.com/user-attachments/assets/28760e37-d78f-42b7-a9e2-043bb0576d3c" />

### 3. Bad Dockerfile
<img width="958" height="426" alt="image" src="https://github.com/user-attachments/assets/eaf7e3e9-2ecc-40a7-8856-908e230891a4" />

1) **FROM ubuntu:latest**
Нет указания конкретной версии. Последняя версия может измениться, и написанный докерфайл может перестать работать в более новых версиях.

2) ADD https://github.com/Ash7428/clouds-labs/edit/main/DevOps%20labs/2%20DevOps%20lab/>
использование прямой ссылки не рекомендуется, так как такие файлы нельзя удалить, и они увеличивают размер образа. 
3) **COPY . ./home/ubuntu/lab2-docker-practice**
При такой директории в контейнер копируется больше данных, чем нужно, а также это делается не очень удобно, указывая путь на папку в инструкции COPY.

   
### 4. Good Dockerfile
<img width="967" height="447" alt="image" src="https://github.com/user-attachments/assets/30788e24-5642-4343-b9b6-d276d660322c" />


1) **FROM ubuntu:18.04**
Указание конкретной версии. Независимо от внешних источников  Docker всегда будет запускаться одинаково. Более рання версия весит меньше, соответсвенно экономия места)

2) Сохранив файл локально, и только потом копируя его на докер из директории, я уберегаю себя от проблем с нерабочей ссылкой которые могут возникнуть в дальнейшем. 
3) Изначально выбрана рабочая дериктория. Скачивается меньше файлов, что экономит место. Плюс во время работы не нужно будет каждый раз указывать полный путь к файлам, достаточно указать пусть с начала выюранной директории, что удобно

### Плохие практики
1. Не чистить контейнеры и образы после сборки:
Отсутствие очистки контейнеров и образов после сборки приводит к накоплению мусора в системе. Остановленные контейнеры и неиспользуемые образы занимают дисковое пространство, что со временем может вызвать нехватку места. Кроме того, в остановленных контейнерах могут оставаться чувствительные данные, создавая угрозу безопасности.
2. Запускать контейнеры с админскими правами:
Запуск контейнеров с правами администратора повышает риски безопасности. Если контейнер работает от имени root и будет скомпрометирован, злоумышленник может получить доступ к хост-системе. Для защиты данных и предотвращения утечек следует использовать непривилегированных пользователей внутри контейнеров.

