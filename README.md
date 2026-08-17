# 🎵📚 Plugin Storage: Literatura Musical (Sample Lessons)

[![Plugin Type](https://img.shields.io/badge/Plugin--Type-Storage-blue.svg)](https://github.com/flachica/literaturamusical-lessons-sample)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](manifest.json)
[![LitMusical Compatible](https://img.shields.io/badge/LitMusical-Compatible-purple.svg)](https://github.com/flachica/literaturamusical-lessons-sample)

Este repositorio es un **Plugin de Almacenamiento (Storage Plugin)** de prueba y muestra para la aplicación **LitMusical** (*Escuela de Detectives Literarios*).

---

## 🎯 Propósito del Repositorio

Servir como fuente desacoplada e intercambiable de catálogo de lecciones, canciones poéticas, versos sincronizados, cuestionarios de comprensión, perfiles de detectives y diccionario infantil.

La arquitectura de **LitMusical** permite conectar diferentes repositorios de almacenamiento de tipo `storage` sin necesidad de modificar el código fuente de la aplicación principal. Este plugin `literaturamusical-lessons-sample` provee una base limpia/vacía lista para pruebas, desarrollo y creación de nuevos contenidos pedagógicos.

---

## 📁 Estructura del Repositorio

```text
literaturamusical-lessons-sample/
├── manifest.json                    # Metadatos del plugin (id, nombre, tipo storage, versión)
├── README.md                        # Documentación principal del plugin
├── .gitignore                       # Exclusión estricta de audios descargados (*.webm, *.m4a, *.mp3, etc.)
├── figures/
│   └── figuras_catalog.json         # Catálogo de figuras literarias (Metáfora, Símil, etc.)
├── songs/
│   └── songs_catalog.json           # Catálogo de canciones y versos sincronizados con retos
├── dictionary/
│   └── rae_dictionary.json          # Diccionario RAE infantil (definiciones adaptadas)
├── detectives/
│   └── detectives.json              # Perfiles de detectives, puntos, nivel, estrellas y medallas
├── progress/
│   └── user_progress.json           # Estado de puntos acumulados y nivel global del jugador
└── suggestions/
    └── sugerencias_detectives.json  # Propuestas del Buzón Familiar creadas por detectives
```

---

## 🚀 Instalación y Uso

1. **Clonar en el directorio de plugins de LitMusical:**
   ```bash
   cd /ruta/a/litmusical/plugins/
   # Opción HTTPS (Recomendada):
   git clone https://github.com/flachica/literaturamusical-lessons-sample.git
   # Opción SSH:
   git clone git@github.com:flachica/literaturamusical-lessons-sample.git
   ```

2. **Detección Automática:**
   Al iniciar LitMusical, la aplicación escanea la carpeta `plugins/`, detecta el archivo `manifest.json` y registra el plugin como fuente de datos `storage`.

3. **Edición y Sincronización:**
   > ⚠️ **Regla de Almacenamiento:** LitMusical admite **un solo plugin activo de tipo `"storage"`** a la vez. Cuando este plugin está activo en `plugins/`, todas las adiciones y ediciones realizadas desde el **Modo Admin** de la aplicación se guardarán y sincronizarán directamente en los archivos JSON de este repositorio.

---

## ⚙️ Especificación del Manifest (`manifest.json`)

```json
{
  "id": "literaturamusical-lessons-sample",
  "name": "Lecciones de Muestra (Sample)",
  "type": "storage",
  "version": "1.0.0",
  "author": "flachica",
  "description": "Repositorio de prueba y catálogo de muestra para lecciones de Literatura Musical.",
  "repository": "git@github.com:flachica/literaturamusical-lessons-sample.git"
}
```

---

## 📊 Descripción de las Colecciones de Datos

| Directorio | Archivo | Descripción |
| :--- | :--- | :--- |
| `figures/` | `figuras_catalog.json` | Definiciones pedagógicas de figuras retóricas (Metáfora, Símil, Personificación, Hipérbole, Anáfora, Aliteración), colores, iconos y insignias. |
| `songs/` | `songs_catalog.json` | Catálogo de canciones con metadatos, enlace a vídeo/audio, versos sincronizados y preguntas de comprensión. |
| `dictionary/` | `rae_dictionary.json` | Diccionario adaptado a niños con definiciones simplificadas para palabras complejas encontradas en las canciones. |
| `detectives/` | `detectives.json` | Lista de perfiles de detectives creados en la aplicación, sus avatars, insignias y progresos individuales. |
| `progress/` | `user_progress.json` | Progreso acumulado general (puntos totales, nivel actual y estrellas). |
| `suggestions/` | `sugerencias_detectives.json` | Mensajes y canciones propuestas a través del Buzón Familiar. |

---

## 🎵 Esquema de Datos de Canción (`songs/songs_catalog.json`)

Cada canción incluye sincronización temporal tipo LRC (`tiempoInicio`, `tiempoFin`), preguntas de comprensión e identificación de figuras literarias:

```json
[
  {
    "id": "titulo-cancion",
    "titulo": "Título de la Canción",
    "artistaId": "artista",
    "artistaNombre": "Nombre del Artista",
    "album": "Álbum (Año)",
    "temaId": "emocion",
    "temaNombre": "Temática Poética",
    "youtubeUrl": "https://www.youtube.com/watch?v=VIDEO_ID",
    "resumen_didactico": "Explicación breve de la lección para niños.",
    "versos": [
      {
        "linea": 1,
        "estrofaNum": 1,
        "texto": "Texto del primer verso...",
        "tiempoInicio": 10.5,
        "tiempoFin": 15.2,
        "palabrasDificiles": ["palabra"],
        "preguntaComprension": "¿Qué transmite este verso?",
        "opcionesComprension": [
          { "id": "a", "texto": "Opción correcta", "correcta": true },
          { "id": "b", "texto": "Opción distractora", "correcta": false }
        ],
        "figuraId": "metafora",
        "figuraNombre": "Metáfora",
        "explicacion": "Explicación adaptada a 9 años..."
      }
    ]
  }
]
```

---

## 🔒 Privacidad y Gestión de Archivos Multimedia

Los archivos de audio pesado (`*.webm`, `*.m4a`, `*.mp3`, `*.wav`, `*.ogg`, `*.flac`) están **estrictamente excluidos** del control de versiones mediante `.gitignore`.

El campo `youtubeUrl` (o `audioPreviewUrl`) en el catálogo permite a LitMusical descargar o reproducir el contenido multimedia localmente en el dispositivo del usuario sin saturar el repositorio Git.

---

## 🔗 Repositorios del Ecosistema LitMusical

Para explorar, clonar o investigar el proyecto completo, aquí están los enlaces a los repositorios públicos del ecosistema:

| Repositorio | Tipo | Descripción | Enlace Web (GitHub) | Comando de Clonación |
| :--- | :--- | :--- | :--- | :--- |
| 📱 **LitMusical App** | Aplicación Web | Plataforma PWA principal (*Escuela de Detectives*) | [flachica/literaturamusical-teacher](https://github.com/flachica/literaturamusical-teacher) | `git clone https://github.com/flachica/literaturamusical-teacher.git` |
| 🧪 **Storage Sample** | Storage Plugin | *(Este repositorio)* Plantilla de muestra limpia para pruebas y desarrollo | [flachica/literaturamusical-lessons-sample](https://github.com/flachica/literaturamusical-lessons-sample) | `git clone https://github.com/flachica/literaturamusical-lessons-sample.git` |

---

## 👤 Autor y Mantenedor

- **Autor:** flachica
- **Licencia:** Proyecto educativo y didáctico colaborativo.

