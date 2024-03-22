# Pildora5
GitHub para Pildora 5

<!-- 
Lo primero que se debe hacer es crear un ambiente en CLoud9 con sistema Linux y conexion ssh. Una vez creado entras a el y vas a instalar terraform

Los pasos para instalarlos son los siguientes: 
-->

sudo apt-get update && sudo apt-get install -y gnupg software-properties-common

<!-- 
Luego pega este bloque entero: 
-->

wget -O- https://apt.releases.hashicorp.com/gpg | \
gpg --dearmor | \
sudo tee /usr/share/keyrings/hashicorp-archive-keyring.gpg > /dev/null
gpg --no-default-keyring \
--keyring /usr/share/keyrings/hashicorp-archive-keyring.gpg \
--fingerprint
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] \
https://apt.releases.hashicorp.com $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update

<!-- 
Y por fin puedes hacer un apt install al terraform  
-->

sudo apt-get install terraform

<!-- 
Cuando ya tenemos el terraform procedemos a clonar el repositorio donde tenemos todos nuestros ficheros del terraform 
-->

git clone git clone https://github.com/MarcRGitHubTIC/Pildora5.git Pildora_5

<!-- 
Cuando tenemos el repositorio clonado, nos movemos a la carpeta descargada
-->

cd Pildora_5/s3-bucket-state

<!-- 
Ahora vamos a proceder a copiar el fichero de credentials de aws en la misma ruta, pero nombrandola "credentials2" 
-->

cp ~/.aws/credentials ~/.aws/credentials2

<!-- 
Cuando tenemos el fichero de credentials2 debemos copiar las credenciales de nuestro lab a este fichero creado 
-->

sudo vi ~/.aws/credentials2

<!-- 
Y hacemos los comandos para el terraform 
-->

terraform init
terraform plan
terraform apply

<!-- 
Cuando ha terminado y lo ha hecho exitosamente, salimos de la carpeta en la que estamos 
-->

cd ..

<!-- 
Por ultimo necesitamos realizar nuevamente los comandos para levantar el terraform 
-->

terraform init
terraform plan
terraform apply

<!-- 
Cuando los dos terraforms se hayan levantado, puedes acceder al load balancer, obtener el link publico e irte al navegador y pegarlo con "/wordpress" al final para acceder al wordpress 

"wordpress-alb-1799337795.us-east-1.elb.amazonaws.com/wordpress" Serie un ejemplo de la URL que necesitamos 
-->