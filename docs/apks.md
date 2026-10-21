# APKs usados

No se versionan los binarios (ver `.gitignore`). Aquí se registra qué versión se usó, de dónde y su huella, para que cualquiera pueda verificar su copia.

**Certificado de firma oficial de Samsung** (`CN=Samsung Cert, OU=DMC, O=Samsung Corporation`):
`34DF0E7A9F1CF1892E45C056B4973CD81CCF148A4050D11AEA4AC5A65F900A42` (SHA-256 del certificado en `META-INF/CERT.RSA`)

Se verificó comparándolo con el Galaxy Wearable instalado desde Google Play en el Pixel.

| App | Paquete | Versión | Fuente | SHA-256 del APK | Firma |
|---|---|---|---|---|---|
| Galaxy Watch Plugin | `com.samsung.android.geargplugin` | 2.2.05.24020151 (target API 33) | APKMirror | `2E1852F635ECCA97A76B173F2F53318C120541248131582503CEAC30A4855476` | ✅ Samsung |

## Ya instaladas desde Play Store (Pixel 10 Pro XL, Android 17)

| App | Paquete | Versión |
|---|---|---|
| Galaxy Wearable | `com.samsung.android.app.watchmanager` | 2.2.72.26092361 |
| Samsung Accessory Service | `com.samsung.accessory` | 3.1.96.61111 |
| Samsung Health Service | `com.samsung.android.service.health` | 1.6.05.03 |
| (Plugin de otro modelo) | `com.samsung.android.waterplugin` | 2.2.11.25120951 |

## Notas
- Play Store no permite instalar el Galaxy Watch Plugin en Android 17: *"se creó para una versión anterior de Android"*.
- Hay que instalarlo con `adb install --bypass-low-target-sdk-block <apk>`.
