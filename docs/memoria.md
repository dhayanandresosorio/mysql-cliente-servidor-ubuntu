# Memoria tecnica - MySQL Cliente-Servidor en Ubuntu

## Resumen

Esta practica documenta la instalacion y configuracion de MySQL en un entorno cliente-servidor con Ubuntu 24.04.

El objetivo es configurar un servidor MySQL, permitir conexiones remotas desde una maquina cliente y comprobar el acceso mediante terminal, MySQL Workbench y DBeaver.

## Entorno utilizado

Servidor MySQL:

- Sistema operativo: Ubuntu Server 24.04
- Servicio: MySQL Server
- Funcion: alojar la base de datos y aceptar conexiones remotas

Cliente:

- Sistema operativo: Ubuntu 24.04
- Herramientas: MySQL Client, MySQL Workbench y DBeaver
- Funcion: conectarse al servidor MySQL y comprobar el acceso remoto

Base de datos utilizada:

```text
nba
```

## Configuracion principal

Instalacion de MySQL Server:

```bash
sudo apt update
sudo apt install -y mysql-server
```

Comprobacion del servicio:

```bash
sudo systemctl status mysql
```

Acceso local a MySQL:

```bash
sudo mysql
```

Archivo de configuracion modificado:

```text
/etc/mysql/mysql.conf.d/mysqld.cnf
```

Cambio realizado:

```text
bind-address = 0.0.0.0
```

Reinicio del servicio:

```bash
sudo systemctl restart mysql
```

## Usuario remoto

Usuario remoto utilizado en el laboratorio:

```sql
CREATE USER 'dhayancliente'@'%' IDENTIFIED BY 'CHANGE_ME_REMOTE_PASSWORD';
GRANT ALL PRIVILEGES ON nba.* TO 'dhayancliente'@'%';
FLUSH PRIVILEGES;
```

Las contrasenas reales no se publican en el repositorio.

## Conexion desde cliente

Instalacion del cliente MySQL:

```bash
sudo apt install -y mysql-client
```

Conexion remota:

```bash
mysql -h IP_SERVIDOR_MYSQL -u dhayancliente -p
```

Comprobaciones dentro de MySQL:

```sql
SHOW DATABASES;
USE nba;
SHOW TABLES;
```

## Pruebas con herramientas graficas

La practica incluye pruebas de conexion con:

- MySQL Workbench
- DBeaver

Las capturas de la practica se encuentran en la carpeta:

```text
capturas/
```

## Capturas

![MySQL Workbench instalado](../capturas/primera.png)

![Conexion en MySQL Workbench](../capturas/tercera.png)

![Conexion correcta](../capturas/quinta.png)

![Consulta desde Workbench](../capturas/octava.png)

![Nueva conexion en DBeaver](../capturas/decima.png)

![Prueba de conexion en DBeaver](../capturas/trece.png)

![Consulta en DBeaver](../capturas/quince.png)

## Seguridad

Para publicar esta practica en GitHub se han sustituido las contrasenas por placeholders.

Ejemplos:

```text
CHANGE_ME_ROOT_PASSWORD
CHANGE_ME_REMOTE_PASSWORD
CHANGE_ME_PASSWORD
```

No se deben subir credenciales reales al repositorio.

## Organizacion del repositorio

```text
mysql-cliente-servidor-ubuntu/
|-- README.md
|-- .gitignore
|-- .gitattributes
|-- docs/
|   |-- memoria.md
|-- capturas/
|   |-- capturas de la practica
```

Esta version de la memoria se deja limpia para evitar problemas de codificacion. La documentacion ampliada puede editarse posteriormente desde GitHub usando el editor web.
