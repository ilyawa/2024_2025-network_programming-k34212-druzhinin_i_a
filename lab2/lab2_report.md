University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab1  
Date of create: 13.11.2023  
Date of finished: 13.11.2023  

## Лабораторная работа №2 "Развертывание дополнительного CHR, первый сценарий Ansible"

## Описание

В данной лабораторной работе вы на практике ознакомитесь с системой управления конфигурацией Ansible, использующаяся для автоматизации настройки и развертывания программного обеспечения. 

## Цель работы

С помощью Ansible настроить несколько сетевых устройств и собрать информацию о них. Правильно собрать файл Inventory.

## Задачи

1. Установить второй CHR на своем ПК.
2. Организовать второй OVPN Client на втором CHR.
3. Используя Ansible, настроить сразу на 2-х CHR:
  * логин/пароль;
  * NTP Client;
  * OSPF с указанием Router ID;
4. Собрать данные по OSPF топологии и полный конфиг устройства.

## Ход работы

Создадим вторую виртуальную машину по аналогии с первой лабораторной работой.

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/user-attachments/assets/0d66ff02-2002-4f6d-8eea-3621c730640d">

Настроим второй Wireguard клиент.
<img width="800" alt="Screen Shot 2024-10-16 at 13 37 14" src="https://github.com/user-attachments/assets/c0b2ef2c-8ddd-4234-b68a-85fdf091770a">


## Вывод
В ходе выполнения данной лабораторной работы на пк был установлен второй CHR в виртуальной машине, на нем был настроен второй VPN клиент, с использованием Ansible была произведена найтройка сразу 2-х CHR, а именно: были настроены логин/пароль, NTP клиент, OSPF, также была собрана информация об OSPF топологии и полный конфиг устройства.
 
