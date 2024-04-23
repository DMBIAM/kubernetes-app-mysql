# kubernetes-app-mysql
Este repositorio muestra como implementar una app que puede estar construida en nodejs junto con un motor mysql, de tal forma que podamos levantar un cluster en kubernetes para aplicar replicas  y así comunicar ambos cluster para mostrar y extraer datos desde una BD

El cluster a construir de kubernetes asociado al app, requiere que la imagen  app_restapi_nodejs esté costruida, esta se puede reemplazar por otra imagen pero para fines de prueba se construye una imagen que desplegará una api rest en nodejs que requiere una conexión a una base de datos MYSQL.


Para comprender el app completamente, puede visitar el proyecto en: https://github.com/DMBIAM/RestApiNodeJs

Para poder cosntruir el cluster solo es necesario ejecutar los comandos:

Para MYSQL: 
kubectl apply -f kubernetes/mysql.yml 

Para el APP:
kubectl apply -f kubernetes/app.yml

Listar todos los POD: 
kubectl get pods

Listar todos los cluster y sus ip:
kubectl get svc

Realizar port forward:
kubectl port-forward svc/xxxxx 3306:3306
