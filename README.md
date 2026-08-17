# 🎵📚 Plugin Storage de Prueba: Literatura Musical (Sample Lessons)

Este repositorio es un **Plugin de Almacenamiento (Storage Plugin)** de prueba y muestra para la aplicación **LitMusical** (Escuela de Detectives Literarios).

---

## 🎯 Propósito del Repositorio

Servir como fuente desacoplada e intercambiable de catálogo de lecciones, canciones poéticas, versos sincronizados, cuestionarios de comprensión y diccionario infantil.

La arquitectura de **LitMusical** permite conectar diferentes repositorios de almacenamiento de tipo `storage` sin necesidad de modificar el código fuente de la aplicación principal. Este plugin `literaturamusical-lessons-sample` provee una base limpia/vacía lista para pruebas, desarrollo y creación de nuevos contenidos pedagógicos.

---

## 📁 Estructura del Repositorio

```
literaturamusical-lessons-sample/
├── manifest.json            # Metadatos del plugin (id, nombre, tipo storage, versión)
├── README.md                # Documentación del plugin
├── .gitignore               # Exclusión estricta de audios descargados (*.webm, *.m4a, *.mp3)
├── figures/
│   └── figuras_catalog.json # Catálogo de figuras literarias (Metáfora, Símil, etc.)
├── songs/
│   └── songs_catalog.json   # Catálogo de canciones y versos sincronizados con retos
└── dictionary/
    └── rae_dictionary.json  # Diccionario RAE infantil (definiciones para palabras complejas)
```

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

> **Regla de Almacenamiento:** En la aplicación **LitMusical** se admite **uno y solo un plugin activo de tipo `"storage"`** a la vez. Cuando este plugin está instalado en `plugins/`, todas las adiciones y ediciones de lecciones desde el Modo Admin se sincronizarán directamente en sus ficheros JSON.

---

## 🎵 Esquema de Datos de Canción (`songs/songs_catalog.json`)

Cada canción contiene la letra sincronizada con marcas de tiempo LRC (`tiempoInicio`, `tiempoFin`), preguntas de comprensión didáctica y etiquetado de figuras poéticas:

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

## 🔒 Privacidad y Gestión de Audios

Los archivos de audio pesado (`*.webm`, `*.m4a`, `*.mp3`) **NUNCA** se almacenan en este repositorio Git.
El campo `youtubeUrl` o `audioPreviewUrl` en el catálogo permite que la aplicación principal descargue o reescriba de manera transparente el audio local en el navegador o backend local de la persona que juega.

---

## 🔗 Repositorio Git Oficial

- **Remote URL:** `git@github.com:flachica/literaturamusical-lessons-sample.git`
