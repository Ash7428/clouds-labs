# Лабораторная №2
## Задание
* Написать “плохой” Dockerfile, в котором есть не менее трех “bad practices” по написанию докерфайлов.
* Написать “хороший” Dockerfile, в котором эти плохие практики исправлены.

1. Первым шагом я установила докер с помощью команд:
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


<img width="1092" height="909" alt="image" src="https://github.com/user-attachments/assets/6c2786f7-a4d7-48c1-916c-c49ca596e59c" />


<img width="855" height="73" alt="image" src="https://github.com/user-attachments/assets/28760e37-d78f-42b7-a9e2-043bb0576d3c" />
