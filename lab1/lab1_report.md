University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
Year: 2023/2024
Group: K4110c
Author: Gusev Dmitriy Alexeevich
Lab: Lab1
Date of create: 27.11.2023
Date of finished: 30.11.2023

Лабораторная работа №1 "Установка Docker и Minikube, мой первый манифест."  
Описание:  
Это первая лабораторная работа в которой вы сможете протестировать Docker, установить Minikube и развернуть свой первый "под".  
Цель работы:  
Ознакомиться с инструментами Minikube и Docker, развернуть свой первый "под".
Ход работы:  
После установки вам необходимо развернуть minikube cluster
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/76445565-7b75-4966-a17b-27ed81a10a7d)  
Загружаем образ HashiCorp Vault  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/49283f7f-42a6-4f43-bd1f-4ec327a7c035)  
Создадим pod с параметрами указанными в myfirst.yaml:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/10bcdf1b-0346-4753-b957-13b51edcec4c)  
Pod стал готовым:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/34740029-a789-434f-8ebb-d86bdb7e359e)  
Создадим сервис для доступа к этому контейнеру:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/e1b33e65-926c-41cd-9483-c553587102fd)  
Переадресуем локальный порт в открытый порт пода:
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/df88943b-a0b2-4be3-8ff8-dfe56ce496be)
Как итог по адресу localhost:8200  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/b1ec86b9-fab1-486a-bef4-26f9771fb23b)  
Рут токен находится в логах пода:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/2137e1a4-0022-429a-9880-4030f10fd46a)  
Зайдем:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/3ea9f116-962b-46f7-a51e-c05ad7616ad1)  
Схема:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/3d54f21a-2324-4f50-8035-bbaebbe5c49f)
 Что сейчас произошло и что сделали команды указанные ранее?  
Был запущен под, содержащий контейнер с vault. При запуске пода был указан порт 8200, также был создан сервис для доступа к поду. Также был добавлен проброс порта локальной машины к открытым портам пода.







