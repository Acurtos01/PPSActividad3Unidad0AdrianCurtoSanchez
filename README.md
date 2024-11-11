# Unidad 0 - Actividad 3ra5. Git

1. Crear cuenta en GitHub
2. Instalar GIT en nuestro equipo
3. Enlazar cuenta de GitHub con nuestro equipo mediante SSH
4. Comprobar la conexión con GitHub
5. Inicializar un repositorio en nuestro equipo
6. Subir repositorio a GitHub 
7. Agregar nuevos cambios


## Crear cuenta en GItHub
Accedemos a [GitHub](https://github.com/signup) para crear una cuenta en la plataforma.

Una vez creada veremos un dashboard como este:
![GitHub dashboard](./images/github_dashboard.png)

## Instalar GIT en nuestro equipo
Comenzamos actualizando los repositorios con el comando `sudo apt update`, continuamos ejecutando `sudo apt install git`. Una vez instalado podemos comprobar su instalación con el comando `git --version` y nos mostrará la versión instalada como se muestra a continuación:

![git version](./images/gitversion.png)

Ahora configuraremos git para que los commits que realicemos están asociados a nuestros datos. Deberemos ejecutar los comandos `git config --global user.name "Adrián Cruto Sánchez"` y `git config --global user.email "acurtos01@iesvjp.es"`.
Comprobaremos que se han actulizados los datos con el comando `git config --list`:

![git config](./images/gitconfig.png)


## Enlazar cuenta de GitHub con nuestro equipo mediante SSH
Ahora procedemos a enlazar la cuenta de GitHub con nuestro equipo mediante ssh. Para ello usaremos la guia que nos oferce GitHub en su [documentación](https://docs.github.com/es/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

Abrimos la terminal y ejecutamos el comando `ssh-keygen -t ed25519 -C "your_email@example.com"
` para generar una clave SSH:

![ssh-keygen](./images/ssh_keygen.png)

En los pasos en los que nos pide que ingresemos un fichero en el que guardar la clave lo omitimos pulsando enter y lo guadará en el fichero por defecto. Para crear la clave tambien pide que intoduzcamos una frase, no es necesario solo es para dar más seguridad, pulsamos enter y termina el proceso de creación de la clave.

Si nos dirigimos a la ruta que nos indica al generar la calve `/home/kali/.ssh` podremos ver que ha generado el fichero `id_ed25519.pub`.

![ssh key folder](./images/ssh_key_folder.png)

Ahora que hemos localizado donde se encuentra la clave tendremos que copiarla, para mostrarla usaremos el comando `cat id_ed25519.pub`(*la clave se muestra cortada por motivos de seguridad*):

![ssh key](./images/ssh_key.png)

Nos dirigimos a la configuración de GitHub, accedemos a dicha configuración pinchando en la esquina superior derecha de cualquier página en GitHub, haciendo clic en la fotografía de perfil y luego en Configuración. 

![GitHub settings](./images/github_settings.png)

En la sección "Acceso" de la barra lateral, haz clic en Claves SSH y GPG.

![GitHub settings access](./images/github_settings_access.png)

Pinchamos en Nueva clave SSH o en Agregar clave SSH.

![GitHub new ssh key](./images/github_newsshkey.png)

Indicamos un titulo para poder identificar el equipo al que pertenece la clave SSH. Y pegamos la clave en el campo "Clave". Y pinchamos en Agregar clave SSH.

![GitHub add ssh key](./images/github_add_shhkey.png)

Tras agregar la clave podemos ver que GitHub nos lista la conexión.

![GitHub SSH key added](./images/github_ssh_key_agregada.png)

## Comprobar la conexión con GitHub

Abrimos la terminal y lanzamos el comando `ssh -T git@github.com`, cuando nos pregunte si deseamos continuar con la conexión le indicamos que si escribiento "yes" y presionado enter. Si se han seguido bien los pasos anteriores nos montrará un mensaje de confirmación conferme hemos establecido una conexión satisfactoria.

![GitHub check conection](./images/github_check_conection.png)

## Inicializar un repositorio en nuestro equipo

Inicializamos el respositorio en nuestro equipo con el comando `git init`.

![Git init](./images/git_init.png)

Ahora que se ha incializado el seguimiento de nuestro directorio agragamos los ficheros con `git add .`

![Git add](./images/git_add.png)

Y creamos el primer commit de nuestro directorio con los fireros e indicamos un texto descriptivo `git commit -m "Primer commit"`.

![Git commit](./images/git_commit.png)

## Subir repositorio a GitHub 

Vamos a la ventana principal de nuestro GitHub y en el apartado de "Comenzar un nuevo repositorio" rellenamos el nombre del nuevo repositorio, indicamos si queremos que sea público o privado(en este caso público) y pinchamos en el botón de "Crear nuevo repositorio".

![Create new repository](./images/create_new_repository.png)

Nos redirige a una página donde nos indica los pasos a seguir, donde deberemos selecciona el tipo de conexión dandonos a elegir entre el protocolo HTTP y SSH, como nosotros ya tenemos configurada la conexión SSH será la que elijamos.

![Quick setup](./images/quick_setup.png)

Continuamos siguiendo los pasos de "...o subir un repositorio existente desde la terminal de comandos", simplemente deberemos ejecutar los comandos que nos indica:

```
git remote add origin git@github.com:Acurtos01/PPSActividad3Unidad0AdrianCurtoSanchez.git
git branch -M main
git push -u origin main
```
![Connect local with remote](./images/conect_local_with_remote.png)

Como podemos ver ha subido los datos locales al repositorio remoto de forma satisfactoria. Si volvemos a GitHub podremos ver nuestro nuevo repositorio.

![Repository created](./images/repository_created.png)

## 7. Agregar nuevos cambios

Aprovechamos que durante la creación de este manual se han creado nuevos cambios en el repositorio para explicar como se agregan y suben al repositorio.

Agregamos los cambios a git ejecutando de nuevo el comando `git add .` y volvemos a crear un commit con los nuevos cambios `git commit -m "Manual completado"` y subimos los cambios con el comando `git push`.

![Push last commit](./images/push_last_commit.png)

- Nota: para conocer el estado actual de nuestro repositorio y obtener ayuda de como continuar podemos utilizar el comando `git status`.