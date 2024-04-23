# kubernetes-app-mysql
Este repositorio muestra como implementar una app que puede estar construida en nodejs junto con un motor mysql, de tal forma que podamos levantar un cluster en kubernetes para aplicar replicas  y así comunicar ambos cluster para mostrar y extraer datos desde una BD

El cluster a construir de kubernetes asociado al app, requiere que la imagen  app_restapi_nodejs esté costruida, esta se puede reemplazar por otra imagen pero para fines de prueba se construye una imagen que desplegará una api rest en nodejs que requiere una conexión a una base de datos MYSQL.

Datos de acceso: Podrá reemplazar los datos de acceso al motor de BD en el archivo mysql.yml, esto lo podrá hacer en los kind secret al inicio del archivo donde

mysql-root-pass: corresponde a la configuración del password del usuario roor, el cual podrá cambiar en el atributo password asignado un nuevo valor, este debe estar codificado en base64. Su valor asignado por defecto es 'test'


mysql-user-pass: corresponde a la configuración del usuario y contraseña a utilizar por el app o por una herramienta visual de diseño de bases de datos como MYSQL workbench  para ver todas las bases de datos del motor MYSQL, por defecto tendrá asignado como usuario y contraseña 'test_user'

Recuerde que podrá cambiarlos por uno de su preferencia, solo se asignan para tener un valor de referencia en la documentación de este repositorio

----------------------------------------------------------------------------------------------------------------------------------------------

Para probar todo el cluster, puede utilizar puede visitar el proyecto en: https://github.com/DMBIAM/RestApiNodeJs y combinarlo con kubernetes

-----------------------------------------------------------------------------------------------------------------------------------------------

Para poder construir el cluster solo es necesario ejecutar los comandos:

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
