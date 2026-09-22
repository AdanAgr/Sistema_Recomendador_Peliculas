# Sistema Recomendador de Películas

Este proyecto es un prototipo de sistema de recomendación de películas desarrollado en Python. Combina filtrado por preferencias del usuario con un modelo SVD entrenado sobre datos de valoraciones para generar recomendaciones personalizadas.

El proyecto incluye una interfaz gráfica de escritorio, módulos de carga y entrenamiento del modelo, persistencia del modelo entrenado y pruebas unitarias básicas.

## Características

- Recomendaciones personalizadas por ID de usuario.
- Filtrado por géneros cinematográficos.
- Filtrado por décadas de estreno.
- Búsqueda por palabras clave o etiquetas.
- Modelo colaborativo basado en `SVD` de la librería `scikit-surprise`.
- Interfaz gráfica construida con `Tkinter`.
- Separación por responsabilidades: carga de datos, entrenamiento, predicción, persistencia e interfaz.

## Tecnologías

- Python 3
- pandas
- scikit-surprise
- joblib
- Pillow
- Tkinter
- unittest

## Estructura del proyecto

```text
.
|-- README.md
|-- requirements.txt
|-- Arquitectura.pdf
|-- Diseño.pdf
|-- TestComprobacion.png
`-- Prototipo/
    |-- DatasetLoader.pyÑ
    |-- IU.py
    |-- ModeloEntrenamiento.py
    |-- ModeloSVD.py
    |-- PersistenciaModelo.py
    |-- Prediction.py
    |-- Recommendation.py
    |-- RecommendationSystem.py
    |-- Test.py
    |-- UserData.py
    |-- peliculas_vistas.py
    `-- fonts/
```

## Cómo funciona

1. `DatasetLoader` carga ratings, películas y etiquetas desde el dataset.
2. `ModeloSVD` entrena un modelo de filtrado colaborativo con `scikit-surprise`.
3. `PersistenciaModelo` guarda el modelo entrenado en un archivo `.pkl`.
4. `RecommendationSystem` carga el modelo y expone el método principal de recomendación.
5. `Prediction` filtra películas por preferencias y ordena las predicciones por puntuación estimada.
6. `IU` ofrece una interfaz de escritorio para introducir preferencias y mostrar resultados.

## Requisitos previos

Para ejecutar el prototipo es necesario disponer de:

- Python 3 instalado.
- Dependencias principales:

```bash
pip install pandas scikit-surprise joblib pillow
```

- Dataset MovieLens 10M en la ruta:

```text
Prototipo/ml-10M/
```

La carpeta debe contener, como mínimo:

```text
movies.dat
ratings.dat
tags.dat
```

- Modelo entrenado en:

```text
Prototipo/modelo_svd.pkl
```

El dataset y el modelo entrenado no están incluidos en este repositorio.

## Instalación

1. Clona el repositorio:

```bash
git clone <url-del-repositorio>
cd Sistema_Recomendador_Peliculas
```

2. Crea y activa un entorno virtual:

```bash
python -m venv .venv
```

En Windows:

```bash
.venv\Scripts\activate
```

En macOS o Linux:

```bash
source .venv/bin/activate
```

3. Instala las dependencias:

```bash
pip install pandas scikit-surprise joblib pillow
```

4. Copia el dataset MovieLens 10M dentro de `Prototipo/ml-10M/`.

5. Coloca el modelo entrenado como `Prototipo/modelo_svd.pkl` o genera uno siguiendo la sección de entrenamiento.

## Ejecución

Ejecuta la interfaz gráfica desde la carpeta `Prototipo`, ya que el proyecto utiliza rutas relativas para localizar el dataset, las fuentes y el modelo:

```bash
cd Prototipo
python IU.py
```

Desde la aplicación podrás seleccionar géneros, décadas, palabras clave, un ID de usuario y el número de recomendaciones que quieres obtener.

## Entrenamiento del modelo

El entrenamiento se realiza con `ModeloEntrenamiento.py`, que carga ratings, entrena un modelo SVD y lo guarda mediante `joblib`.

Antes de ejecutarlo, revisa la ruta `ratings_path` dentro de:

```text
Prototipo/ModeloEntrenamiento.py
```

Debe apuntar al archivo:

```text
Prototipo/ml-10M/ratings.dat
```

Después, ejecuta:

```bash
cd Prototipo
python ModeloEntrenamiento.py
```

El resultado esperado es un archivo:

```text
modelo_svd.pkl
```

## Pruebas

Las pruebas unitarias se encuentran en:

```text
Prototipo/Test.py
```

Para ejecutarlas:

```bash
cd Prototipo
python -m unittest Test.py
```

Ten en cuenta que las pruebas requieren el dataset `ml-10M` y el modelo `modelo_svd.pkl`.

## Documentación adicional

El repositorio incluye documentación de apoyo:

- `Arquitectura.pdf`: descripción de la arquitectura del sistema.
- `Diseño.pdf`: documentación de diseño del prototipo.
- `TestComprobacion.png`: evidencia visual de comprobación.

## Estado del proyecto

Este prototipo académico/experimental está orientado a demostrar un flujo completo de recomendación:

- carga de datos,
- entrenamiento de modelo,
- persistencia,
- predicción,
- filtrado por preferencias,
- e interfaz de usuario.

Como siguientes mejoras recomendadas para un entorno productivo se podrían incluir:

- normalizar rutas mediante configuración externa,
- completar `requirements.txt`,
- empaquetar el proyecto como módulo Python,
- automatizar la descarga/preparación del dataset,
- ampliar cobertura de pruebas,
- y separar la lógica de interfaz de la lógica de dominio.

