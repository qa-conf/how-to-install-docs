# Guía de Instalación y Configuración de Gradle

## Descripción
Gradle es una herramienta de automatización de tareas que permite la construcción, prueba y despliegue de aplicaciones en diversos lenguajes de programación. Se destaca por su flexibilidad y rendimiento.

---

## Instalación en Windows

### 1. Descargar Gradle
Descarga la última versión binaria de Gradle desde el sitio oficial:
[https://gradle.org/](https://gradle.org/)
- Da Click en **Install Gradle 8.x.x**
- Selecciona **Install Manually**
- Elige **Binary-only**

### 2. Extraer y Mover a una Ubicación Permanente
- Extrae el archivo ZIP en una ubicación permanente, por ejemplo: `C:\tools\gradle`.

### 3. Configurar Variables de Entorno
1. Abre **Configuración avanzada del sistema**:
   - Presiona `Win + R`, escribe `sysdm.cpl` y presiona `Enter`.
   - Ve a la pestaña **Opciones avanzadas** y haz clic en **Variables de entorno**.
2. En **Variables del sistema**, y agrega una variable global asi
```
GRADLE_HOME
C:\RUTA\gradle
```
3. Luego de guardar la variable anterior, selecciona **Path** y haz clic en **Editar**.

3. Agrega la ruta de `bin` de Gradle, por ejemplo:
   ```
   %GRADLE_HOME%\bin
   ```
---

## Instalación en macOS

### Opción 1: Instalación con Homebrew (Recomendada)
1. Abre una terminal y ejecuta:
   ```sh
   brew install gradle
   ```
2. Verifica la instalación con:
   ```sh
   gradle -v
   ```
---

## Verificar Instalación
Abre una terminal (cmd o PowerShell) y ejecuta:
```sh
gradle -v
```
Si la instalación fue exitosa, verás la versión de Gradle instalada.


