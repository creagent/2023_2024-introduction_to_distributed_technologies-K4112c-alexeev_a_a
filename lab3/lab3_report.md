University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Alexeev Anton Andreevich\
Lab: Lab3\
Date of create: 16.11.2023\
Date of finished: 

___
1) Cоздание и применение configMap configmap_3.yaml kubectl apply -f configmap_3.yaml
2) Cоздание и применение replicaSet replicaset_3.yaml с 2 репликами контейнера ifilyaninitmo/itdt-contained-frontend:master (REACT_APP_USERNAME, REACT_APP_COMPANY_NAME подтягиваются из предыдущего файла): kubectl apply -f replicaset_3.yaml
3) Создание и применение service service_3.yaml: kubectl apply -f service_3.yaml
4) Включение Ingress: minikube addons enable ingress
5) Генерация TLS сертификата: ``openssl req -x509 -newkey rsa:4096 -sha256 -days 12 -nodes -keyout tls.key -out tls.crt -subj "/CN=lab3.front.com"``
6) Импорт сертификата в minikube: ``kubectl create secret tls lab3-local-tls --cert=tls.crt --key=tls.key``
7) Cоздание ingress [ingress_3.yaml](ingress_3.yaml) в minikube, где указан ранее импортированный сертификат, FQDN и имя сервиса и его применение: ``kubectl apply -f ingress.yaml``
8) Прописываем в hosts (C:\Windows\System32\Drivers\etc\hosts) FQDN и IP адрес localhost: ``127.0.0.1 lab3.front.local``
9) Создаем туннель между локальной машиной и Minikube кластером: ``minikube tunnel``
10) Вход в веб приложение по FQDN используя HTTPS и проверка наличия сертификата: https://lab3.front.local

<img width="670" alt="Снимок экрана 2023-12-06 в 22 51 44" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/36edc55b-68c9-4f77-bced-a376d4586d49">

<img width="910" alt="277191386-0051622d-98c0-43c6-b405-d0a221ad1e17-2" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/211d9295-1cbd-4a7a-8aae-6f6d3d92f3a9">

![277192281-56d3a6bf-a277-4054-992b-d0a45442d3e4-2](https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/755b2bbf-1aab-417b-84e9-3035a6ca755f)


