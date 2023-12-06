University: [ITMO University](https://itmo.ru/ru/)
Faculty: [FICT](https://fict.itmo.ru)
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)
Year: 2023/2024
Group: K4110c
Author: Gusev Dmitriy Alexeevich
Lab: Lab2
Date of create: 29.11.2023
Date of finished: 07.12.2023  
Используя myfirst.yaml создадим deployment с двумя репликами и service для доступа к двум репликам.  
myfirst.yaml:  
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: app-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: app
  template:
    metadata:
      labels:
        app: app
    spec:
      containers:
        - name: itdt-contained-frontend
          image: ifilyaninitmo/itdt-contained-frontend:master
          ports:
          - name: container-port
            containerPort: 3000
          env:
            - name: REACT_APP_USERNAME
              value: "DG-GDST"
            - name: REACT_APP_COMPANY_NAME
              value: "ITMO"

---

apiVersion: v1
kind: Service
metadata:
  name: app
  namespace: default
  labels:
    app: app
spec:
    type: NodePort
    ports:
    - port: 8200
      targetPort: container-port
    selector:
      app: app      
```  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/e9f110ac-423d-48a6-9721-72bf04d9e125)  
Проверим, что все создаваемые в манифесте ресурсы появились:
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/f163d2fd-70ef-4b23-86de-147780f75742)  
Настроим проброс портов:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/f0ef891e-4cac-495a-8604-8f8b0fff795c)  
Результат:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/1b743c1e-94d1-45ce-87e1-1077b98449d3) 
При обновлении страницы container name не изменяется так как сервис берёт только одну реплику и каждый раз использует ее без балансировщика нагрузки.  
Логи подов:
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/5363909c-b8bc-435a-a17e-69f5f54da3e0)  
Схема:  
![image](https://github.com/DG-GDST/2023_2024-introduction_to_distributed_technologies-K4110c-gusev_d_a/assets/62474929/788dbc9a-9c2b-4c30-bc3f-adbd57130427)



