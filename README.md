# Dash Neon Pro 2.0

Juego arcade infinito para Android, desarrollado con Flutter y un motor Canvas 2D embebido. Esta edición renueva la identidad visual, los iconos y el equilibrio de juego, manteniendo el progreso local de la edición anterior.

## Identidad de la aplicación

- **Nombre visible:** Dash Neon Pro
- **Versión:** 2.0.0 (build 2)
- **Identificador Android:** `com.neondash.game` (se conserva para facilitar actualizaciones sobre instalaciones anteriores)
- **SDK mínimo:** Android 21 (Android 5.0)
- **Modo de juego:** offline; recursos del juego incluidos en el APK.

## Mejoras de esta edición

- Nuevo arte de nave para el icono de Android, con variantes adaptativas, redondas y por densidad.
- Marca Dash Neon Pro aplicada al menú, encabezado, título del WebView y etiqueta Android.
- Nuevo sistema de monedas bonus: cada cinco obstáculos superados consecutivamente otorgan monedas adicionales; el multiplicador de racha aumenta la recompensa.
- Mejor equilibrio de dificultad: aceleración progresiva ligeramente más suave y mayor separación mínima entre patrones de obstáculos.
- Protección de generación: se retrasa la aparición de obstáculos cuando hay una ruta de monedas activa, evitando cruces injustos.
- Interfaz pulida con estados táctiles, foco visible, controles más cómodos y ajustes para pantallas de poca altura.
- Eliminadas las fuentes remotas: la interfaz usa fuentes del sistema y no necesita descargarlas.
- Se conserva la clave de almacenamiento local para mantener monedas, alias, récords, skins y temas existentes.


## Compilar automáticamente en GitHub Actions

Este repositorio incluye el workflow `.github/workflows/build-android.yml`. GitHub compila el APK automáticamente cuando haces `push` a `main` o `master`, al abrir/actualizar un Pull Request hacia esas ramas, o cuando lo ejecutas manualmente. También se activa al publicar un tag que empiece por `v` (por ejemplo, `v2.0.1`).

### Cómo usarlo

1. Crea un repositorio en GitHub.
2. Sube **todo el contenido de esta carpeta** a la raíz del repositorio; `pubspec.yaml` debe quedar en la raíz y la carpeta `.github/workflows/` debe conservarse.
3. En GitHub, abre la pestaña **Actions**.
4. Espera a que termine el workflow **Build Dash Neon Pro APK**. También puedes iniciarlo desde **Actions → Build Dash Neon Pro APK → Run workflow**.
5. Abre la ejecución terminada y descarga el artefacto `dash-neon-pro-android-apk`. Dentro estará `app-release.apk`.

El workflow instala Java 17 y Flutter estable, ejecuta `flutter pub get` y compila con `flutter build apk --release`. No necesitas subir `build/`, `.dart_tool/` ni `android/local.properties` al repositorio: Flutter los genera durante la compilación.

**Nota:** el APK generado por este workflow está firmado con la configuración de depuración que trae este proyecto. Sirve para pruebas e instalación directa; para publicar en Google Play o distribuir actualizaciones oficiales, configura una clave de firma release privada en GitHub Secrets y ajusta la firma de Android. Nunca subas la clave ni sus contraseñas al repositorio.

## Compilar APK en Windows

1. Instala Flutter y Android Studio con el SDK de Android.
2. Extrae el ZIP y abre una terminal dentro de la carpeta del proyecto (donde está `pubspec.yaml`).
3. Ejecuta:

```bash
flutter clean
flutter pub get
flutter build apk --release
```

El APK se genera en:

`build/app/outputs/flutter-apk/app-release.apk`

Para instalarlo con un dispositivo conectado por USB y depuración activada:

```bash
flutter install --release
```

## Notas

- El identificador `com.neondash.game` se mantiene intencionalmente. Cambiarlo haría que Android tratara la app como una aplicación distinta y dificultaría conservar instalaciones existentes.
- El ranking y los datos de torneo siguen siendo locales a cada dispositivo; no se añade sincronización ni validación de premios en servidor.
- La versión del proyecto y el ZIP se han revisado estáticamente. La compilación final del APK debe ejecutarse en un entorno con Flutter/Android SDK.
