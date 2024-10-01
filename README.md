# Linux

### 1. **Enlace simbolico**
Por ejemplo, si deseas crear un enlace simbólico para un archivo llamado texto.txt en el directorio /home/usuario/Documentos/, podrías hacer lo siguiente:
    
    #### ln -s /home/usuario/Documentos/texto.txt /home/usuario/EnlaceSimbolico.txt
 Este comando crea un enlace simbólico llamado EnlaceSimbolico.txt que apunta al archivo texto.txt. Si luego accedes o editas el enlace simbólico, en realidad estarás trabajando con el archivo original.

### 1. **Entrada - Salida y Error estándar**

#### 1. Redirección de flujo: `>`, `>>`, `1>`, `2>`
Los operadores de redirección permiten enviar la salida o los errores de un comando hacia archivos en lugar de mostrarlos directamente en pantalla.

- `>` o `1>` (Redirección de salida estándar): Redirige la salida estándar de un comando hacia un archivo. Si el archivo ya existe, lo sobrescribe.

    **Ejemplo:**
    ```bash
    ls > listado.txt
    ```
    Aquí, el comando `ls` lista los archivos del directorio y guarda los resultados en el archivo `listado.txt`. Si el archivo ya existe, será sobrescrito.

- `>>` (Redirección con agregar): Añade la nueva salida al final de un archivo existente, en lugar de sobrescribirlo.

    **Ejemplo:**
    ```bash
    echo "Nueva línea" >> listado.txt
    ```
    Esto agregará "Nueva línea" al final del archivo `listado.txt` sin eliminar el contenido previo.

- `2>` (Redirección de error estándar): Redirige los mensajes de error de un comando hacia un archivo.

    **Ejemplo:**
    ```bash
    ls archivo_no_existe.txt 2> errores.txt
    ```
    Aquí, el comando `ls` intentará listar un archivo que no existe, y el error se guardará en el archivo `errores.txt`.

#### 2. Redirección `>>` (Agregar al final)
Este operador es útil cuando no quieres sobrescribir el contenido de un archivo. Usa `>>` para agregar contenido nuevo al final del archivo existente, en lugar de reemplazarlo.

**Ejemplo:**
```bash
echo "Otra línea" >> listado.txt

### 3. `2>&1` (Redirigir errores al mismo archivo que la salida)
Este comando combina los flujos de error estándar y salida estándar, redirigiendo los errores (stderr) al mismo lugar donde se envía la salida (stdout).

- `2>`: Redirige el error.
- `&1`: Especifica que el destino del error debe ser el mismo que el de la salida estándar.

**Ejemplo:**
```bash
ls archivo_no_existe.txt > salida.txt 2>&1

### 4. Redirección de entrada estándar `0<` o `<`
Este tipo de redirección se usa para dar entrada a un comando desde un archivo en lugar de desde el teclado.

- `<` o `0<`: Redirige la entrada estándar desde un archivo.

**Ejemplo:**
```bash
cat < fichero.txt

### 5. Redirección combinada
La redirección combinada te permite manejar tanto la salida como los errores de un comando de forma independiente o combinada.

#### Redirigir la salida estándar a un archivo y el error a otro archivo
```bash
ls archivo_no_existe.txt > salida.txt 2> errores.txt


### 2. **Navegación por el sistema de archivos**

#### `pwd` (Print Working Directory)
Este comando te muestra en qué directorio estás actualmente.

```bash
pwd
```
Ejemplo de salida:
```
/home/federico
```

#### `ls` (List)
Muestra el contenido de un directorio.

```bash
ls
```
Si quieres ver más detalles (como permisos, propietario, tamaño, fecha de modificación), usa `-l` (opción larga):
```bash
ls -l
```

Para mostrar archivos ocultos, usa `-a` (all):
```bash
ls -a
```

#### `cd` (Change Directory)
Te permite moverte entre directorios.

```bash
cd /ruta/del/directorio
```
Ejemplos:
```bash
cd /home/federico  # Cambia al directorio /home/federico
cd ..              # Sube un nivel en el sistema de archivos
cd                 # Vuelve al directorio personal (/home/usuario)
```

### 3. **Gestión de archivos y directorios**

#### `touch`
Crea un archivo vacío nuevo o actualiza la fecha de modificación si ya existe.

```bash
touch nombrearchivo.txt
```

#### `mkdir` (Make Directory)
Crea un nuevo directorio.

