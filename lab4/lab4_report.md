University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab 4 
Date of create: 19.12.2023  
Date of finished: 20.12.2023  

## Лабораторная работа №4 "Базовая 'коммутация' и туннелирование используя язык программирования P4"

## Описание

В данной лабораторной работе вы познакомитесь на практике с языком программирования P4, разработанный компанией Barefoot (ныне Intel) для организации процесса обработки сетевого трафика на скорости чипа. Barefoot разработал несколько FPGA чипов для обработки трафика которые были встроенны в некоторые модели коммутаторов Arista и Brocade.

## Цель работы

Изучить синтаксис языка программирования P4 и выполнить 2 задания обучающих задания от Open network foundation для ознакомления на практике с P4.

## Задачи

Первой частью лабораторной работы является задание Implementing Basic Forwarding. В нем необходимо выполнить следующие задачи: - В виртуальной машине перейдите в папку проекта и выполните задания описанные в Implementing Basic Forwarding - Зафиксируете результаты и укажите результаты в вашем отчете.  

Второй частью лабораторной работы является задание Implementing Basic Tunneling В нем необходимо выполнить следующие задачи: - В виртуальной машине перейдите в папку проекта и выполните задания описанные в Implementing Basic Tunneling - Зафиксируете результаты и укажите результаты в вашем отчете.  

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

## Вывод
В ходе выполнения данной лабораторной работы был изучен синтаксис языка программирования P4 и выполнены 2 обучающих задания от Open network foundation для ознакомления на практике с P4.
 
