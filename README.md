# script-projeto-apache
script para o projeto apache-DIO
neto@serverlinux:~$ su
Password:
root@serverlinux:/home/neto# cd /
root@serverlinux:/# mkdir /scripts2 //criando pasta na raiz
root@serverlinux:/# ls
bin                boot   dev    etc   lib    lib.usr-is-merged  media  opt   root  sbin                scripts   snap  swap.img  tmp  var
bin.usr-is-merged  cdrom  disk2  home  lib64  lost+found         mnt    proc  run   sbin.usr-is-merged  scripts2  srv   sys       usr
root@serverlinux:/# cd scripts2 //acessando a pasta
root@serverlinux:/scripts2# ls
root@serverlinux:/scripts2# nano script-iac2.sh //criando o arquivo de script no nano
#!/bin/bash


echo "Atualizando o servidor..."

apt-get update
apt-get upgrade -y
apt-get install apache2 -y
apt-get install unzip -y

echo "Baixando e copiando os arquivos da aplicação..."

cd /tmp
wget https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip
unzip main.zip
cd /linux-site-dio
cp -R * /var/www/html/

root@serverlinux:/scripts2# ls -l
total 4
-rw-r--r-- 1 root root 342 abr 18 20:03 script-iac2.sh
root@serverlinux:/scripts2# chmod +x ./script-iac2.sh
root@serverlinux:/scripts2# ls -l
total 4
-rwxr-xr-x 1 root root 342 abr 18 20:03 script-iac2.sh
root@serverlinux:/scripts2# ./script-iac2.sh
Atualizando o servidor...
./script-iac2.sh: line 16: cd: /linux-site-dio: No such file or directory //mostrou que houve um erro
root@serverlinux:/scripts2# cd /tmp //entrar na pasta tmp onde está o arquivo que deu erro
root@serverlinux:/tmp# ls
linux-site-dio-main //faltou o main, por isso que deu erro  
systemd-private-b19f3d19bfa84f66894e9ca81e64059d-apache2.service-53hWua       systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-logind.service-1IHnlM
main.zip             systemd-private-b19f3d19bfa84f66894e9ca81e64059d-ModemManager.service-B2OdgI  systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-resolved.service-qDHMO8
snap-private-tmp     systemd-private-b19f3d19bfa84f66894e9ca81e64059d-polkit.service-SlwNvb        systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-timesyncd.service-gp7vKU
root@serverlinux:/tmp# cd /scripts2 //entrar novamente na pasta
root@serverlinux:/scripts2# ls //verificou o arquivo 
script-iac2.sh
root@serverlinux:/scripts2# nano script-iac2.sh //reeditar com nano
#!/bin/bash


echo "Atualizando o servidor..."

apt-get update
apt-get upgrade -y
apt-get install apache2 -y
apt-get install unzip -y

echo "Baixando e copiando os arquivos da aplicação..."

cd /tmp
wget https://github.com/denilsonbonatti/linux-site-dio/archive/refs/heads/main.zip
unzip main.zip
cd /linux-site-dio-main //arquivo reeditado com o “main” na frente
cp -R * /var/www/html/
root@serverlinux:/scripts2# ./script-iac2.sh //executar de novo
Atualizando o servidor...
root@serverlinux:/scripts2# cd /var/www/html/  //verificar se os arquivos forma copiados
root@serverlinux:/var/www/html# ls //listar
index.html           systemd-private-b19f3d19bfa84f66894e9ca81e64059d-apache2.service-53hWua         systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-resolved.service-qDHMO8
linux-site-dio-main  systemd-private-b19f3d19bfa84f66894e9ca81e64059d-fwupd.service-qSwJve           systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-timesyncd.service-gp7vKU
main.zip             systemd-private-b19f3d19bfa84f66894e9ca81e64059d-ModemManager.service-B2OdgI    systemd-private-b19f3d19bfa84f66894e9ca81e64059d-upower.service-BQ93Zy
main.zip.1           systemd-private-b19f3d19bfa84f66894e9ca81e64059d-polkit.service-SlwNvb
snap-private-tmp     systemd-private-b19f3d19bfa84f66894e9ca81e64059d-systemd-logind.service-1IHnlM  //arquivos copiados
root@serverlinux:/var/www/html#

