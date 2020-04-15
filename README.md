# MongoDB Dockerfile



# Base Docker Image
dockerfile / ubuntu

# Instalación
# Instalar Docker .

#Descargue la compilación automatizada del registro público de Docker Hub :docker pull dockerfile/mongodb

(alternativamente, Se Puede Construir Una imagen de Dockerfile: docker build -t="dockerfile/mongodb" github.com/dockerfile/mongodb)

# Uso

correr mongod

docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb

# Ejecutar mongodcon directorio persistente / compartido

docker run -d -p 27017:27017 -v <db-dir>:/data/db --name mongodb dockerfile/mongodb
  
# Ejecutar mongodcon soporte HTTP

docker run -d -p 27017:27017 -p 28017:28017 --name mongodb dockerfile/mongodb mongod --rest --httpinterface

Ejecutar con un tamaño mongodde archivo predeterminado más pequeño

docker run -d -p 27017:27017 --name mongodb dockerfile/mongodb mongod --smallfiles

# correr mongo

docker run -it --rm --link mongodb:mongodb dockerfile/mongodb bash -c 'mongo --host mongodb'

Uso con VirtualBox (boot2docker-vm)

# Deberá configurar el reenvío de puertos nat con:

VBoxManage modifyvm "boot2docker-vm" --natpf1 "guestmongodb,tcp,127.0.0.1,27017,,27017"

# Esto le permite utilizar un contenedor con los mongocomandos estándar .
