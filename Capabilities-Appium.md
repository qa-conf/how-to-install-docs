# Capabilities en Appium

## ¿Qué son las Capabilities?

Las **desired capabilities** en Appium son un conjunto de parámetros clave-valor que se utilizan para configurar la sesión de automatización. Estas capacidades le indican al servidor de Appium qué tipo de dispositivo o emulador se va a utilizar, qué sistema operativo tiene, qué app abrir, entre otros detalles importantes.

Algunas capabilities son obligatorias (como `platformName` y `deviceName`) y otras son opcionales dependiendo del contexto. Se pueden clasificar en varias categorías:

- **Generales:** Aplican tanto para Android como iOS.
- **Específicas de Android:** Solo se usan para dispositivos o emuladores Android.
- **Específicas de iOS:** Solo aplican para dispositivos o simuladores iOS.
- **App-related:** Relacionadas con la aplicación a probar.
- **Sesión / Estado:** Configuran el comportamiento de la sesión, como `noReset`.

---

## 📱 Android Físico

```json
{
  "appium:platformName": "Android",
  "appium:deviceName": "ID-DISPOSITIVO",
  "appium:platformVersion": "VERSION",
  "appium:appPackage": "com.XXX",
  "appium:appActivity": "com.XXX.XYZ.HomeActivity",
  "appium:noReset": true,
  "appium:automationName": "UiAutomator2"
}
```

## 📱 Android Emulador

```json
{
  "appium:platformName": "Android",
  "appium:deviceName": "EMULATOR-ID",
  "appium:platformVersion": "VERSION",
  "appium:appPackage": "com.XXX",
  "appium:appActivity": "com.XXX.XYZ.HomeActivity",
  "appium:noReset": true,
  "appium:automationName": "UiAutomator2"
}
```

---

## 🍎 iOS Físico

```json
{
  "appium:platformName": "iOS",
  "appium:deviceName": "iPhone 12 Pro Max",
  "appium:platformVersion": "VERSION",
  "appium:udid": "ID-DISPOSITIVO",
  "appium:automationName": "XCUITest",
  "appium:xcodeSigningId": "iPhone Developer",
  "appium:bundleId": "com.XXX.XYZ",
  "appium:showXcodeLog": true,
  "appium:noReset": true
}
```

## 🍎 iOS Emulador

```json
{
  "appium:platformName": "iOS",
  "appium:deviceName": "iPhone 16 Pro Max",
  "appium:platformVersion": "VERSION",
  "appium:udid": "ID-DISPOSITIVO",
  "appium:automationName": "XCUITest",
  "appium:xcodeSigningId": "iPhone Developer",
  "appium:bundleId": "com.XXX.XYZ",
  "appium:showXcodeLog": true,
  "appium:noReset": true
}
```
