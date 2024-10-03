                                                      Kubernetes Assignment:-  2
Create Helm charts for a sample application (e.g., a web server) with   configurable values.
 command :  helm create web-app
        This command will generate a Helm chart template in a directory called spring-boot-app. The default Helm chart includes directories like templates, and files such as Chart.yaml and values. yaml. 
         go to web -app command : cd web-app
Modify the values.yaml file.
         Edit the values.yaml file to include configurable values for your Spring Boot application. Set the Docker image reference, container port and replica set.  
         Using this command:      vi  values.yaml
Modify the deployment.yaml file. 
        Open the deployment.yaml file located in the templates directory and update it to use the Spring Boot Docker image and container port.
        command :  vi ./templates/deployment.yaml
Save the file after making the changes.
 
 Use the Helm charts to deploy the application to a Kubernetes cluster.
 Install the Helm Chart:
 Deploy the Spring Boot application to the Kubernetes cluster using the helm install command:
•	helm install my-web-app ./web-app

 
Verify the Deployment:
                Using this command :
•	kubectl get pods 
•	kubectl get services
Upgrade the application by changing the Helm chart values and performing a Helm upgrade.
Update the values.yaml file: For example, update the replicaCount value from 1 to 2
Apply the upgrade command :
                                helm upgrade my-web-app  ./web-app
Verify the upgrade command:
                             kubectl get deployment my-web-app
 
Implement a namespace strategy for your Kubernetes cluster, organizing applications and resources into separate namespaces based on their environments (e.g., development, staging, production).
Create Namespaces using this command:
kubectl create namespace development
kubectl create namespace staging
kubectl create namespace production

Deploy the Application to Different Namespaces:
helm install my-web-app-app-dev ./web-app --namespace development
helm install my-web-app-staging ./web-app --namespace staging
helm install my-web-app-prod ./web-app --namespace production


Verify Deployments in Different Namespaces:
kubectl get pods -n development
kubectl get pods -n staging
kubectl get pods -n production






                   
Rollback the application to a previous version using Helm rollback.
View the Helm Release History:
               helm history my-web-app
Rollback to a Previous Version:
               Use the helm rollback command followed by the release name and revision number:
               helm rollback my-web-app 2
Verify the Rollback:
              Check the status of the deployment to ensure it has been rolled back successfully:
               kubectl get deployment my-web-app

 