```bash
mkdir nuevodirectorio
```

#### `cp` (Copy)
Copia archivos o directorios. Si quieres copiar un archivo:
```bash
cp archivo.txt /ruta/destino
```
Para copiar un directorio y su contenido, usa `-r` (recursivo):
```bash
cp -r directorio /ruta/destino
```

#### `mv` (Move)
Mueve o renombra archivos y directorios.

```bash
mv archivo.txt /ruta/destino   # Mueve archivo.txt a otro lugar
mv archivo.txt nuevonombre.txt # Renombra archivo.txt
```

#### `rm` (Remove)
Elimina archivos. **Ten cuidado** al usar este comando, ya que elimina de manera permanente.

```bash
rm archivo.txt
```
Si quieres eliminar un directorio y todo su contenido, usa `-r` (recursivo):
```bash
rm -r directorio
```

#### `cat` (Concatenate)
Muestra el contenido de un archivo en la terminal.

```bash
cat archivo.txt
```

#### `nano` o `vi`
Son editores de texto en la terminal. `nano` es más fácil para principiantes.

```bash
nano archivo.txt  # Abre un archivo para editar con nano
vi archivo.txt    # Abre un archivo para editar con vi
```

### 4. **Permisos y propietarios**

#### `chmod` (Change Mode)
Cambia los permisos de un archivo o directorio.

```bash
chmod 755 archivo.sh
```
El número representa los permisos: `7` (lectura, escritura, ejecución), `5` (lectura, ejecución).

#### `chown` (Change Owner)
Cambia el propietario de un archivo o directorio.

```bash
sudo chown nuevo_dueño archivo.txt
```

### 5. **Visualización de procesos y uso del sistema**

#### `ps`
Muestra una lista de los procesos que están ejecutándose.

```bash
ps
```
Para ver todos los procesos en el sistema (no solo los tuyos):
```bash
ps aux
```

#### `top`
Muestra los procesos en ejecución y el uso de la CPU/memoria en tiempo real.

```bash
top
```

#### `kill`
Mata (finaliza) un proceso por su ID (PID).

```bash
kill 1234
```
También puedes matar un proceso con más fuerza usando `-9`:
```bash
kill -9 1234
```

### 6. **Comandos de red**

#### `ping`
Verifica la conectividad con una red o sitio.

```bash
ping www.google.com
```

#### `ifconfig` o `ip a`
Muestra la configuración de red y direcciones IP.

```bash
ifconfig
```

En sistemas modernos se usa más `ip a`:
```bash
ip a
```

#### `wget`
Descarga archivos desde internet.

```bash
wget https://example.com/archivo.zip
```

### 6. **Utilidades del sistema**

#### `df`
Muestra el espacio libre en los discos.

```bash
df -h  # La opción -h muestra el tamaño en formato legible (human-readable)
```

#### `du` (Disk Usage)
Muestra el uso del espacio en disco de archivos y directorios.

```bash
du -h archivo.txt
du -h --max-depth=1  # Muestra el tamaño de los directorios dentro de la carpeta actual
```

#### `free`
Muestra la cantidad de memoria libre y utilizada en el sistema.

```bash
free -h
```

### 7. **Superusuario**

#### `sudo`
Permite ejecutar comandos con privilegios de superusuario. En Linux, muchos cambios en el sistema requieren permisos de administrador. Para hacer esto, antepones `sudo` al comando.

```bash
sudo apt update  # Actualiza la lista de paquetes en sistemas basados en Debian/Ubuntu
```

### 8. **Sistema de paquetes (Ubuntu/Debian)**

#### `apt`
Gestor de paquetes en sistemas basados en Debian (como Ubuntu). Te permite instalar, actualizar o eliminar programas.

```bash
sudo apt update          # Actualiza la lista de paquetes disponibles
sudo apt upgrade         # Actualiza los paquetes instalados
sudo apt install nombre  # Instala un programa
sudo apt remove nombre   # Elimina un programa
```

### 9. **Comandos de ayuda**

Información sobre el sistema operativo, incluyendo el nombre del kernel, la versión y la arquitectura del sistema.
```bash
uname -a
```

#### `man` (Manual)
Muestra la documentación de un comando. Es muy útil para obtener más información sobre cómo usar cualquier comando.

```bash
man ls  # Muestra el manual del comando ls
```

#### `--help`
Otra forma rápida de obtener información sobre un comando.

```bash
ls --help
```

---


