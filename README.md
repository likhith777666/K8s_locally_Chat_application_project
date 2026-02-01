Implemented K8s for Chat application using minikube
Implementing process
1. Installed the docker and set up minikube in the system refered the minikube documentation
2. Cloned the project into system using "git clone <repolink>"
3. Run the minikube in the docker using "minikube start --driver=docker" -- It will run the minikube in the docker i.e a container will run.
4. Now I can deploy the application using this container which is minikube.
5. Inspected the code and understood the code.
6. Created Docker images and pull that images into docker hub for backend , front end and for mongo db however it will present in the hub.(docker push likhith045/chat-appfrontend:tagname --for frontend, docker push likhith045/chat-app:tagname --for backend)
7. Main Work
   1. first created the namespace namespace.yml
   2. Created the deployment for backend backenddeployment.yml
   3. Created the deployment for frontend frontend-deployment.yml
   4. Created the deployment for mongodb mongodb-deployment.yml
   5. The main importent thing here we need to create pv and pvc means persistance volume and persistance volume claim
   6. about pv and pvc -- A pod can be restarted, deleted and resume again but the data wll lot if it is restarted and deleted , for databases like mongodb data must not lost for that we need create an storage in the hard disk.
      for that by using the pvc we can claim the storage and by using pv and mentioning the path we can store the data in that disk path if pod will restart or deleted the data will be available in the disk after the resume of the pod the data will retrive fron the hard disk.

  7. Next we need to create the services to expose the port to access we can't access the without exposing , for that we need to create backend-serive.yml , frontend-service.yml and mongodb-sevice.yml.
  8. For Jwt tocken if it is very large use secret.yml.
  9. Mention env variable in the mongodb and backend.
  10. Now run the config file one by one
  11. "kubectl apply --f <config-file-name>" for all service, deployments.
  12. Check the status using kubectl "kubectl get pods -n <namespace>" to check the status of running pods
  13. If there is any issue check the using kubectl describe pods <podID> -n <namespace>.
  14. Or kubectl logs <podId>  -n <namespace>.
  15. Now if every thing running then we need to do port forwarding for backend and frontend and mongodb using the "kubectl port-forward service/<service-name> -n <namespace> <LOCAL_PORT>:<SERVICE_PORT>"
  16. Completed.         

