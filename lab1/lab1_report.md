University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab1  
Date of create: 26.09.2023  
Date of finished: 27.09.2023  

## Лабораторная работа 1 "Лабораторная работа №1 "Установка CHR и Ansible, настройка VPN""

## Описание

Данная работа предусматривает обучение развертыванию виртуальных машин (VM) и системы контроля конфигураций Ansible а также организации собственных VPN серверов.  

## Цель работы

Целью данной работы является развертывание виртуальной машины в облаке с установленной системой контроля конфигураций Ansible и установка CHR в VirtualBox. Настроить между машинами VPN.

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

<img width="850" alt="Screen Shot 2024-09-26 at 13 24 23" src="https://github.com/user-attachments/assets/c077d895-532b-47b8-b2e1-1d1f0baee03b">
<br></br>  

* Для установки VPN сервера Wireguard на Ubuntu выполним следующую команду ```apt install wireguard-tools```
<img width="571" alt="Screen Shot 2024-09-26 at 13 31 28" src="https://github.com/user-attachments/assets/8c7ef4e3-4978-437f-afb2-2fcaa9d30bbc">
<br></br>  

* Создадим пару publickey и privatekey ключей на сервере.
<img width="572" alt="Screen Shot 2024-09-26 at 13 39 22" src="https://github.com/user-attachments/assets/448f207f-89ca-42e4-b7d3-ec448c1d4185">
<br></br>  

* В дирекории ```/etc/wireguard/``` создадим файл ```wireguard.conf``` с конфигурацией для виртуального сетевого Адаптера. В секции ```[Interface]``` заданы параметры VPN сервера, расположенного на Ubuntu. В секции ```[Peer]``` ,соответственно, заданы параметры VPN клиента MikroTik CHR. Публичный ключ клиента был автоматически сгенерирован при создании виртуального адаптера Wireguard на роутере. 
<img width="576" alt="Screen Shot 2024-09-26 at 15 56 11" src="https://github.com/user-attachments/assets/0b370a59-08c6-44b0-aa6a-6c48a43cd17e">
<br></br>  

* Запустим службу wireguard, а также добавим этот процесс в автозагрузку при запуске ОС.
<img width="571" alt="Screen Shot 2024-09-26 at 15 54 23" src="https://github.com/user-attachments/assets/ac3eff30-e991-4b84-9cfe-5148b50fa66f">
<br></br>  

* На стороне клиента пропишем интерфейсу wireguard IP адрес и создадим Peer с параметрами VPN сервера.
<img width="700" alt="Screen Shot 2024-09-26 at 15 59 59" src="https://github.com/user-attachments/assets/01ddf5ff-34bd-4dcb-9982-6c828cbfebd0">

<img width="700" alt="Screen Shot 2024-09-26 at 16 11 13" src="https://github.com/user-attachments/assets/0ddf0ed9-1e53-4e84-9897-fc906e0d263e">
<br></br>  

## Ping
* Протестируем связь между VPN клиентом и VPN сервером.
<img width="512" alt="Screen Shot 2024-09-26 at 16 04 13" src="https://github.com/user-attachments/assets/19974e9a-99aa-46f7-813e-85c6e4f2b2e1">
<br></br>  
<img width="606" alt="Screen Shot 2024-09-26 at 16 03 56" src="https://github.com/user-attachments/assets/d97f8e6d-162d-4c6a-b9c2-f09910755e8a">

  
## Вывод
Таким образом, была развернута виртуальная машина в облаке, на машину была установлена система контроля конфигураций Ansible, также на домашнем пк была поднята виртуальная машина CHR в среде виртуализации VirtualBox. Между виртуальной машиной в облаке и виртуальной машиной CHR было создано VPN соединение.
 
