University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
Year: 2023/2024
Group: K4110c
Author: Gusev Dmitriy Alexeevich
Lab: Lab3
Date of create: 18.12.2023
Date of finished: 21.12.2023  

Включаем Ingress 
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/2d0c4620-9886-43f7-aef1-270a1bb7e8c8)  
Генерируем TLS сертификат:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/4f2eb875-e35b-4e08-8016-44ae58ae2821)  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/2e983840-517b-47d1-8325-334bef0e8300)  

Также появились файлы cert и key. Они появились в этой папке, т.к. у меня только таким образом "завёлся" openssl
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/d904fcf6-ab42-4a30-b82c-58ace605fedd)  
Создадим секрет:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/53ef0828-49aa-46ce-adb0-c6cacddc9dae)
Отредактируем манифест написанный в рамках лабораторной работы 2, создадим ingress.  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/72f03efa-fd31-4b80-ba4d-85c9d7df1120)  
Свяжем ip адрес с доменным именем в файле hosts.  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/69e58a59-8a0a-4031-bd68-91e7c42dbea7)  
Проверим работает ли сайт:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/85075003-ba09-41d0-812f-ab7b25905757)  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/398c348d-1d86-4ef8-865f-7ca3ab975a70)  
Схема:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/649252c2-6e3c-406b-bbd2-7d2d0a7534d4)  
