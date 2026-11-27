# Sonificación de astropartículas · Hackathon CoAfina

¿Llegan juntas las partículas de una cascada atmosférica? Puedes explorarlo en una hoja de cálculo. Este dataset reúne **350 cascadas simuladas con CORSIKA 7.8010**. Para ver un caso en el navegador, abre el [CSV de siete llegadas](ejemplos/llegadas_foton_1TeV.csv). En esta cascada iniciada por un fotón de 1 TeV llegaron seis fotones y un electrón en una ventana de 112,78125 nanosegundos.

## Elige una descarga

| Edición | Tamaño de descarga | Qué incluye |
|---|---:|---|
| [STARTER](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/CORSIKA_MULTIESPECIE_STARTER.zip) | 9 MB | Una cascada por cada una de las 35 condiciones, con llegadas y perfiles en CSV. Es el punto de entrada para Excel y LibreOffice. |
| [LITE](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/CORSIKA_MULTIESPECIE_LITE.zip) | 1,26 GB | Llegadas, perfiles, balance de energía y productos atmosféricos de las 350 cascadas. Incluye todos los pasos de transporte de 44 cascadas que cubren las 35 condiciones. |
| [FULL · tres partes](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/tag/multiespecie-v1.0) | 6,19 GB en total | Las mismas tablas y los 394.240.729 pasos de transporte de las 350 cascadas. Instrucciones de descarga y unión más abajo. |

Para el taller, empieza con STARTER. Abre `cascadas.csv` y elige un `id_cascada`. Filtra las llegadas por ese identificador y ordénalas por `tiempo_desde_primera_ns`. Si usas Excel, importa los archivos como UTF-8, con coma entre columnas y punto decimal. Conserva los identificadores como texto.

## Qué se simuló

Las siete primarias son fotón, protón, helio-4, carbono-12, oxígeno-16, silicio-28 y hierro-56. Cada una entra verticalmente con una de cinco energías totales del proyectil (100, 300, 1.000, 3.000 y 10.000 GeV). Se simularon diez cascadas independientes por combinación. La matriz representa condiciones elegidas para compararlas. Los datos proceden de simulaciones, y el reloj de cada cascada empieza de nuevo.

- **Llegadas.** Se registraron 125.140 partículas al nivel de observación. Las 56 cascadas con cero llegadas también están incluidas.
- **Perfiles y energía.** Cada cascada tiene 103 muestras de población y 103 intervalos de balance energético. La profundidad se expresa en g/cm². Las contribuciones por ionización se pueden explorar por separado.
- **Productos atmosféricos.** Se registraron 12.385.948 productos en dos procesos concretos: conversión de fotones en pares electrón–positrón y desintegración de piones neutros en dos fotones. Las tablas de primera interacción tienen su propia cobertura.
- **Transporte.** Cada fila contiene los extremos de un paso. Una partícula puede aportar muchos pasos. El registro carece de un identificador persistente que permita reconstruir su genealogía.

## Descargar y abrir FULL

1. Guarda los cuatro archivos en la misma carpeta: [parte 001](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/CORSIKA_MULTIESPECIE_FULL.zip.001), [parte 002](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/CORSIKA_MULTIESPECIE_FULL.zip.002), [parte 003](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/CORSIKA_MULTIESPECIE_FULL.zip.003) y [unir_full.py](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/unir_full.py). Conserva los nombres de descarga.
2. Abre una terminal en esa carpeta y ejecuta `python unir_full.py` con Python 3. El programa verifica las tres partes y crea `CORSIKA_MULTIESPECIE_FULL.zip`. En Windows también puedes usar `py -3 unir_full.py`.
3. Extrae el ZIP resultante con 7-Zip o ejecuta `python -m zipfile -e CORSIKA_MULTIESPECIE_FULL.zip Cascadas_FULL`. Abre `LEEME.txt` en la carpeta extraída. Reserva unos **24 GB** si conservas las partes, el ZIP unido y los datos extraídos en el mismo disco.

LITE se extrae directamente. En Windows también puedes usar `tar.exe -xf CORSIKA_MULTIESPECIE_LITE.zip` desde una carpeta nueva donde hayas guardado el archivo. El tamaño extraído es de 2,10 GB para LITE y 10,93 GB para FULL.

## Orientarse dentro de LITE y FULL

| Carpeta | Primer archivo que conviene abrir |
|---|---|
| `DATOS_CSV/` | `cascadas.csv` reúne los eventos. Con su identificador puedes abrir llegadas, poblaciones y energía de una misma cascada. |
| `GUIAS/` | `ABRIR_ARCHIVOS.md` explica los formatos. Hay un glosario y ejemplos de Python. |
| `TRANSPORTE/` | `indice_segmentos.csv` indica dónde están los pasos de cada cascada disponible. En LITE, `cobertura_350.csv` identifica las 44 incluidas. |
| `PRODUCCION_ATMOSFERICA/` | `ejemplo.csv` permite explorar pares de partículas nacidas en el mismo vértice. |
| `TECNICO/` | `LEEME.md` explica cómo abrir los archivos originales, las semillas, el código y los controles. |

La descarga **Source code (zip)** que genera GitHub contiene la portada y los archivos pequeños del repositorio. Para obtener LITE o FULL utiliza los archivos de la [release multiespecie](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/tag/multiespecie-v1.0). El archivo `corsika_cascade_STARTER.zip` que ya existía en la raíz se conserva como entrega anterior. Puedes cotejar las descargas con las [firmas SHA-256](https://github.com/rmartinezra/Datos-Simulaciones-Hackathon-CoAfina/releases/download/multiespecie-v1.0/SHA256SUMS.txt).

Las licencias incluidas para datos y código se presentan como propuestas pendientes de adopción por sus titulares.
