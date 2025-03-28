# Guía de Instalación de JDK 17

## Descripción
El **Java Development Kit (JDK)** es un conjunto de herramientas necesarias para desarrollar y ejecutar aplicaciones Java. Esta guía explica cómo instalar la versión 17 de JDK en Windows y macOS.

---

## Instalación en Windows

### 1. Descargar JDK 17
- Descarga el instalador desde el sitio oficial de Oracle o utiliza una distribución OpenJDK:
  - [Oracle JDK 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
  - [OpenJDK 17](https://jdk.java.net/17/)

### 2. Instalar JDK
1. Ejecuta el instalador `.exe` descargado.
2. Sigue las instrucciones del asistente de instalación.
3. El instalador configurará automáticamente las variables de entorno.

### 3. Configurar Variables de Entorno

1. Abre **Configuración avanzada del sistema** (`Win + R`, escribe `sysdm.cpl` y presiona `Enter`).
2. Ve a **Opciones avanzadas > Variables de entorno**.
3. Crea una nueva variable llamada `JAVA_HOME` con la ruta del JDK:
   ```
   JAVA_HOME
   C:\Program Files\Java\jdk-17
   ```
4. En **Variables del sistema**, edita la variable `Path` y agrega la ruta de `bin` del JDK, por ejemplo:
   ```
 %JAVA_HOME%\bin
   ```

---

## Instalación en macOS

### Opción 1: Instalación con Homebrew (Recomendada)
1. Abre una terminal y ejecuta:
   ```sh
   brew install openjdk@17
   ```
2. Agrega OpenJDK al `PATH`:
   ```sh
   echo 'export PATH="/opt/homebrew/opt/openjdk@17/bin:$PATH"' >> ~/.zshrc
   echo 'export JAVA_HOME="$(/usr/libexec/java_home -v 17)"' >> ~/.zshrc
   source ~/.zshrc
   ```
---



## Verificar Instalación

Abre una terminal (`cmd` o `PowerShell`) y ejecuta:
```sh
java -version
```
Si la instalación fue exitosa, verás la versión 17 de Java.

