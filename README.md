# Reconocimiento de Vocales mediante Energías de Bancos de Filtros Mel

Proyecto desarrollado para la extracción de características de señales de voz utilizando un banco de filtros Mel y la clasificación de vocales mediante una métrica de similitud basada en distancia coseno.

## Descripción

El objetivo del proyecto es implementar un sistema de reconocimiento de vocales a partir de características espectrales obtenidas de señales de audio.

La metodología consiste en:

- Preprocesamiento de las grabaciones de voz.
- Segmentación de la señal en ventanas temporales.
- Cálculo del espectro de potencia mediante la FFT.
- Construcción de un banco de 20 filtros Mel.
- Extracción de las energías de cada filtro.
- Conversión de las energías a escala logarítmica (dB).
- Construcción de un vector característico mediante el promedio temporal de las energías.
- Clasificación utilizando distancia coseno.

Todo el procesamiento fue implementado desde cero en Python sin utilizar librerías de extracción automática de características como MFCC de `librosa`.

---

## Características implementadas

- Lectura y organización automática de la base de datos.
- Normalización de las señales.
- Segmentación en ventanas de 50 ms.
- Solapamiento del 50 %.
- Aplicación de ventana de Hamming.
- FFT y cálculo del espectro de potencia.
- Construcción manual del banco de filtros Mel.
- Cálculo de energías por banda.
- Conversión a escala logarítmica.
- Obtención de un vector de características de dimensión 20.
- Construcción de plantillas promedio por vocal.
- Clasificación mediante distancia coseno.
- Evaluación mediante matriz de confusión.

---

## Representación vectorial

Cada grabación es representada mediante un único vector de dimensión 20.

Para construir este vector se realiza el siguiente procedimiento:

1. División del audio en ventanas.
2. Cálculo de la FFT para cada ventana.
3. Obtención del espectro de potencia.
4. Aplicación del banco de filtros Mel.
5. Cálculo de la energía de cada filtro.
6. Conversión de las energías a decibelios.
7. Promedio temporal de las energías de todas las ventanas.

El resultado final es un vector que resume el contenido espectral de toda la grabación.

---

## Estructura del proyecto

```
Proyecto/
│
├── Proyecto.ipynb          # Notebook principal
├── README.md
├── audio/                  # Base de datos de audios
│
├── resultados/
│   ├── matriz_confusion.png
│   ├── histogramas.png
│   └── filtros_mel.png
│
└── figures/
```

---

## Requisitos

Python 3.10 o superior

Librerías utilizadas:

```bash
numpy
scipy
matplotlib
pandas
os
glob
sklearn
```

Instalación:

```bash
pip install numpy scipy matplotlib pandas scikit-learn
```

---

## Ejecución

1. Clonar el repositorio.

```bash
git clone https://github.com/usuario/repositorio.git
```

2. Abrir el notebook

```
Proyecto.ipynb
```

3. Actualizar la ruta de la base de datos si es necesario.

4. Ejecutar todas las celdas en orden.

---

## Resultados

El proyecto genera:

- Banco de filtros Mel.
- Espectrogramas.
- Energías por filtro.
- Vectores de características.
- Plantillas promedio por vocal.
- Histogramas de similitud.
- Matriz de confusión.
- Resultados de clasificación.

---

## Metodología

La representación de cada señal se obtiene a partir de las energías de un banco de filtros Mel. Después de segmentar la señal y calcular su espectro de potencia mediante la FFT, las componentes espectrales son proyectadas sobre 20 filtros triangulares distribuidos en la escala Mel. La energía contenida en cada banda es calculada y posteriormente convertida a escala logarítmica. Finalmente, las energías de todas las ventanas son promediadas para obtener un único vector de características de dimensión fija que representa el comportamiento espectral de cada grabación.

---

## Autor

**Oscar David Mercado Gómez**

Ingeniería Electrónica

Universidad de Antioquia
