# DW_AppMovilClinica

*Transformando la atención médica con innovación móvil sin fricciones*

![last commit](https://img.shields.io/badge/last_commit-today-success?style=flat) ![java](https://img.shields.io/badge/java-100.0%25-blue) ![languages](https://img.shields.io/badge/languages-1-informational)

_Built with the tools and technologies:_

![JSON](https://img.shields.io/badge/JSON-000?logo=json&logoColor=white&labelColor=333) ![Markdown](https://img.shields.io/badge/Markdown-000?logo=markdown&logoColor=white&labelColor=333) ![npm](https://img.shields.io/badge/npm-000?logo=npm&logoColor=white&labelColor=333) ![Android](https://img.shields.io/badge/Android-000?logo=android&logoColor=3DDC84&labelColor=333) ![Gradle](https://img.shields.io/badge/Gradle-000?logo=gradle&logoColor=02303A&labelColor=333) ![XML](https://img.shields.io/badge/XML-000?logo=w3c&logoColor=white&labelColor=333) ![Google](https://img.shields.io/badge/Google-000?logo=google&logoColor=white&labelColor=333) ![bat](https://img.shields.io/badge/bat-000?logo=windows&logoColor=white&labelColor=333)


---

## Overview

**DW_AppMovilClinica** es una aplicación móvil orientada a **optimizar flujos clínicos**, **mejorar la gestión de pacientes** e **integrar funcionalidades nativas** con contenido web para una experiencia unificada. Basada en Android con recursos web (HTML/CSS/JS) y compatible con Capacitor, permite empaquetar vistas web dentro de una app nativa.

Este proyecto busca impulsar la eficiencia y el acceso a datos en entornos clínicos mediante:

- **Compatibilidad multiplataforma:** arquitectura preparada para integrarse con Capacitor y desplegarse en distintos dispositivos Android con un mismo código base web.
- **Configuración de build robusta:** Gradle y plugins configurados para builds consistentes y mantenibles en Android Studio.
- **Integración nativa de Android:** uso de componentes nativos (por ejemplo, `MainActivity` y `AndroidManifest`) para rendimiento y seguridad.
- **Aseguramiento de calidad:** posibilidad de integrar pruebas (unitarias e instrumentadas) para validar estabilidad durante el desarrollo.
- **Despliegue sencillo:** configuración pensada para copiar recursos web al contenedor nativo y generar APK/Bundle sin fricción.

> **Nota:** Esta app consume un backend público (API) para listar productos de farmacia y mostrarlos en tarjetas responsivas, con soporte de búsqueda y modal de detalle.

---

## Getting Started

### Prerequisites

Este proyecto requiere el siguiente entorno (ajústalo según tu configuración):

- **Programming Language:** Java (Android) + HTML/CSS/JavaScript (frontend).
- **Package Manager:** npm (para tareas de frontend/Capacitor si aplica) y **Gradle** (para Android).
- **Herramientas recomendadas:**
  - **Android Studio** (SDK/NDK y herramientas de plataforma actualizadas).
  - **Node.js** 18+ *(opcional, si usas Capacitor o tareas npm)*.

### Installation

Clona el repositorio y prepara el entorno.

1. **Clonar el repo**
   ```bash
   git clone https://github.com/gchamalef/DW_AppMovilClinica.git
   ```

2. **Entrar al directorio del proyecto**
   ```bash
   cd DW_AppMovilClinica
   ```

3. **(Opcional) Instalar dependencias web**
   > Si tu proyecto incluye `package.json`, instala dependencias:
   ```bash
   npm install
   ```

4. **Copiar recursos web a Android (elige el flujo que uses)**

   - **Capacitor** (recomendado si está configurado):
     ```bash
     npx cap copy android
     npx cap sync android
     ```

   - **Manual**: coloca `index.html`, `styles.css`, `script.js` (y otros estáticos)
     dentro de:
     ```text
     android/app/src/main/assets/public/
     ```

5. **Abrir en Android Studio**
   - Con Capacitor: `npx cap open android`
   - O abre el directorio `android/` directamente en Android Studio.

6. **Compilar con Gradle**
   - Desde Android Studio (Build ▶ Make Project), o
   - Por consola:
     ```bash
     cd android
     ./gradlew assembleDebug
     ```

### Usage

- **Web (estático):**
  - Abre `index.html` directamente en tu navegador, o
  - Sirve los archivos con un servidor local si necesitas CORS/Service Workers.

- **Android (emulador/dispositivo):**
  - Desde Android Studio: _Run ▶ Run 'app'_ (elige un dispositivo/AVD).
  - Por consola (instalar debug en dispositivo conectado):
    ```bash
    cd android
    ./gradlew installDebug
    ```

> El proyecto incluye **modo claro** (`index.html` + `styles.css`) y **modo oscuro** (`darktheme.html` + `darkstyles.css`), con un **botón de alternancia** ya integrado.

### Testing

Pruebas sugeridas (ajústalas a tu stack real):

- **Gradle (unit tests/JVM):**
  ```bash
  cd android
  ./gradlew test
  ```

- **Android instrumentadas (en dispositivo/emulador):**
  ```bash
  cd android
  ./gradlew connectedAndroidTest
  ```

- **npm (si tienes configuración de pruebas web):**
  ```bash
  npm test
  ```

---

## Estructura (vista general)

```
DW_AppMovilClinica/
├─ android/                         # Proyecto Android (Gradle)
│  └─ app/src/main/assets/public/   # Recursos web empaquetados en la app
├─ index.html                        # Modo claro (web)
├─ styles.css                        # Estilos modo claro
├─ script.js                         # Lógica de consumo de API y UI
├─ darktheme.html                    # Modo oscuro (web)
├─ darkstyles.css                    # Estilos modo oscuro
├─ theme-toggle.js                   # Lógica del botón Día/Noche
├─ theme-toggle.css                  # Estilos del botón Día/Noche
└─ README.md
```

---

## Notas

- Revisa tu **.gitignore** para evitar subir archivos generados (`/build`, `/dist`, `node_modules/`, `android/app/src/main/assets/public/`, llaves/keystores, etc.).
- Sustituye `https://github.com/<tu-usuario>/DW_AppMovilClinica.git` por la URL real de tu repositorio.
- Si no utilizas Capacitor, puedes seguir compilando con Gradle y copiando manualmente los recursos web.
