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
Помимо контейнера с Netbox поднимем СУБД PostgreSQL и нереляционную СУБД Redis для корректной работы Netbox.  

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2017.05.24.png">  

При сборке контейнера получаем ошибку со следующим стек-трейсом.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-08%20at%2006.56.13.png">  

В интернете было найдено решение данной проблемы - в файл docker-compose был добавлен секретный ключ.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2021.07.26.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-01%20at%2021.07.18.png">  

Netbox был поднят и схема сети приобрела следующий вид.  

<img width="500" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-08%20at%2011.00.39.png">  

Заполняем в Netbox информацию о сетевых устройствах: тип, вендор, модель, имя, интерфейсы и их IP-адреса.  

<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2015.18.48.png">
<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2017.09.59.png">
<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2017.10.42.png">
<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2017.12.13.png">
<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2018.38.46.png">
<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2018.38.59.png">

Список устройств в Netbox.  

<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-07%20at%2005.41.04.png">

Создадим токен для того, чтобы работать с Netbox с помощью API.  

<img width="700" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2018.39.54.png">

Установим модуль netbox.netbox для Ansible.  

<img width="600" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2018.57.51.png">

Далее создадим новый файл инвентаря Ansible.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2018.59.16.png">

Выведем список устройств с помощью команды ```ansible-inventory --list```  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2019.01.47.png">

Получим все данные об устройствах из Netbox в виде yaml файла (файл прикреплен в папке работы).  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2019.01.30.png">

Напишем сценарий Ansible, который изменит имена и IP-адреса устройств CHR-1 и CHR-2, используя информацию из Netbox.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2019.01.30.png">

Затем напишем сценарий, который внесет серийный номер устройств CHR в Netbox.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab3/images/Screen%20Shot%202024-12-05%20at%2019.01.30.png">

## Вывод
В ходе выполнения данной лабораторной работы с помощью Ansible и Netbox была собрана вся информация о сетевых устройствах, информация была сохранена в отдельном файле, также на основе информации из Netbox и с помощью Ansible были изменены имена и IP адреса устройств, был написан сценарий, позволяющий собрать серийный номер устройства и вносящий серийный номер в Netbox.
 
