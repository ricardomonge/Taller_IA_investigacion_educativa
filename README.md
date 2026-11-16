# Taller de Optimización y uso ético de la IA generativa en la investigación educativa

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.24294336.svg)](https://doi.org/10.5281/zenodo.24294336)

Materiales del teletaller dictado por el Dr. Ricardo Monge (rmonge@udla.cl).

El taller tiene dos partes. La primera revisa qué dice la literatura reciente sobre el uso de la IA generativa en el proceso de investigación. La segunda muestra, en Google Colab, cómo construir un sistema RAG (generación aumentada por recuperación) que responde preguntas a partir de artículos exportados de Web of Science, con citas trazables y validación humana. La ética es el eje transversal: protección de datos, sesgos, alucinaciones y supervisión humana en cada etapa.

## Contenido del repositorio

| Archivo | Descripción |
| --- | --- |
| [`IA_investigacion_educativa.pptx`](IA_investigacion_educativa.pptx) | Presentación de la Parte 1 (evidencia), introducción a la Parte 2 y anexos: ejercicio de delegación, vacíos de investigación y lista de verificación. |
| [`Respondedor_preguntas_IA_investigacion_v2.ipynb`](Respondedor_preguntas_IA_investigacion_v2.ipynb) | Cuaderno de la Parte 2: RAG en Python con la API de OpenAI. |
| [`Cadena_busqueda.txt`](Cadena_busqueda.txt) | Fórmula de búsqueda utilizada en Web of Science. |
| [`DB/`](DB) | Registros exportados de Web of Science (11 archivos `.xls`, con títulos y resúmenes). |
| [`sintesis_literatura_IA_2026_10_27.docx`](sintesis_literatura_IA_2026_10_27.docx) | Síntesis generada por el cuaderno: diez preguntas con sus respuestas y referencias. |

## Qué hace el cuaderno

[![Abrir en Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/ricardomonge/Taller_IA_investigacion_educativa/blob/main/Respondedor_preguntas_IA_investigacion_v2.ipynb)

1. Carga las exportaciones de Web of Science y elimina duplicados y registros sin resumen.
2. Convierte cada artículo (título y resumen) en un vector para buscar por significado.
3. Recupera, para cada pregunta, los 12 artículos más relacionados.
4. Pide a un modelo de lenguaje una respuesta en español con citas numeradas. Las referencias las arma el código desde los datos de WoS, no el modelo.
5. Verifica que no se citen documentos inexistentes y exporta los resultados a Excel y Word para la validación humana.

## Cómo reproducirlo

Se necesita una cuenta de Google, una clave de la API de OpenAI (servicio de pago; el costo de este ejercicio es bajo) y los archivos de la carpeta `DB/`.

1. Abrir el cuaderno en Colab con el botón de arriba.
2. Guardar la clave en los Secretos de Colab con el nombre `OPENAI_API_KEY`. No escribirla en el código.
3. Ejecutar las celdas en orden. Cuando se pidan los archivos, subir `savedrecs (11).xls` a `savedrecs (20).xls` como búsqueda 1 y `savedrecs (21).xls` como búsqueda 2.
4. Revisar el Excel generado y completar las columnas de validación humana antes de usar las respuestas.

## Datos y procedimiento

- **Fuente:** Web of Science (Clarivate), publicaciones de 2023 a 2026.
- **Registros:** 511 exportados; tras eliminar 3 duplicados y 4 registros sin resumen, se analizaron 504 artículos.
- **Búsquedas:** «IA generativa en investigación educativa» (492 registros) y «Agentes y automatización de la investigación» (19 registros).
- **Ejecución registrada:** 27 de octubre de 2026, con `gpt-6-luna` para las respuestas, `gpt-4.1-mini` para traducir las consultas al inglés y `text-embedding-3-small` para los vectores. Los modelos se pueden cambiar en los parámetros del cuaderno.

## Limitaciones

- La síntesis se basa solo en títulos y resúmenes, no en textos completos.
- Cada respuesta usa un subconjunto de 12 artículos; lo que no se recupera no llega al modelo.
- Web of Science sobrerrepresenta la literatura en inglés. SciELO, Redalyc y Latindex quedan fuera.
- El cuaderno solo procesa metadatos públicos. No debe usarse con datos personales o sensibles sin anonimización previa y revisión del comité de ética.

## Declaración de uso de IA

La síntesis de la literatura y parte del contenido de la presentación se elaboraron con apoyo de IA generativa, siguiendo el procedimiento descrito arriba. Los resultados requieren contrastarse con los artículos originales antes de citarse o difundirse.

## Cómo citar

Monge, R. (2026). *Optimización y uso ético de la IA generativa en la investigación educativa* [Materiales de taller]. GitHub. https://github.com/ricardomonge/Taller_IA_investigacion_educativa

## Contacto

Dr. Ricardo Monge · rmonge@udla.cl
