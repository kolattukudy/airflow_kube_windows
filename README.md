
docker build --rm --build-arg AIRFLOW_DEPS="kubernetes" --build-arg PYTHON_DEPS="kubernetes" -t bjose/docker-airflow .

# airflow-on-kubernetes
Source code for guide to run Apache Airflow on Kubernetes

Set proxy with 
kubectl proxy 


Everthing need to be run with mingwin

start
cleaning up PV
kubectl patch pvc airflow-logs-pvc -p '{"metadata":{"finalizers": []}}' --type=merge



Install dashboard after each kuberenete cluster restart
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0/aio/deploy/recommended.yaml

create admin user for dashboard under dashboard folder
kubectl apply -f dashboard-admin.yaml

Get token
kubectl get secret -n kubernetes-dashboard $(kubectl get serviceaccount admin-user -n kubernetes-dashboard -o jsonpath="{.secrets[0].name}") -o jsonpath="{.data.token}" | base64 --decode

 get the token


Access Kubernettte dashboard from 
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login

 


http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/#/login

Set the airflow weberver service as Loadbalancer
on the service Yaml

access airflow

http://localhost:8080/admin


Kubectl login
kubectl exec -itn default pod airflow-scheduler-f84d978f7-bdbs5 -- /bin/bash
