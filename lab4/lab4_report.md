University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
Year: 2023/2024
Group: K4110c
Author: Gusev Dmitriy Alexeevich
Lab: Lab4
Date of create: 20.12.2023
Date of finished: 21.12.2023   


Запустим minikube с указанием calico в качестве плагина и 2 ноды.  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/8236d88d-32e5-4531-b841-40f42b10ec7c)  
Проверим результат работы calico, посмотрим количество нод.  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/c3473ed2-b462-4e82-a1b0-6215b9e25176)  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/c9df5eb9-b068-4eea-b20b-6f5cff9ba822)  
Добавим к нодам label по признаку стойки, посмотрим, что он добавился.  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/5db79036-a8a4-4b21-a0ae-85ad8686b413)  
Создадим манифест для назначения ip адресов подам:  
```
apiVersion: projectcalico.org/v3
kind: IPPool
metadata:
  name: rack-0-ippool
spec:
  cidr: 192.168.0.0/24
  ipipMode: Always
  natOutgoing: true
  nodeSelector: rack == "0"

---

apiVersion: projectcalico.org/v3
kind: IPPool
metadata:
  name: rack-1-ippool
spec:
  cidr: 192.168.1.0/24
  ipipMode: Always
  natOutgoing: true
  nodeSelector: rack == "1"
```
Установим calicoctl:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/206398f5-1fc2-4fec-85b8-9138f14cb1f4)  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/13846f7a-1c1f-4364-b597-77914df8ce5e)  
Добавим конфиг файл для calico:  
```
apiVersion: projectcalico.org/v3
kind: CalicoAPIConfig
metadata:
spec:
  datastoreType: "kubernetes"
  kubeconfig: "C:/users/Gusev/.kube/config"
```
Создадим ippool:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/47efe2ae-4035-4d83-bd15-1e41df047e13)  
Настроим проброс портов:
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/d6b839d0-f3f2-4dbe-81fe-c366510a045b)  
Результат:  
 ![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/b7b35347-4569-4436-8d7c-4e6910b70c90)  
Определим FQDN (полное доменное имя) при помощи команды nslookup, обратившись по ip адресу.
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/181f2b9b-c965-499f-ba3e-1fbde52e45c2)  
Пинг соседнего пода при помощи FQDN:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/10effea5-64e9-4079-aa33-ee408bddc8e8)  
Схема:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/97c9e973-a807-418e-9e28-c10f41bd67dd)



