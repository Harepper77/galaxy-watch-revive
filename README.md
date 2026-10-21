# galaxy-watch-revive ⌚

Revivir relojes Samsung con **Tizen** (Galaxy Watch 2018, Gear S3, Gear Sport…) que Samsung dejó sin soporte, para que vuelvan a funcionar con **teléfonos Android recientes que no son Samsung**.

> Estado: 🟡 **Scoping / investigación** — todavía no hay nada probado.

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
| **A. Sideload de versiones viejas** | Instalar versiones compatibles de *Galaxy Wearable* + *Galaxy Watch Plugin* + *Samsung Accessory Service* vía `adb install --bypass-low-target-sdk-block` | ⏳ siguiente |
| **B. Parchear APKs** | Si A falla por chequeos de compatibilidad o cuenta, quitar esas validaciones | — |
| **C. Cliente propio (SAP)** | App propia que hable el protocolo Samsung Accessory con el reloj, al estilo Gadgetbridge | — |
| **Carátulas por SDB** | Modo desarrollador del reloj + Tizen Studio para instalar `.wgt`/`.tpk` por Wi-Fi, sin tienda | idea |

Más detalle en [docs/plan.md](docs/plan.md).

## ⚠️ Notas

- **No se suben APKs de Samsung a este repo** (son software con copyright). Se documentan las versiones y su checksum; cada quien las descarga.
- Al vincular el reloj a un teléfono nuevo, es probable que el reloj se restablezca de fábrica.
