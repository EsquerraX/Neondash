# Compilar Dash Neon Pro para Android

## Requisitos
- Flutter SDK estable compatible con Dart 3.4 o superior.
- Android Studio y Android SDK instalados.
- JDK configurado según la versión de Flutter/Gradle del equipo.

## Pasos
Abre PowerShell o CMD en la raíz del proyecto y ejecuta:

```powershell
flutter doctor
flutter clean
flutter pub get
flutter build apk --release
```

APK resultante:

```text
build\app\outputs\flutter-apk\app-release.apk
```

Instalación en un móvil conectado:

```powershell
flutter install --release
```

El proyecto conserva el ID de paquete `com.neondash.game`; si ya tienes una versión anterior instalada, firma el APK con la misma clave de publicación para poder actualizarla sin desinstalar. La configuración de ejemplo del proyecto usa firma debug para builds locales; antes de distribuir públicamente, configura tu propia firma release.


## Compilar desde GitHub sin instalar Flutter localmente

El repositorio ya incluye `.github/workflows/build-android.yml`. Sube el proyecto completo a GitHub conservando la carpeta `.github`, entra en **Actions** y ejecuta **Build Dash Neon Pro APK** (o haz un push a `main`/`master`). Al terminar, descarga `dash-neon-pro-android-apk` desde la sección **Artifacts** de esa ejecución.

Para esta compilación automática se usa Java 17 y Flutter estable. El APK resultante usa la firma de depuración del proyecto; configura firma release y secretos protegidos antes de distribuirlo oficialmente.
