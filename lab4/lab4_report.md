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

Поднимем вм из .ova файла, скачанного с веб сайта https://p4.org/p4_events/p4-developer-day-2/.  

<img width="400" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2007.35.54.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2007.36.13.png">  

С помощью команды ```make run``` поднимем виртуальную сеть mininet и убедимся, что пинги между устройствами не идут.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2008.16.08.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2008.23.49.png">  

С помощью информации с официального гитхаба P4 реализуем в файле basic.p4 базовую коммутацию пакетов.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2011.38.20.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2011.47.44.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2011.59.33.png">  

Пересоберем mininet и убедимся, что пинги между устройствами идут.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2012.20.50.png">   

Далее реализуем туннелирование, для этого изменим файл basic_tunneling.p4.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2013.16.13.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2013.17.59.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2013.59.39.png">

С помощью скриптов send.py и receive.py проверим отправку и получение пакетов.  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2014.46.23.png">  

Затем проверим работу туннелирования, как можно видеть, у отправленного пакета есть заголовок [My_Tunnel].  

<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2017.10.36.png">  
<img width="800" src="https://github.com/ilyawa/2024_2025-network_programming-k34212-druzhinin_i_a/blob/main/lab4/images/Screen%20Shot%202024-12-20%20at%2017.10.06.png">  

## Вывод
В ходе выполнения данной лабораторной работы был изучен синтаксис языка программирования P4 и выполнены 2 обучающих задания от Open network foundation для ознакомления на практике с P4.
 
