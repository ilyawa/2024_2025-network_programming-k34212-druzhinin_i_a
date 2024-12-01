University: [ITMO University](https://itmo.ru/ru/)  
Faculty: [FICT](https://fict.itmo.ru)  
Course: [Network programming](https://github.com/itmo-ict-faculty/network-programming)  
Year: 2024/2025  
Group: K34212  
Author: Druzhinin Ilya Antonovich  
Lab: Lab 3  
Date of create: 1.12.2023  
Date of finished: 6.12.2023  

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

Создадим вторую виртуальную машину по аналогии с первой лабораторной работой.

<img width="600" alt="Screen Shot 2024-10-16 at 13 13 09" src="https://github.com/user-attachments/assets/0d66ff02-2002-4f6d-8eea-3621c730640d">  
<br></br>

Настроим второй Wireguard клиент.  

<img width="800" alt="Screen Shot 2024-10-16 at 13 37 14" src="https://github.com/user-attachments/assets/c0b2ef2c-8ddd-4234-b68a-85fdf091770a">
<br></br>

Добавим peer для VPN подключения на удаленной машине в облаке.

<img width="571" alt="Screen Shot 2024-10-16 at 14 40 31" src="https://github.com/user-attachments/assets/0a3f38f1-c869-4a6b-ae1a-ed3935a9f7fe">
<br></br>

Получим следующую топологию сети.

<img width="473" alt="Screen Shot 2024-11-13 at 16 53 39" src="https://github.com/user-attachments/assets/b718fd2f-fc5d-4235-af2e-3c5fb9777915">
<br></br>

Результаты пингов.

<img width="593" alt="Screen Shot 2024-11-12 at 12 57 13" src="https://github.com/user-attachments/assets/d27e4e87-e0b0-4213-9302-397968040f03">
<img width="587" alt="Screen Shot 2024-11-12 at 12 56 46" src="https://github.com/user-attachments/assets/1ed67e47-d82f-4b89-947d-0df8b078b0c3">
<img width="574" alt="Screen Shot 2024-11-12 at 12 56 17" src="https://github.com/user-attachments/assets/7c8cca4a-75ac-4976-a36a-fe53e51c474e">
<br></br>

Напишем файл inventory.

<img width="598" alt="Screen Shot 2024-11-12 at 22 14 52" src="https://github.com/user-attachments/assets/7eb0a9b4-0330-4d64-8faf-387cad5781fd">
<br></br>

Выведем конфигурацию ansible inventory.

<img width="603" alt="Screen Shot 2024-11-12 at 22 15 30" src="https://github.com/user-attachments/assets/4ae4e038-ba26-4d08-ab4d-6de896c9eee4">
<br></br>

Проверим пинг в в ansible.

<img width="603" alt="Screen Shot 2024-11-12 at 22 16 05" src="https://github.com/user-attachments/assets/c1abf7a4-0927-47de-9eb7-4d56ca0b8299">
<br></br>

Напишем playbook.

<img width="681" alt="Screen Shot 2024-11-12 at 22 52 45" src="https://github.com/user-attachments/assets/3117db42-f10a-404e-b606-4e4db34a50d1">
<br></br>

Запустим playbook и увидим, что на машине не установлен модуль paramiko.

<img width="685" alt="Screen Shot 2024-11-12 at 22 56 21" src="https://github.com/user-attachments/assets/8a7098f3-4451-4f75-b804-965b02cb64bf">
<br></br>

Установим paramiko.

<img width="683" alt="Screen Shot 2024-11-12 at 22 58 35" src="https://github.com/user-attachments/assets/2ec593c9-d9a0-4224-a9a8-da3659582d27">
<br></br>

Попробуем опять запустить playbook и получим ошибку - машина в облаке не может определить аутентичность хостов CHR.

<img width="684" alt="Screen Shot 2024-11-12 at 23 02 24" src="https://github.com/user-attachments/assets/64eaee0a-c1a4-4b7a-914a-b994592fa65a">
<br></br>

Зайдем с виртуальной машины в облаке на CHR машины по ssh, тогда машина в облаке автоматически запомнит ssh ключи chr-ов.

<img width="684" alt="Screen Shot 2024-11-12 at 23 06 24" src="https://github.com/user-attachments/assets/be25e9fa-295b-4f8c-9474-a32b6c97b4d7">
<br></br>

Аутентификация по логину/парлю все равно не работает. После поиска в гугле было найдено решение - использовать pylibssh вместо paramiko.

<img width="681" alt="Screen Shot 2024-11-12 at 23 07 33" src="https://github.com/user-attachments/assets/9d123f19-4065-4bdf-a091-58cefe26bcba">
<br></br>

Как можно видеть, playbook отработал. Конфигурации были выведены в консоль.

<img width="733" alt="Screen Shot 2024-11-13 at 10 18 49" src="https://github.com/user-attachments/assets/69b68f4c-3bbf-49d2-93ef-98c19e6d4a4b">
<img width="732" alt="Screen Shot 2024-11-13 at 10 19 43" src="https://github.com/user-attachments/assets/8f50cde0-88b8-43b5-ab63-7fe2b4e6a402">
<br></br>

Далее приведем скриншоты с информациях об инстансах/соседях ospf на самих роутерах, как подтверждение правильной настройки ospf.

<img width="844" alt="Screen Shot 2024-11-13 at 10 21 32" src="https://github.com/user-attachments/assets/1556962e-fde5-4328-a687-89c951cff039">
<img width="887" alt="Screen Shot 2024-11-13 at 10 29 10" src="https://github.com/user-attachments/assets/ec264f2f-8f7c-411e-a8a7-ee160577ad71">
<img width="888" alt="Screen Shot 2024-11-13 at 10 29 19" src="https://github.com/user-attachments/assets/d50361fc-ed61-4e09-aeb4-a3310acfc0ac">
<br></br>

## Вывод
В ходе выполнения данной лабораторной работы с помощью Ansible и Netbox была собрана вся информация о сетевых устройствах, информация была сохранена в отдельном файле.
 
