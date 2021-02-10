### ESQUEMA DE RED

![img](https://i.imgur.com/NBlGZDM.png)

Donde: 

+ Usaremos maquinas virtuales, una como servidor y una como cliente
+ La servidor tendrá un adaptador puente o nat (en nuestro caso será puente así podremos trabajar por ssh en el equipo físico) y una red interna, que será la elegida para conectar el cliente
+ servidorxxx = servidor207
+ ip servidor (adaptador puente) = 192.168.0.57
+ ip servidor (red interna) = 192.168.1.1
+ Para nuestros casos prácticos solo será necesario un cliente
+ ip del cliente 192.168.1.11
+ gateway (puerta de enlace) del cliente 192.168.1.1

