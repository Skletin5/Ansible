# Ansible
Ansible es una plataforma de software que permite la administración de varios equipos de forma simultanea desde un unico servidor a traves de ssh. Este contiene varias colecciones de modulos para realizar infinidad de tareas en dichos equipos, por lo que aquí documentare el uso de uno de ellos.

## Slurp
El modulo slurp es similar a otro modulo llamado `fetch` asi que primero explicare brevemente el mismo para introduciros al procedimineto:  

Fetch nos permite obtener el contenido de un fichero de una o mas maquinas de la sigiente manera...
  ```yaml
  - name: Obtener contenido de /home/usuario/fichero
    ansible.builtin.fecth:
      src: /home/usuario/fichero
      dest: /home/usuario/resultado
  ```
Esto transportara el contenido de dicho fichero a nuestra maquina de ejecución creando el fichero mencionado en el destino. Ahora vamos con Slurp:  

Slurp nos permite codificar a base64 el contenido del fichero del que extraigamos la información, podriamos decir que es una forma segura de obtener información desde otro equipo.  
Su sintaxis funciona de la siguiente manera:  
![ComandoSlurp1.PNG](img/ComandoSlurp.png)  
Como Puedes ver, debemos agragear la salida del modulo a una variable usando `register: NOMBRE_VARIABLE` para luego llamar al contenido de la misma con el modulo `debug`

Y nos devolvera lo siguiente:  
![ResultadoSlurp1.PNG](img/ComandoSlurp.png)

Tambien podemos descodificar el contenido en un mensaje para ver desde nuestro terminal que es lo que hemos descargado. Para ello volveremos a usar el modulo `debug`:  
![ComandoSlurp2.PNG](img/ComandoSlurp2.png)  
Pedimos que nos imprima el contenido de la variable y que la decodifique de base64.  

Nos devolvera lo siguiente:  
![ResultadoSlurp2.PNG](img/ResultadoSlurp2.png)  

Podeis descargar ambos playbooks en el contenido de este repositorio.
## Referencias
- [Guia en youtube de Percy Grunwald from TopTechSkills](https://www.youtube.com/watch?v=fXmPZNacitE)  
- [Guia oficial de Ansible](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/slurp_module.html#ansible-collections-ansible-builtin-slurp-module)
