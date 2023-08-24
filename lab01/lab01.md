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

    **Falso**. `git pull` es utilizado para actualizar el repositorio local respecto a los cambios que existen en el servidor (por ejemplo: `github`), mientras que, `git clone` es utilizado para "*descargar*" un repositorio desde el servidor a tu entorno local por primera vez (*no quise usar la palabra clonar, aunque, sé que descargar tampoco es la palabra adecuada*).

8. **`git status` genera los mismos resultados que `git log`.**

    **Falso**. `git status` es utilizado para listar los archivos que han sido creados/modificados/borrados en el repositorio local, mientras que, `git log` es utilizado para listar los commits aplicados en el repositorio.

9.  **En `Git` es posible deshacer cambios y volver a versiones anteriores del código.**

    ...

10. **El comando `git commit` se utiliza para enviar cambios al repositorio remoto.**

    ...

### 1.c. Investigue

11. **¿Para que sirve `git stash`?**

    ...

12. **¿Para que sirve `git reset`?. ¿Cuál es la diferencia de este comando con `git revert`?**

    ...

## Parte 2: Presentacion Personal

- [Presentacion Personal](https://github.com/claudiourbina/claudiourbina)

## Parte 3: Repositorio Externo

1. **Clone el repositorio**

    `git clone https://github.com/MDS7202/lab1.git`

2. **Crea un `.gitignore` que omita la carpeta `videos` y los archivos con la extension `.txt` exceptuando el archivo `171.txt` de la carpeta `texts`.**

    ```
    # .gitignore
    videos/
    texts/*.txt
    !texts/171.txt
    ```

3. **Cual es el objetivo del proyecto?. Explique la estructura del proyecto y los elementos que lo conforman.**

    ...
4. **Identifique los últimos cambios al repositorio, reconociendo las principales ramas de trabajo. ¿Son informativos los `commit` realizados?**

    ...
5. **Uno de los académicos se da cuenta que la rama principal de trabajo no se ejecuta correctamente para todos los argumentos. Señale y explique el error en el código e identifique a la persona que lo cometió usando `git blame`.**

    ...
6. **Busque los siguientes `commit`. ¿Qué diferencias existen entre cada uno?**
   1. `c8b1a62d7299552b0654f930d695b33109214111`
   2. `362fe21ee44f53ee944cee4ba484600308f83d78`
   3. `25543a3baf77292baf849726784ca005473acab1`

    ...
7. **Realice una `merge` de la rama `fix-ifs` con la rama `main` y describa lo que ocurre. ¿Qué parte del código podría estar ocasionando esto?**

    ...
8. **Cree una rama nueva y proponga una solución al problema anterior, adjuntando el código corregido y señalando las líneas modificadas.**

    ...