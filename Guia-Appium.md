# Guía de Instalación de Appium Inspector

Appium Inspector es una herramienta utilizada para inspeccionar elementos de aplicaciones móviles y facilitar la automatización de pruebas. Esta documentacion tiene las instrucciones para la instalación en macOS *(tanto en procesadores ARM como Intel)* y en *Windows*.

## Requisitos Previos
Antes de instalar Appium Inspector es importante instalar las siguientes herramientas:

- **Node.js**
- **Appium Server**
- **JDK**
- **Android SDK**
- **Xcode** *(para iOS en macOS)*

---

## Instalación en macOS (ARM & Intel)

### 1. Instalar [Homebrew](https://brew.sh/ "Homebrew")
```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2. Instalar Node.js, Appium y JDK
```sh
brew install node
brew install openjdk
export PATH="/opt/homebrew/opt/openjdk/bin:$PATH"
npm install -g appium@next
```
Verifica la instalación con:
```sh
appium -v
java -version
```

### 3. Instalar Android SDK
```sh
brew install android-platform-tools
```
Configura las variables de entorno:
```sh
echo 'export ANDROID_HOME=$HOME/Library/Android/sdk' >> ~/.zshrc
echo 'export PATH=$ANDROID_HOME/platform-tools:$PATH' >> ~/.zshrc
source ~/.zshrc
```

### 5. Instalar dependencias para iOS
```sh
brew install carthage
brew install ios-deploy
brew install libimobiledevice
npm install -g appium-doctor
```

Si usas un Mac con procesador ARM (M1/M2), instala Rosetta:
```sh
softwareupdate --install-rosetta --agree-to-license
```

### 6. Configurar Xcode (solo para iOS)
- Abre Xcode y acepta la licencia:
```sh
sudo xcode-select --switch /Applications/Xcode.app/Contents/Developer
sudo xcodebuild -runFirstLaunch
```

---

## Instalación en Windows

### 1. Instalar Node.js, Appium y JDK
Descarga e instala [Node.js](https://nodejs.org/) y [JDK](https://www.oracle.com/java/technologies/javase-downloads.html). Luego, ejecuta:
```sh
npm install -g appium@next
```
Verifica la instalación con:
```sh
appium -v
java -version
```

### 2. Instalar Android SDK
Descarga e instala [Android Studio](https://developer.android.com/studio) y asegúrate de incluir el SDK Manager.

Configura las variables de entorno:
1. Agrega `ANDROID_HOME` y `JAVA_HOME` a las variables de entorno.
2. Agrega las rutas de `platform-tools` y `tools` a la variable `Path`:
   ```sh
   C:\Android\Sdk\platform-tools
   C:\Android\Sdk\tools
   ```

## Verificar la Instalación

Ejecuta los siguientes comandos para validar que las herramientas estan todas instaladas correctamente.

```sh
appium-doctor --android
```

Verifica la configuración en iOS con:
```sh
appium-doctor --android
appium-doctor --ios
```
Deberias ver algo asi

iOS
[![https://iili.io/3Thc0dJ.png](https://iili.io/3Thc0dJ.png "https://iili.io/3Thc0dJ.png")](https://iili.io/3Thc0dJ.png "https://iili.io/3Thc0dJ.png")

Android
[![https://iili.io/3ThrOoN.png](https://iili.io/3ThrOoN.png "https://iili.io/3ThrOoN.png")](https://iili.io/3ThrOoN.png "https://iili.io/3ThrOoN.png")

---

## Ejecucion de Appium
Ejecuta Appium Server con:
```sh
appium --allow-cors
```

Deberias de ver algo asi

[![https://iili.io/3Th4Lmv.png](https://iili.io/3Th4Lmv.png "https://iili.io/3Th4Lmv.png")](https://iili.io/3Th4Lmv.png "https://iili.io/3Th4Lmv.png")

Abre Appium Inspector en el navegador [https://inspector.appiumpro.com/](https://inspector.appiumpro.com/ "https://inspector.appiumpro.com/") y esta listo para agregar los capabilities y conectar un dispositivo o emulador para inspeccionar elementos de la aplicación.

Vista Previa

[![https://iili.io/3ThPF8g.png](https://iili.io/3ThPF8g.png "https://iili.io/3ThPF8g.png")](https://iili.io/3ThPF8g.png "https://iili.io/3ThPF8g.png")

---

## Instalar Herramientas Adicionales en MacOS para Appium

Instala las siguientes herramientas

```sh
appium driver install xcuitest

```

Instala linea de comandos de Xcode

```sh
xcode-select --install
```


Verifica la lista de herramientas instaladas con 

```sh
appium driver list --installed
```