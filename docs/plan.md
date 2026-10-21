# Plan de trabajo

## Fase 0: Preparación
- [x] Identificar el reloj (SM-R815U, Tizen 5.5, firmware DVH1)
- [x] Identificar el teléfono (Pixel 10 Pro XL, Android 17)
- [ ] Activar Opciones de desarrollador + Depuración USB en el Pixel
- [ ] Instalar `platform-tools` (ADB) en Windows y verificar `adb devices`

## Fase 1: Ruta A (sideload)
- [ ] Investigar qué versiones de las 3 apps fueron las últimas en soportar Tizen en teléfonos no-Samsung
  - Galaxy Wearable (`com.samsung.android.app.watchmanager`)
  - Galaxy Watch Plugin (`com.samsung.android.geargplugin`)
  - Samsung Accessory Service (`com.samsung.accessory`)
- [ ] Descargar de fuente confiable y registrar versión + SHA-256 en `docs/apks.md`
- [ ] Instalar con `adb install --bypass-low-target-sdk-block` (Android 14+ bloquea apps con targetSdk antiguo)
- [ ] Desinstalar o congelar la versión nueva de Galaxy Wearable si se pelea con la vieja
- [ ] Intentar vincular → documentar cada error con captura y `adb logcat`
- [ ] Probar objetivos: notificaciones → salud → llamadas → carátulas

## Fase 2: Ruta B (si A falla)
- [ ] Decompilar con apktool o jadx y localizar el chequeo de compatibilidad
- [ ] Parchear, firmar y probar

## Fase 3: Ruta C (si A y B fallan, o como proyecto open source)
- [ ] Investigar el protocolo SAP (Samsung Accessory Protocol) y proyectos previos
- [ ] Prototipo: conexión RFCOMM + handshake

## Carátulas
- [ ] Activar modo desarrollador en el reloj (tocar varias veces la versión de software)
- [ ] Probar conexión `sdb` por Wi-Fi desde Tizen Studio
- [ ] Instalar una carátula de prueba

## Preguntas abiertas
- ¿Samsung Health en Android 17 todavía acepta datos de relojes Tizen?
- ¿La tienda de Tizen sigue en línea para carátulas?
- ¿Las llamadas funcionan solo con el perfil Bluetooth estándar (HFP), sin las apps de Samsung?
