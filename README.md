# 'Petclinic' on Kubernetes.
Deploying Spring based Petclinic project on kubernates cluster using minikube

## Getting Started

### Pre-requisites
* Install kubectl: <https://kubernetes.io/docs/tasks/tools/install-kubectl-windows/>
* Install minikube: <https://minikube.sigs.k8s.io/docs/start> 
* Install docker: <https://docs.docker.com/engine/install/> 
* Sign up on docker hub: <https://hub.docker.com/>
* Clone project to local: <https://github.com/spring-projects/spring-petclinic>
## Steps for  execution
* Write Dockerfile:

![image](https://github.com/user-attachments/assets/4c6a3ae5-7e11-492f-9b9b-0cf6a54aeba0)

* Create docker image:
```
docker build -t pet-clinic-demo
```
* Verify in docker images list:
```
docker images
```
![image](https://github.com/user-attachments/assets/18b87c2b-7dfc-456e-967d-58674976b39c)

* Docker desktop:

![image](https://github.com/user-attachments/assets/e17c90c3-9063-45e6-9517-e7b3113bcaa1)

* Run docker image locally:
```
docker run -p 8080:8080 pet-clinic-demo
```
![image](https://github.com/user-attachments/assets/3f9c9628-5b62-4fad-9b3d-d7df1f7f33c8)

* Push local docker image to docker hub:

* 1: Add tag
```
docker tag pet-clinic-demo rushi2323/pet-clinic-demo:01
```
![image](https://github.com/user-attachments/assets/947823a4-c877-4166-9b14-3f665b2cab87)

* 2: Push to docker hub
```
docker push rushi2323/pet-clinic-demo:01
```
![image](https://github.com/user-attachments/assets/63a779ae-07ac-46be-b0b1-fd989554bf69)

* Start minikube :
```
minikube start
```
![image](https://github.com/user-attachments/assets/32cf703f-9224-423a-937f-4fc07f7507d5)

* Minikube should be on running state
```
minikube status
```
![image](https://github.com/user-attachments/assets/5d070ff0-d572-4a70-9b3e-ee5b97f145bc)

* Create deployment on Kubernetes 
```
kubectl create deployment pet-clinic-deployment  –-image= rushi2323/pet-clinic-demo
```
![image](https://github.com/user-attachments/assets/1acf2b27-8afd-40b3-b2c1-45afe0754ec2)

* Verify deployments
```
kubectl get deployments 
```
![image](https://github.com/user-attachments/assets/c84d7d77-d4a6-443e-b9df-e3078d1ca53d)

* Verify created pods
```
kubectl get pods 
```
![image](https://github.com/user-attachments/assets/b8d86406-8bcd-44f8-ab25-ee7253aa10fd)

* Verify pods using k9s dashboard

![image](https://github.com/user-attachments/assets/b0f585da-95a2-4af7-b489-d0d2aeb3a934)

* Port binding
```
kubectl expose deployment  pet-clinic-deployment --port=8080 --type=LoadBalancer
```
![image](https://github.com/user-attachments/assets/e48aa4cf-4f21-428f-b0e7-8dc53ba9a825)

* Verify kubectl services
```
kubectl get services
```
![image](https://github.com/user-attachments/assets/e17c1eab-ab85-4455-91dc-89c031590bcd)

* Service expose on minikube
```
minikube service pet-clinic-deployment
```
![image](https://github.com/user-attachments/assets/eee87f05-7c30-4f82-9228-57113bad7f68)

* Verify url is up and running 

![image](https://github.com/user-attachments/assets/56a1f32f-5ec3-4ed7-a5b2-f8544692ff1a)

* Verify pods on minikube dashboard
```
minikube dashboard
```
![image](https://github.com/user-attachments/assets/e33215de-175e-4864-981d-ec010cd563bb)

![image](https://github.com/user-attachments/assets/afdc7c19-86f4-4670-823f-86f4c7b3f239)

* Scaling up to 4 replicas
```
kubectl scale deployment pet-clinic-deployment –replicas=4 
```
![image](https://github.com/user-attachments/assets/969358c8-159c-4cbd-b3f8-a59252ae8743)

```
kubectl get pods
```
![image](https://github.com/user-attachments/assets/4f48d5ad-ac0d-41bd-83a6-477a47eab56b)

* Minikube dashboard

![image](https://github.com/user-attachments/assets/b9225dbf-fa13-4b74-9b24-d4eee911ac03)

* With K9s

![image](https://github.com/user-attachments/assets/61b9ca35-2aab-412b-b2fd-419b00386b42)

* Scaling back or down to 1 replica 
```
kubectl scale deployment pet-clinic-deployment -–replicas=1
```
![image](https://github.com/user-attachments/assets/1cec55e9-3763-474a-bc8d-710ca09419bb)

