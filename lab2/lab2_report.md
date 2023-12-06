University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Alexeev Anton Andreevich\
Lab: Lab2\
Date of create: 13.11.2023\
Date of finished: 

___

1) Создание [deployment](lab2_deployment.yaml) с 2 репликами контейнера ifilyaninitmo/itdt-contained-frontend:master, установка переменных в эти реплики и создание сервиса для доступа к подам: 
REACT_APP_USERNAME, REACT_APP_COMPANY_NAME: ``kubectl apply -f lab2_deployment.yaml``
2) Получение имен созданных контейнеров: ``kubectl get pods``
3) Запуск режима проброса портов: ``kubectl port-forward <pod_name> 3001:3000``
4) Смотрим через браузер веб-интерфейс:

<img width="1225" alt="275289338-702bd6eb-f2d4-40a7-8e4b-83162c7f5d99-2" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/983cb40b-0d2b-4dbf-abcc-b27ade4f5588">


5) Смотрим логи контейнеров: ``kubectl logs <pod_name>``

<img width="520" alt="286292723-6a49c7ab-26d2-4e2c-acc1-98c94ba050f4" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/b4e98c37-95d7-4690-8939-802ba94348b8">

___

Схема организации контейеров и сервисов

<img width="475" alt="275308791-f58b32c8-8248-43ad-b114-13b2e22172aa" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/1b5dca21-a3e8-4c10-ae16-0a996d0a1f2c">

