# pet-clinic-k8s
Deploying pet-clinic app on kubernates using minikube

# Clone project from github link to local:  https://github.com/spring-projects/spring-petclinic
# Write Dockerfile:
![image](https://github.com/user-attachments/assets/673983bf-ae8b-428e-ba83-ad23e38255fa)
# Create docker image:
> docker build -t pet-clinic-demo .
# Verify in docker images list:
> docker images OR  > docker image ls
![image](https://github.com/user-attachments/assets/5d1be937-3d71-4dfa-be1b-d3f042d7a382)
# Docker desktop: 
![image](https://github.com/user-attachments/assets/b9f0946e-ac07-4eaf-adc8-01904fc09cb1)
# Run docker image locally:
> docker run -p 8080:8080 pet-clinic-demo
![image](https://github.com/user-attachments/assets/35b42c3d-279b-47c5-b14d-132796cb2eb7)
# Push local docker image to docker hub:
Step 1:
> docker tag pet-clinic-demo rushi2323/pet-clinic-demo:01
![image](https://github.com/user-attachments/assets/397f2b05-c56e-4db3-93fa-5e913e86c26e)
Step 2:
> docker push rushi2323/pet-clinic-demo:01
![image](https://github.com/user-attachments/assets/5c6e4b8f-61cb-42d3-9eb8-d8869ae04a04)
# Verify minikube status:
![image](https://github.com/user-attachments/assets/7344ae03-1bdd-4e1a-a379-8d41928fff17)
# Start minikube :
![image](https://github.com/user-attachments/assets/d33e2f2d-4cd4-49e2-88b3-68b41fca51e1)
# Create deployment on Kubernetes 
> kubectl create deployment pet-clinic-deployment  –-image= rushi2323/pet-clinic-demo
![image](https://github.com/user-attachments/assets/d8ddb4e1-7b91-463b-8836-1aac244638cd)
# Verify deployments
> kubectl get deployments 
![image](https://github.com/user-attachments/assets/3e8c4426-ac76-4f5b-8e32-c720ba9a386a)
# Verify created pods
> kubectl get pods 
![image](https://github.com/user-attachments/assets/841b494d-fd80-469f-bbf9-183292a640ee)
# Verify pods using k9s dashboard   
![image](https://github.com/user-attachments/assets/7230ab9a-09bf-46b2-85c3-1495a124adcd)
# Port binding
kubectl expose deployment  pet-clinic-deployment --port=8080 --type=LoadBalancer
![image](https://github.com/user-attachments/assets/b1fd6c5d-4ea1-4e64-8c16-46df293e5ef8)
# Verify kubectl services
> kubectl get services
![image](https://github.com/user-attachments/assets/e40a8c25-0e6e-4c4f-a2e9-2f9d49dffeb7)
# Service expose on minikube
> minikube service pet-clinic-deployment
![image](https://github.com/user-attachments/assets/a4f412d3-9beb-4f7c-8a6e-d32b9014ce10)
# Verify on url 
![image](https://github.com/user-attachments/assets/fe8786ad-6856-4410-9cc2-9c595a24da03)
# Minikube dashboard
> minikube dashboard  
![image](https://github.com/user-attachments/assets/ecf4c0e8-794f-4d10-9fac-d7b89ec63827)
![image](https://github.com/user-attachments/assets/58dc3108-ee72-4ff8-9a17-71d174c4c466)

# Scale up for 4 replicas
> kubectl scale deployment pet-clinic-deployment –replicas=4  
![image](https://github.com/user-attachments/assets/fe8b5d25-be90-4929-89a8-f5a95905034a)
> kubectl get pods  
![image](https://github.com/user-attachments/assets/4032bfd5-797b-47e6-82f0-50153bdd6028)
# Minikube dashboard
![image](https://github.com/user-attachments/assets/45fc6700-c801-465d-bb0e-a582b797712b)
# K9s dashboard  
![image](https://github.com/user-attachments/assets/56fdf02c-3885-478a-902d-a257fc7f88b4)
# Scale back or down to 1 replica 
> kubectl scale deployment pet-clinic-deployment –replicas=1 
![image](https://github.com/user-attachments/assets/3cd9357c-23b3-4a55-a41c-af65b2b64554)
