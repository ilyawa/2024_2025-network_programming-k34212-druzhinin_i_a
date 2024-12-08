University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab 3  
Date of create: 1.12.2023  
Date of finished: 8.12.2023  

## Лабораторная работа №3 "Развертывание Netbox, сеть связи как источник правды в системе технического учета Netbox"

## Описание

В данной лабораторной работе вы ознакомитесь с интеграцией Ansible и Netbox и изучите методы сбора информации с помощью данной интеграции.

## Цель работы

С помощью Ansible и Netbox собрать всю возможную информацию об устройствах и сохранить их в отдельном файле.

## Задачи

1. Поднять Netbox на дополнительной VM.
2. Заполнить всю возможную информацию о ваших CHR в Netbox.
3. Используя Ansible и роли для Netbox в тестовом режиме сохранить все данные из Netbox в отдельный файл, результат приложить в отчёт.
4. Написать сценарий, при котором на основе данных из Netbox можно настроить 2 CHR, изменить имя устройства, добавить IP адрес на устройство.
5. Написать сценарий, позволяющий собрать серийный номер устройства и вносящий серийный номер в Netbox.

## Ход работы

Netbox - это открытое веб-приложение, разработанное для управления и документирования компьютерных сетей.   
Поднимем Netbox в докере с помощью готового образа netbox:latest. Файл docker-compose будет выглядеть следующим образом.
Помимо контейнера с Netbox поднимем СУБД PostgreSQL и нереляционную СУБД Redis для правильной работы Netbox.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  
<br></br>
При сборке контейнера получаем ошибку со следующим стек трейсом.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  
<br></br>

В интернете было найдено решение данной проблемы, файл docker-compose был изменен.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  
<br></br>

Netbox был поднят и схема сети приобрела следующий вид.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  
<br></br>

Заполняем в Netbox информацию о сетевых устройствах: тип, вендор, модель, имя, интерфейсы и их IP-адреса.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  
<br></br>

## Вывод
В ходе выполнения данной лабораторной работы с помощью Ansible и Netbox была собрана вся информация о сетевых устройствах, информация была сохранена в отдельном файле, также на основе информации из Netbox и с помощью Ansible были изменены имена и IP адреса устройств, был написан сценарий, позволяющий собрать серийный номер устройства и вносящий серийный номер в Netbox.
 
