# galaxy-watch-revive ⌚

Revivir relojes Samsung con **Tizen** (Galaxy Watch 2018, Gear S3, Gear Sport…) que Samsung dejó sin soporte, para que vuelvan a funcionar con **teléfonos Android recientes que no son Samsung**.

> Estado: 🟢 **Vinculado y reconocido por Galaxy Wearable** (2026-10-20) con la ruta A. Falta probar cada función.

## ⚡ Receta rápida (lo que funcionó)

1. Desde Play Store: **Galaxy Wearable** y **Samsung Accessory Service** (versiones actuales).
2. Descargar **Galaxy Watch Plugin 2.2.05.24020151** (Play lo bloquea en Android 17) y verificar la firma de Samsung: ver [docs/apks.md](docs/apks.md).
3. Activar Depuración USB y ejecutar `adb install --bypass-low-target-sdk-block geargplugin-2.2.05.24020151.apk`
4. **En el reloj: elegir "iniciar sin vincular"** (modo independiente) y terminar su configuración básica.
5. Ya con el reloj iniciado: en Galaxy Wearable → agregar dispositivo → elegir **"Galaxy Watch (XXXX)" sin "LE"** → aceptar todos los permisos.

### Problemas conocidos
- **Vincular directo desde la pantalla de vinculación del reloj se puede trabar** en *"Finalizando vinculación…"*: el teléfono manda un mensaje por SAP y el reloj nunca contesta. Solución: iniciar el reloj sin vincular primero (paso 4).
- **Vinculación por la dirección LE**: si el teléfono se vincula con la dirección BLE del reloj, el plugin intenta RFCOMM a esa dirección y falla (`PAGE_TIMEOUT` / `SOCKET_CONNECT_FAILED`) → *"No fue posible conectarse con su reloj"*. Solución: olvidar todas las entradas "Galaxy Watch" en Ajustes → Bluetooth y vincular la entrada **sin "LE"**.
- **No vincular desde los ajustes de Bluetooth de Android**, siempre desde Galaxy Wearable.
- Si el reloj se restablece, el teléfono conserva claves viejas → olvidar el dispositivo antes de reintentar.

## El problema

El reloj aparece por Bluetooth en el teléfono, pero la versión actual de **Galaxy Wearable** ya no lo lista como compatible, así que no hay manera de vincularlo. Sin vincularlo, el reloj solo sirve en modo independiente (sin notificaciones, salud sincronizada ni llamadas).

## Equipo de prueba

| | |
|---|---|
| **Reloj** | Samsung Galaxy Watch (2018) **SM-R815U**: 42 mm, LTE, versión EE.UU. |
| Software | `R815USQU1DVH1` (parece ser ago-2022, probablemente el último) |
| Plataforma | One UI Watch 2.0 · Tizen 5.5.0.2 · Knox 2.5.0 |
| Nombre BT | `Galaxy Watch D021` |
| **Teléfono** | Google Pixel 10 Pro XL · **Android 17** |
| Equipo de trabajo | PC Windows 11 (ADB por USB) |

## Objetivos (por prioridad)

1. **Notificaciones** en el reloj
2. **Salud**: pasos, ritmo cardiaco, sueño → Samsung Health en el teléfono
3. **Llamadas**: contestar o hacer llamadas del teléfono desde el reloj
4. **Carátulas**: instalar y, más adelante, diseñar las nuestras

Fuera de alcance por ahora: LTE propio del reloj (es modelo de EE.UU.), Samsung Pay y root del teléfono.

## Rutas

| Ruta | Idea | Estado |
|---|---|---|
| **A. Sideload del plugin** | Instalar el *Galaxy Watch Plugin* vía `adb install --bypass-low-target-sdk-block` | ✅ funcionó |
| **B. Parchear APKs** | Si A falla por chequeos de compatibilidad o cuenta, quitar esas validaciones | — |
| **C. Cliente propio (SAP)** | App propia que hable el protocolo Samsung Accessory con el reloj, al estilo Gadgetbridge | — |
| **Carátulas por SDB** | Modo desarrollador del reloj + Tizen Studio para instalar `.wgt`/`.tpk` por Wi-Fi, sin tienda | idea |

Más detalle en [docs/plan.md](docs/plan.md).

## ⚠️ Notas

- **No se suben APKs de Samsung a este repo** (son software con copyright). Se documentan las versiones y su checksum; cada quien las descarga.
- Al vincular el reloj a un teléfono nuevo, es probable que el reloj se restablezca de fábrica.
