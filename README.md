# Sharklatan AirPlay

Parche independiente compatible con **Morphe**, para enviar vídeo y audio de YouTube a un receptor AirPlay utilizando los controles y gestos nativos de YouTube.

<!-- ADD_SOURCE_START -->
[Añadir a Morphe](https://morphe.software/add-source?github=sharklatan/AirPlayTY)
<!-- ADD_SOURCE_END -->

## Compatibilidad de esta versión

| Elemento | Compatibilidad |
| --- | --- |
| YouTube | **21.30.216**, previamente parcheado con Morphe |
| Paquete de entrada | `app.morphe.android.youtube` |
| Motor | Morphe Patcher **2.4.0** |
| Formato | `.mpp` |
| Receptor probado | Hisense 50A6NU / VIDAA |

**Es un segundo paso de parcheo.** Esta entrega no se aplica directamente a la APK original `com.google.android.youtube` ni declara compatibilidad con 21.45.83. Primero genera YouTube con Morphe y **Spoof video streams**, después aplica únicamente Sharklatan AirPlay a esa APK. No vuelvas a aplicar los parches principales al resultado del primer paso.

La reproducción con la APK de adaptación fue confirmada por el usuario. La compilación del paquete `.mpp`, su carga y su ejecución se verifican aparte; eso no equivale a certificar todos los receptores AirPlay. No se incluye la versión anterior de ReVanced 20.40.45: su código y respaldo permanecen en el proyecto de origen.

## Subir esta carpeta manualmente

1. Crea un repositorio **público** en GitHub, por ejemplo `sharklatan-airplay-patches`.
2. Sube **el contenido de esta carpeta**, incluyendo `.github`, `gradle`, `gradlew` y los demás archivos. No subas la carpeta externa como un nivel adicional.
3. En GitHub, abre **Actions → Build and publish AirPlay**. Se ejecuta al subir a `main`; también puedes iniciarlo con **Run workflow**. En forks puede ser necesario habilitar Actions primero.
4. Al terminar aparecerá la Release **v0.1.0**, con `patches-0.1.0.mpp`. El workflow completará el botón **Añadir a Morphe** y los metadatos de actualización usando el nombre real de tu repositorio.
5. En Morphe también puedes abrir **Fuentes → + → Remoto** y pegar la URL de tu repositorio.

No debes compilar en tu PC ni disponer de nuestra clave de firma. GitHub genera el paquete para los usuarios. Si GitHub bloquea escrituras por políticas de la organización, habilita permisos de lectura y escritura de Actions para que publique los metadatos.

Para aparecer en el buscador comunitario, envía la URL pública en [Submit a bundle](https://morphe-patches.software/). Publicar el repositorio no lo agrega automáticamente a ese índice.

## Uso local sin publicar

Importa el `.mpp` desde **Fuentes → + → Local**. El primer paquete verificado se adjunta en el ZIP de entrega, en `release/`. Para recibir actualizaciones automáticas usa la fuente remota publicada.

El paquete de parches no contiene la clave que firma tu YouTube. Morphe sigue firmando las APK con la clave que hayas importado en sus ajustes.

## Compilar desde el código

Requisitos: Python 3.10+, JDK 21+ para el compilador de parches, JDK 17 para las herramientas Android, Android SDK con plataforma 33 y Build Tools 34.0.0.

```sh
# JAVA_HOME: JDK 21 o superior
# AIRPLAY_JAVA_HOME: JDK 17
# ANDROID_HOME: Android SDK
python tools/build.py --version 0.1.0
```

Las dependencias públicas se descargan y se comprueba su SHA-256. El resultado queda en `dist/`. El comando también carga el paquete con Morphe para validar su registro. El proceso no requiere APK, cuentas de Google, credenciales personales de GitHub ni claves privadas.

La estructura Gradle proviene de la plantilla oficial y permite continuar el desarrollo con los plugins de Morphe; su resolución de paquetes puede requerir acceso a GitHub Packages. La ruta pública de compilación comprobada es `tools/build.py` y es la que usa nuestro workflow.

## Funciones y límites

- Icono AirPlay en la fila nativa de controles, sin depender de la visibilidad del botón Cast.
- Selector con recursos y colores de la aplicación.
- Miniatura local, controles de reproducción y volumen del receptor.
- Avance automático y recuperación local al terminar una sesión.
- Los saltos de tiempo usan reapertura de sesión cuando el receptor no confirma un salto directo; pueden producir un corte visible.
- Pulsación larga en el receptor: vídeo y audio / solo audio.
- Mismo acceso de red local que necesita AirPlay. No se envían credenciales de la cuenta de YouTube al televisor.

Las referencias de recursos y puntos de control están limitadas a esta base exacta. Para otras versiones hay que adaptar y probar, no solo ampliar los metadatos.

## Licencias y procedencia

GPL-3.0, con los avisos conservados de la plantilla. Consulta `LICENSE`, `NOTICE`, `THIRD_PARTY_NOTICES.md` y `licenses/`. Producto independiente de Sharklatan; las referencias a Morphe, YouTube y AirPlay describen compatibilidad y no implican patrocinio ni certificación.
