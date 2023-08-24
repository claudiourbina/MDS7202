# Lab01: `git`

`MDS7202`: Laboratorio de Programación Científica para Ciencia de Datos - Primavera 2023

##### Integrantes:
- Claudio Urbina | [Repositorio](https://github.com/claudiourbina/MDS7202) | claudio.urbina@ug.uchile.cl

## Parte 1: Conocimiento Teorico

### 1.a. Preguntas conceptuales

1. **¿Qué es `Git` y cómo se relaciona con el control de versiones?**

    `Git` es un sistema de control de versiones (`VCS`) distribuido, es decir, registra los cambios realizados en uno o más archivos en el tiempo, permitiendo acceder a versiones antiguas de un proyecto.

2. **Nombre y explique 3 diferencias entre `Git` y `Github`.**

    1. `Git` es un sistema de control de versiones distribuido, mientras que, `GitHub` es un servicio alojado en una plataforma web.
    2. Para utilizar `Git`, se debe hacer mediante `CLI`, mientras que, para utilizar `Github`, se debe ingresar por su interfaz gráfica en `web`/`app`.
    3. `Git` permite crear y versionar repositorios localmente, mientras que, `GitHub` permite almacenar una copia de este repositorio en sus servidores.

3. **¿Qué es un `hash` y cómo se representa en un `commit`? De un ejemplo.**

    Un `hash` es una cadena alfanumérica única que nos permite identificar un conjunto de datos. En `Git`, un `hash` puede representar un `blob`, un `tree` o un `commit`. Un `commit` captura un *snapshot* de los cambios realizados en los archivos que estan siendo *trackeados* en el repositorio, ese `commit` se representa con un `hash` único, y es posible revisar los cambios realizados en un futuro revisando un `hash` en específico.

4. **¿Que elementos componen a la estructura de datos de `Git`?**

    1. `blob`: almacena un *snapshot* del contenido de un archivo. Si el contenido es modificado, otro `blob` almacena este nuevo *snapshot*
    2. `tree`: representa directorios que contienen archivos, y por lo tanto, `blobs`. Tambien puede contener otros directorios, así que, pueden haber `trees` dentro de otros `trees`.
    3. `commit`: captura un *snapshot* de los cambios realizados en los archivos que estan siendo *trackeados* en el repositorio. Relacionando los antiguos `blobs`, con los nuevos.

5. **¿Que comandos de `Git` sirven para crear un repositorio y hacer seguimiento a cambios en los archivos?**

    Para crear un repositorio local se utiliza `git init <repository-name>`. Para hacer seguimiento de un archivo o carpeta, es necesario indicarle a `git` que archivos o carpeta debe revisar utilizando `git add <path>`.

### 1.b. Verdadero o Falso

6. **`Git` siempre resuelve automáticamente los problemas de lineas al hacer merge entre diferentes ramas.**

    **Falso**. Depende de la configuración indicada en el repositorio para el `rebase` ante conflictos. Si no existe conflictos entre las ramas, el `merge` se resuelve automáticamente, por otra parte, si existe conflicto, estos se pueden resolver manualmente (si el `rebase` es `false`) o automáticamente (si el `rebase` es `true`).

7. **Ejecutar `git pull` sobre un repositorio es equivalente a ejecutar `git clone`.**

    **Falso**. `git pull` es utilizado para actualizar el repositorio local respecto a los cambios que existen en el servidor remoto (por ejemplo: `github`), mientras que, `git clone` es utilizado para "*descargar*" un repositorio desde el servidor remoto a tu entorno local por primera vez (*no quise usar la palabra clonar, aunque, sé que descargar tampoco es la palabra adecuada*).

8. **`git status` genera los mismos resultados que `git log`.**
    **Falso**. `git status` es utilizado para listar los archivos que han sido creados/modificados/borrados en el repositorio local, mientras que, `git log` es utilizado para listar los `commits` aplicados en el repositorio.

9.  **En `Git` es posible deshacer cambios y volver a versiones anteriores del código.**

    **Verdadero**. La objetivo principal de tener un sistema de control de versiones es principalmente este, poder deshacer y volver a versiones anteriores del código.

10. **El comando `git commit` se utiliza para enviar cambios al repositorio remoto.**

    **Falso**. `git commit` es utilizado para guardar el snapshot de los cambios realizados en el repositorio, pero, es cambios no son enviados al repositorio remoto hasta aplicar `git push`.

### 1.c. Investigue

11. **¿Para que sirve `git stash`?**

    `git stash` permite guardar los cambios realizados en el repositorio local, de manera temporal. Al aplicar `git stash` los cambios *desaparecen* del repositorio local, permitiendote cambiar de contexto para hacer otros cambios, y posteriormente, volver a aplicar los cambios guardados en el `stash`.

12. **¿Para que sirve `git reset`?. ¿Cuál es la diferencia de este comando con `git revert`?**

    `git reset` permite restablecer el estado de uno o más archivos de tu repositorio a un estado específico, sobreescribiendo el historial de `commits`, mientras que, `git revert` permite restablecer el estado del repositorio a un `commit` anterior, creando un `commit` completamente **nuevo**, dejando el historial mucho más limpio y que muy posiblemente, no afecte a otros colaboradores del mismo repositorio.

## Parte 2: Presentacion Personal

- [Presentacion Personal](https://github.com/claudiourbina/claudiourbina)

## Parte 3: Repositorio Externo

1. **Clone el repositorio**

    ```sh
    git clone git@github.com:MDS7202/lab1.git
    ```

2. **Crea un `.gitignore` que omita la carpeta `videos` y los archivos con la extension `.txt` exceptuando el archivo `171.txt` de la carpeta `texts`.**

    ```sh
    # .gitignore
    videos/
    texts/*.txt
    !texts/171.txt
    ```

3. **Cual es el objetivo del proyecto?. Explique la estructura del proyecto y los elementos que lo conforman.**

    El objetivo del proyecto es imprimir el sonido que hace el animal por el que se le consulta. La estructura es la siguiente:
    ```text
    .
    └── lab1/
        ├── main.py # interfaz que recibe la consulta
        ├── animales.py # contiene el sonido de los animales a consultar
        └── readme.md # deberia contener la información del repositorio
    ```

4. **Identifique los últimos cambios al repositorio, reconociendo las principales ramas de trabajo. ¿Son informativos los `commit` realizados?**

    Existen tres ramas: `main`, `new_features`, `fix-ifs`. Se podría decir que son algo informativos ya que indican de manera general cuales son los cambios realizados.

5. **Uno de los académicos se da cuenta que la rama principal de trabajo no se ejecuta correctamente para todos los argumentos. Señale y explique el error en el código e identifique a la persona que lo cometió usando `git blame`.**

    El error es que, en el archivo` animales.py`, el *statment* `else` aplica solo sobre el último `if` y no para todas las condiciones. Al ejecutar `git blame animales.py` se puede observar que el archivo completo fue realizado por el usuario `mezosky`.

6. **Busque los siguientes `commit`. ¿Qué diferencias existen entre cada uno?**
   
   1. `c8b1a62d7299552b0654f930d695b33109214111`: Agrega la función `animales` al archivo `main.py`.
   2. `362fe21ee44f53ee944cee4ba484600308f83d78`: Separa la función `animales` en un módulo nuevo llamado `animales.py`.
   3. `25543a3baf77292baf849726784ca005473acab1`: Corrige el error de los `ifs` que habia en la función `animales` en `animales.py`
   
7. **Realice una `merge` de la rama `fix-ifs` con la rama `main` y describa lo que ocurre. ¿Qué parte del código podría estar ocasionando esto?**

    Hay un conflicto al hacer el `merge` entre ambas ramas. Básicamente, la rama `fix-ifs` tiene el mismo historial de `commits` que `main` hasta cierto punto (el penultimo `commit`, en el cual se agrega la función `animales` a `main.py`), pero, después de ese commit, ambas ramas siguieron caminos diferentes, incluyendo un `commit` distinto a su historial. Por su parte, la rama `main` separó la función `animales` en un módulo distinto llamado `animales.py`, mientras que, la rama `fix-ifs` arregló el problema de los `ifs` en la misma función que existia en `main.py` (sin la separación de modulos). Esta inconsistencia entre ambos historiales no permite que el `merge` se haga de manera natural, teniendo que resolver el conflicto de manera manual.

8. **Cree una rama nueva y proponga una solución al problema anterior, adjuntando el código corregido y señalando las líneas modificadas.**

    Se clona el repositorio y se crea una rama para solucionar el problema.

    ```sh
    git clone git@github.com:MDS7202/lab1.git
    git checkout main
    git checkout -b bugfix/if-statments
    ```

    Se modifica el archivo `animals.py` quedando de esta manera.

    ```py
    def animales(input):
    
        '''
        Como hace el animalito?
        '''
        
        if input.lower() == 'gato':
            print('miau')
        elif input.lower() == 'perro':
            print('guau')
        elif input.lower() == 'fox':
            print('https://www.youtube.com/watch?v=jofNR_WkoCE')
        else:
            raise ValueError('animal no reconocido :(')
    ```

    Se agregan las modificaciones al seguimiento y a un `commit`. Finalmente, se pushea la rama (que de momento solo existe de manera local) al repositorio remoto.

    ```sh
    git add animals.py
    git commit -m "fixed if statments"
    git push --set-upstream origin bugfix/if-statements
    ```

    Luego, se debe hacer el merge con la rama `main` para aplicar estos cambios en la rama. Esto, trae los `commits` a la rama main en el repositorio local, luego hay que mandarlos al repositorio remoto.

    ```sh
    git checkout main
    git pull
    git merge bugfix/if-statments
    git push
    ```
