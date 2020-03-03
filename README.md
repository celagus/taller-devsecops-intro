# Bienvenidos al repositorio del taller de introducción a DevSecOps

La actividad práctica del taller consistirá en el aprovisionamiento de una VM Linux Ubuntu con Jenkins (herramienta de automatización que utilizaremos para el desarrollo del AppSec pipeline) junto con otras herramientas utilizadas para automatizar controles de Seguridad (Security-as-Code). Todas las herramientas utilizadas en este taller son FREEWARE, es decir, con licencia para su libre uso y distribución.

*** DISCLAIMER IMPORTANTE ***: EL CONTENIDO DE ESTE TALLER ESTÁ SIMPLIFICADO CON FINES PEDAGÓGICOS, NO UTILICE ESTAS HERRAMIENTAS EN ENTORNOS PRODUCTIVOS SIN SU DEBIDA HARDENIZACIÓN EN BASE A LAS BUENAS PRÁCTICAS Y/O LINEAMIENTOS CORRESPONDIENTES.

Los requisitos para ejecutar las actividades son los siguientes:

1- Instalar software de virtualiación VirtualBox (instalación default, es recomendable instalar versiones 6.0.X ya que algunas funcionalidades de Vagrant podrían no ser compatibles con la última versión)
```
https://www.virtualbox.org/wiki/Downloads
```
2- Instalar software de aprovisionamiento Vagrant (instalación default)
```
https://www.vagrantup.com/
```
3- Descargar este repositorio git localmente. Dos opciones:

a. Puede recurrirse a la utilidad git (si está instalada en su Sistema Operativo)
```
git clone https://github.com/celagus/taller-devsecops-intro.git
```
b. Puede descargarse el repositorio a través de la interfaz gráfica web de github clickeando el botón verde "Clone or 
Download" (bajará un archivo ".zip" comprimido que debe descomprimirse posteriormente)

En el siguiente directorio encontrarán los instructivos para llevar a cabo los pasos anteriores (SO Windows):
```
https://github.com/celagus/taller-devsecops-intro/tree/master/Instructivos%20Windows
```

## Antes de empezar:

Si usted es usuario de Windows:
Para asegurar que la virtualización funcione es necesario que NO esté habilitado el componente Hyper-v.
Para desactivar Hyper-v en Windows debe abrir una consola de PowerShell con permisos de administrador y ejecutar el siguiente comando:
```powershell
Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
```

## Setup del Lab:

1. Abrir una terminal de comandos o CLI del Sistema Operativo (si usted es usuario de Windows presione las tecla “Windows” + r, escribir “powershell”, luego Enter o click en "Ok").
2. Acceda al repositorio previamente descargado utilizando el comando "cd" (compatible tanto SO Windows como Linux) e indicando la ruta del directorio. Ej.: "cd /rutadeldirectorio/taller-devsecops-intro".
3. Dentro del directorio encontrará la carpeta "vm-vagrant-taller" que contiene los archivos de configuración que se utilizarán para aprovisionar y configurar la VM.
4. Luego ingresar al directorio de la VM principal con el comando "cd vm-vagrant-taller" y ejecute el comando "vagrant up" para que comience el aprovisionamiento. Vagrant buscará en el repositorio el archivo de configuración inicial "Vagrantfile" y seguirá las instrucciones previamente escritas para aprovisionar la VM. Este proceso demorará mas tiempo la primera vez que se ejecute ya que implica descargar de la nube de Vagrant la "box/caja" base del laboratorio. Una "box/caja" de Vagrant es una mini VM preconfigurada con SO, software y dependencias que puede aprovisionarse directamente sobre un hipervisor como Virtualbox, en este caso.
5. Sobre el final del aprovisionamiento puede ocurrir que encuentre el siguiente mensaje. Esto significa que Vagrant no puede conectar con el host por medio de las claves públicas que cree tomar como válidas. Esto no es importante porque en este caso ingresaremos igual a la VM con el método tradicional de usuario+password (vagrant+vagrant), por lo tanto córtelo presionando CTRL+C:
```
    default: SSH username: vagrant
    default: SSH auth method: private key
    default: Warning: Connection aborted. Retrying...
    default: Warning: Connection aborted. Retrying...
    [...]
```
6. Finalizado el aprovisionamiento podrá ver con el comando "vagrant global-status" las VM's creadas y el ID asignado a cada una.
```
    id       name    provider   state    directory
    --------------------------------------------------------------------------------------------------------------------
    4462282  default virtualbox poweroff D:/taller-devsecops-intro/vm-vagrant-taller
```

## Interacción con la VM

1. Utilice el comando "vagrant ssh ID" (reemplace "ID" por el que corresponde a las VM)
2. Ingrese el usuario "vagrant" y la pass "vagrant" 

## Finalización y desaprovisionamiento del Lab

1. Salga de las VM con el comando "exit"  --> esto aborta la sesión SSH
2. Ejecute el comando "vagrant halt ID" (reemplace "ID" por el que corresponde a las VM) --> esto interrumpe la ejecución de la VM
3. Ejecute el comando "vagrant destroy ID" (reemplace "ID" por el que corresponde a las VM) --> esto desaprovisiona la VM, es decir, elimina el hardware virtual asignado

## Opcional

Para aquellas personas que quieran extender el lab incorporando al pipeline una herramienta de registro y gestión de incidentes, puede levantar la VM que se encuentra en el directorio "vm-vagrant-ubuntu-jira" con el mismo procedimiento mencionado anteriormente. Para ello debe disponer de al menos 2GB RAM y 20GB HD extra a los ya consumidos por la VM principal del lab.
