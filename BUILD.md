# Cómo generar la APK de Kiosco

## Lo que necesitás instalado en tu PC

- [Node.js](https://nodejs.org) (v18+)
- [Android Studio](https://developer.android.com/studio) (para el SDK de Android)
- Java JDK 17+ (viene con Android Studio)

---

## Paso 1 — Configurar la URL de tu app

Antes de compilar, editá el archivo `www/index.html` y reemplazá las dos
ocurrencias de `STREAMLIT_URL` con la URL real donde corre tu app.

Por ejemplo, si tu app corre en tu PC en la red local:
```
http://192.168.1.50:8501
```
O si la tenés en Streamlit Cloud:
```
https://tu-usuario-streamlit-app.streamlit.app
```

---

## Paso 2 — Instalar dependencias

Desde la carpeta `apk-kiosco/`:

```bash
npm install
```

---

## Paso 3 — Preparar el proyecto Android

```bash
npx cap sync android
```

---

## Paso 4 — Abrir en Android Studio y generar APK

```bash
npx cap open android
```

Dentro de Android Studio:
1. Esperá que termine de indexar (barra de progreso abajo)
2. Menú **Build → Build Bundle(s) / APK(s) → Build APK(s)**
3. La APK queda en: `android/app/build/outputs/apk/debug/app-debug.apk`

---

## Paso 5 — Instalar en la tablet

Pasá el archivo `app-debug.apk` a la tablet por USB, WhatsApp, o Drive,
abrilo desde el gestor de archivos y seguí los pasos de instalación.

> En Android hay que habilitar "Instalar apps de fuentes desconocidas" en
> Configuración → Seguridad (solo la primera vez).

---

## Consideraciones de red

- La tablet y el servidor deben estar en la **misma red Wi-Fi** si usás IP local.
- Si la app está en la nube (Streamlit Cloud, Railway, etc.) funciona desde cualquier red.
- La APK **no incluye** la app Streamlit adentro — es una ventana que se conecta al servidor.
  Si el servidor está apagado, la app muestra la pantalla de "Sin conexión".
