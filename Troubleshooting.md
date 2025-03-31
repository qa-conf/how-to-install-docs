# Troubleshooting General

Esta guía sirve para encontrar solución a posibles errores que se pueden presentar al momento de configurar diferentes herramientas o su ejecución.

**Nota**: Si la solución a tu pregunta no está aquí, por favor crea un issue en el repositorio y con gusto te ayudaremos a resolverlo.

## Tabla de Contenido

- [Appium](#appium)
  - [Error `xcodebuild failed with code 70` o `xcodebuild failed with code 65`](#error-xcodebuild-failed-with-code-70-o-xcodebuild-failed-with-code-65)
- [Xcode](#xcode)
  - [Sign & Capabilities no tiene un Team asignado](#sign--capabilities-no-tiene-un-team-asignado)
  - [Failed Registering Bundle Identifier](#failed-registering-bundle-identifier)
- [Dispositivos](#dispositivos)
  - [iPhone físico está configurado como no confiable](#iphone-fisico-esta-configurado-como-no-confiable)

---

## Appium

### Error `xcodebuild failed with code 70` o `xcodebuild failed with code 65`

#### Verificar permisos y perfiles de firma

1. Abre **Xcode** → **Settings** → **Accounts**.
2. Asegúrate de que tu Apple ID está registrado y asociado a un perfil de desarrollo.
3. Ve a **Xcode** → **Preferences** → **Locations** y asegúrate de que la versión correcta de Xcode está seleccionada.
4. En **Signing & Capabilities**, selecciona tu equipo de desarrollo en **WebDriverAgentRunner** y **WebDriverAgentLib**.

#### Verificar la instalación de `iproxy` y `usbmuxd`

```sh
brew install usbmuxd
brew install libimobiledevice
brew install ideviceinstaller
brew install ios-deploy
brew install carthage
```

#### Verificar la licencia está OK

```sh
sudo xcodebuild -license accept
```

#### Eliminar y reinstalar los paquetes en WebDriverAgent

```sh
cd /Users/USUARIO-REEMPLAZAR/.appium/node_modules/appium-xcuitest-driver/node_modules/appium-webdriveragent
rm -rf Carthage
mkdir -p Resources/WebDriverAgent.bundle
./Scripts/bootstrap.sh -d
```

#### Lanzar manualmente WebDriverAgent habilitando la creación automática de perfiles

Reemplaza `ID-DEL-DISPOSITIVO-REAL` por el ID de tu dispositivo.

```sh
xcodebuild -project /Users/USUARIO-REEMPLAZAR/.appium/node_modules/appium-xcuitest-driver/node_modules/appium-webdriveragent/WebDriverAgent.xcodeproj \
-scheme WebDriverAgentRunner \
-destination 'id=ID-DEL-DISPOSITIVO-REAL' \
-allowProvisioningUpdates \
clean test
```

Intenta lanzar nuevamente Appium y verifica si el dispositivo conecta la aplicación con el Inspector correctamente.

---

## Xcode

### Sign & Capabilities no tiene un Team asignado

Abre el proyecto.

```sh
cd /usr/local/lib/node_modules/appium/node_modules/appium-webdriveragent
open WebDriverAgent.xcodeproj
```

1. Selecciona tu dispositivo real en la barra superior de Xcode.
2. Ve a **Signing & Capabilities** y asigna un Apple ID válido como Team o con tu cuenta personal.
3. Intenta compilar el proyecto con **CMD + B** y revisa si hay errores.
4. En la pestaña de **Signing & Capabilities**, activa la opción **Automatically manage signing** y asigna un equipo de desarrollo válido en `WebDriverAgentLib` y `WebDriverAgentRunner`.
5. Si aún no tienes una cuenta:
   - En el campo "Team", selecciona tu cuenta de Apple.
   - Pulsa en "Add Account".
   - Inicia sesión con tu Apple ID.
6. Si tienes una cuenta gratuita, Xcode generará automáticamente un perfil de firma para tu dispositivo.
7. Si tienes cuenta gratuita, solo puedes usar la app en tu iPhone por 7 días antes de necesitar volver a firmarla.
8. Dale clic en **Product** → **Clean Build Folder**.
9. Luego **Product** → **Build**.
10. Finaliza con **Product** → **Test**.

Esto debería instalar **IntegrationApp** y el **WebDriverAgent** en tu dispositivo físico.

---

### Failed Registering Bundle Identifier

Si ves este error al ejecutar WebDriverAgent:

```sh
Failed Registering Bundle Identifier
The app identifier "com.facebook.IntegrationApp"
```

En el proyecto de Xcode para el **WebDriverAgent**, **WebDriverAgentLib** e **IntegrationApp**, cambia `facebook` por otro dato, `com.NOMBRE.IntegrationApp`.

Vuelve a construir el proyecto:

1. **Product** → **Clean Build Folder**.
2. Luego **Product** → **Build**.
3. **Product** → **Test**.

---

## Dispositivos

### iPhone físico está configurado como no confiable

Para esto, verifica que el **Modo Desarrollador** está habilitado.

1. Ve a **Ajustes** → **General** → **Transferir o Restablecer iPhone**.
2. Selecciona **Restablecer**.
3. Selecciona **Restablecer Localización y Privacidad**.
4. Sigue los pasos recomendados por el sistema operativo para completar el proceso.

Verifica que el **Modo de Desarrollador** está activo. Si no lo está, sigue los siguientes pasos:

1. **Ajustes** → **Privacidad y Seguridad**.
2. Ve al final y ubica **Modo de Desarrollador**. Ingresa a esta opción.
3. Habilita el **Toggle** y sigue los pasos que te sugiere el sistema operativo (te indicará reiniciar).
4. Al reiniciar, un **Splashscreen** te debe confirmar el **Modo Desarrollador**.

Luego, dirígete nuevamente a **Ajustes**:

1. **General** → **Administración de Dispositivos y VPN**.
2. Allí debe aparecer tu cuenta personal como **App del Desarrollador**.
3. Selecciónala y dale en **Confiar en "[nombre del desarrollador]"**.

Conecta el dispositivo nuevamente a tu Mac y dale **Confiar** al **Popup** que aparecerá para confiar en el dispositivo.