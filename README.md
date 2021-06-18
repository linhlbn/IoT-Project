# Iot-Project-OOO

# 2. Introduction
THe team know :)

## Modify the config files

**Note**: It’s not required to modify the Helm-Chart because you can just change the K8s config files and apply the new configuration to the namespace. However, you can still customize the Helm-Chart and try to deploy your app with it.
   
   - **server.yaml**
    ![server](./img/server.png)
        
   - **mqtt.yaml** 
    ![mqtt](./img/mqtt.png)
        
   - **cluster-ip.yaml** 
    ![cluster](./img/cluster.png)
        
   - **ingress.yaml**      
   Set the Host Name → sso-frontend-{Name}.{namespace name}.{cluster name}.en.internal
    ![ingresshost](./img/ingresshost.png)
        
3. Run "Edge-Mock-Temperature" push data to postgresql
    - [Sample code](https://github.com/WISE-PaaS/edge-mock-temperature)
    - Follow the steps in the video to set up the Edge-Mock-Temperature data
    - See if the graph shows the latest temperature data
4. Set up Postgresql data source for your dashboard
    - ExternalHost (Find it in the credential’s JSON file decoded from the *secret*)
    - Database Name
    - Username
    - Password
5. Create a *Graph* panel and link it to the Postgresql data source as demonstrated in the training video.</br>
**Note : Stop the *auto-refeshing* setting of your dashboard and fix the time range so that we can check the result within the range.**

# 2. To-DO:
- edit the js file for more data capture !
- Use direct influxDB ?

# 3. Note
namespace_name : cxnam
cluster_name : ews
image: your image file

# 4. Code to deploy
1. start Docker  (win only ?)
1.2 move to the right path
2. minikube start (with PATH correct)
3. cd ... to the build folder (have docker file)
4. docker build -t bsdfuyih2gh/iot-home-mqtt:3.0.0 . // with the correct image name !!!
4.1 cd ...
4. docker build -t bsdfuyih2gh/iot-home-server:3.1.0 . // with the correct image name !!!

5. docker push bsdfuyih2gh/iot-home-mqtt:3.0.0
6. docker push bsdfuyih2gh/iot-home-server:3.1.0 

8?. kubectl config set-context --current --namespace=cxnam
9. kubectl config use-context 72d26fca-6c62-47ff-920e-4306bfbb07bc-ews-context

10. kubectl apply -f k8s --namespace cxnam

# 4. Code to check 
- kubectl get ingress
- kubectl get pods
- remove ingress: kubectl delete ingress iot-home-ooo
- remove pod: kubectl delete pods server-ooo-76bcdbbb77-fn6j5

<!-- Mark the node as unschedulable by using the kubectl cordon command. This ensures that no new pods will get scheduled to the node while you are preparing it for removal or maintenance. -->

- kubectl get deployments
- kubectl delete deployment

