# devops-ansible-actividad-2

Actividad 2 de Ansible en Diplomado DevOps Usach.

Uso de inventarios, playbooks con ansible y máquinas vagrant.

## Requerimientos

- vagrant
- virtualbox

## Poner en marcha

1. Levantar máquina master con vagrant


````
vagrant up
````

2. Levantar máquins nodos con vagrant


````
vagrant up
````

3. Crear clave a usuario root en cada nodo


````bash
vagrant ssh nodo #número de nodo correspondiente
sudo su
passwd
#Ingresar password
````

4. 
Dar permiso root a usuarios remotos. En cada nodo modificar archivo /etc/ssh/sshd_config


````bash
# Authentication:
LoginGraceTime 120
PermitRootLogin yes
StrictModes yes
````

5. Reiniciar servidos ssh en cada nodo


````bash
service ssh restart
````

5. En el master, generar llave


````bash
ssh-keygen -t rsa
````

6. Copiar llave a cada uno de los nodos


````bash
ssh-copy-id root@ip.nodo 
#Revisar Vagrantfiles para saber las direcciones ip de las máquinas nodos
````

7. En el master, situarse en la carpeta  /home/usuario/projects y ejecutar ansible-playbook

````bash
ansible-playbook -i inventario/inventario playbook/playbook.yaml
`````

