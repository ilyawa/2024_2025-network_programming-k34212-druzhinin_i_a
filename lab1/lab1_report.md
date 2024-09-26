University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab1  
Date of create: 26.09.2023  
Date of finished: 27.09.2023  

## Лабораторная работа 1 "Установка ContainerLab и развертывание тестовой сети связи"

## Описание

Данная работа предусматривает обучение развертыванию виртуальных машин (VM) и системы контроля конфигураций Ansible а также организации собственных VPN серверов.  

## Цель работы

Целью данной работы является развертывание виртуальной машины в облаке с установленной системой контроля конфигураций Ansible и установка CHR в VirtualBox.  

## Ход работы

* На хостинге Timeweb CLoud был арендован облачный сервер Ubuntu 20.4 с 1 CPU и 1 ГБ RAM.

 <img width="700" alt="Screen Shot 2024-09-26 at 11 56 57" src="https://github.com/user-attachments/assets/7e09e6af-fb06-4809-a6ed-9e2fdb28b0b8">
<br></br>  

* Доступ к серверу был получен по ssh с помощью команды ```ssh root@<ip сервера>```.

<img width="571" alt="Screen Shot 2024-09-26 at 12 02 19" src="https://github.com/user-attachments/assets/4c656290-6947-4cc3-9a71-3b77ddb8702c">
<br></br>  

* Далее на хост были установлены python, pip, ansible с помощью команд:
  ```
  sudo apt install python3-pip
  sudo pip3 install ansible
  ```
<img width="571" alt="Screen Shot 2024-09-26 at 12 11 58" src="https://github.com/user-attachments/assets/f3789961-1f8c-4443-9c0a-3ca36b9e982a">  
<br></br>  

* Следующим шагом стало разворачивание MikroTik CHR на виртуальной машине в VirtualBox на домашнем пк. 

<img width="565" alt="Screen Shot 2024-09-26 at 12 50 28" src="https://github.com/user-attachments/assets/f20b413e-f22e-4970-9638-09b82ec39d3e">
<br></br>  

* Дальнейшую настройку виртуального роутера можно осуществить с помощью веб-интерфейса - утилиты WebFig.
Создадим виртуальный адаптер Wireguard для VPN клиента.

<img width="1021" alt="Screen Shot 2024-09-26 at 13 24 23" src="https://github.com/user-attachments/assets/c077d895-532b-47b8-b2e1-1d1f0baee03b">
<br></br>  

## Вывод
Таким образом, была развернута виртуальная машина в облаке, на машину была установлена система контроля конфигураций Ansible, также на домашнем пк была поднята виртуальная машина CHR в среде виртуализации VirtualBox.
 
