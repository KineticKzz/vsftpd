### CASOS PRÁCTICOS

- Versión de vsftpd instalado
    
      vsftpd -v
      
      output: vsftpd: version 3.0.3


- Usuarios creados en la instalación

      getent passwd
      
      ftp:x:117:125:ftp daemon,,,:/srv/ftp:/usr/sbin/nologin


- Servicio asociado

      vsftpd

- Ficheros de configuración

      /etc/vsftpd.conf
      
  Las directivas mas importantes y que tenemos que cambiar son:
  
    - write_enable=YES –> Esta directiva nos permite poder escribir (copiar archivos y carpetas) al servidor FTP.
    - local_umask=022 –> Esta directiva nos permite habilitar los permisos nuevos cuando copiemos datos al servidro FTP, por defecto el umask es 077 pero podremos modificarlo por el valor que nosotros queramos, 022 es el umask más utilizado en otros servidores FTP.
    - ftpd_banner –> Esta directiva permite poner un banner de inicio de sesión.
    - chroot_list_enable=YES –> Nos permite habilitar el chroot de los diferentes usuarios del sistema, para que solamente un usuario entre en su carpeta /home/usuario y en ninguna más, es una medida de seguridad, pero hay que usarla con mucho cuidado ya que si un usuario tiene permisos en directorios superiores tendrá acceso al resto.
    - chroot_list_enable=YES –> Nos permite crear una lista con los usuarios en chroot, todos los que aparezcan aquí podrán conectarte.
    - chroot_list_file=/etc/vsftpd.chroot_list –> Es la lista de usuarios con sus rutas predeterminadas.

- Acceso al servidor FTP: usuarios del sistema + Enjaular usuario

      mkdir -p /home/ftp/usuarioftp
      chmod -R 777 /home/ftp/usuarioftp
      echo "allow_writeable_chroot=YES" >> /etc/vsftpd.conf
      sudo useradd -g ftp -d /home/ftp/usuarioftp -c "usuarioftp" usuarioftp
      sudo passwd usuarioftp
      
      systemctl restart vsftpd
      
     Ahora vamos a filezilla y nos conetamos al usuario usuarioftp

- Acceso al servidor FTP: anónimo tiene solo permiso de lectura en su dir

- Acceso al servidor FTP: anónimo tiene permiso de escritura en el directorio sugerencias, que es un subdirectorio de su directorio raíz.

- Acceso al servidor FTP: Creación de usuarios virtuales.

- Acceso seguro al servidor FTP
