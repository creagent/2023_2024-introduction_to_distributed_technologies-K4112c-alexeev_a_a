University: [ITMO University](https://itmo.ru/ru/)\
Faculty: [FICT](https://fict.itmo.ru)\
Course: [Introduction to distributed technologies](https://github.com/itmo-ict-faculty/introduction-to-distributed-technologies)\
Year: 2023/2024\
Group: K4112c\
Author: Alexeev Anton Andreevich\
Lab: Lab4\
Date of create: 9.17.2023\
Date of finished: 

___
1) Запуск Minikube с плагином CNI Calico и в режиме Multi-Node Clusters: ``minikube start --cni=calico --nodes=2``
2) Проверка работы CNI плагина Calico и количество нод командами:
- ``kubectl get nodes``
- ``kubectl get pods -n kube-system -l k8s-app=calico-node``

<img width="564" alt="286376678-0d6ba8f2-0fcc-4476-8177-daf6d00d83e4" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/4305f853-d7fc-40c9-b301-5d318c003277">

Для проверки IPAM (IP Address Management), назначим метки узлам. Присвоем метку географического расположения: location=us-east и location=us-west, для соответсвующих нод.\
``kubectl label nodes <узел_1> location=us-east``\
``kubectl label nodes <узел_2> location=us-west``

3) Создадим манифест для Calico, определяющий IP-пулы в соответствии с метками узлов: [ippool.yaml](ippool.yaml)

4) Создадим манифест для Deployment с необходимыми переменными окружения: [deployment.yaml](deployment.yaml)
5) Установим calicoctl: ``kubectl create -f calicoctl.yaml``
6) Создадим IP пулы с помощью calicoctl в поде: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl create -f - < ippool.yaml --allow-version-mismatch``
7) Выводим информацию о IP пулах через calicoctl: ``kubectl exec -i -n kube-system calicoctl -- /calicoctl get ippool -o wide   --allow-version-mismatch``
<img width="831" alt="286376888-cb2c19b1-b4cc-4a6e-8e2f-81944ed8dbd8" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/2d4819d2-0a6c-4008-a835-76116c75d37b">

9) Открываем доступ к сервису Minikube: ``minikube service frontend-service``
10) Пробрасываем порты сервиса на локальную машину: ``kubectl port-forward service/frontend-service 9090:9090``
<img width="853" alt="281860575-f0a483cf-b5fe-40a6-83fb-343b2e674375-2" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/dbbb22b6-40fc-4b01-af7f-f1a0a23fde9f">

11) Получим IP одного из контейнеров и пропингуем из другого:
- ``kubectl get pods -o wide``
- ``kubectl exec -it frontend-6844569ff8-7bcm9 -- /bin/sh``
- ``ping 10.244.205.193``
<img width="791" alt="286376987-af59b2b6-38c8-4a11-a1eb-86c73ef1eb8e" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/14025f1f-f41b-4a04-97ba-692a3d484843">

___

### Схема

<img width="497" alt="282321193-1957143e-8e9c-4113-87e8-92941f7a0c9a-2" src="https://github.com/creagent/2023_2024-introduction_to_distributed_technologies-K4112c-alexeev_a_a/assets/70636573/81ebf59d-d18b-4d6c-b419-21f83d292e75">

