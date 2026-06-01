# ACUS099 - Fundamentos para leer archivos WAV con librosa

Material de reforzamiento para el curso **Procesamiento Digital de Señales con Python**.

Este repositorio permite practicar, desde lo más básico, cómo leer un archivo `.wav`, obtener sus muestras, conocer su frecuencia de muestreo, calcular su duración, graficar la forma de onda y escuchar el audio dentro de un cuadernillo Jupyter.

La idea central es:

```text
archivo WAV → señal x → frecuencia de muestreo sr → duración → gráfico → reproducción
```

Antes de trabajar con muchos archivos de audio, es fundamental dominar muy bien el flujo para **un solo archivo WAV**.

## Estructura

```text
acus099_wav_basics_librosa/
├── data/
│   └── audio/
│       └── .gitkeep
├── notebooks/
│   └── 01_leer_un_archivo_wav_con_librosa.ipynb
├── scripts/
│   └── check_audio_files.py
├── outputs/
│   └── figures/
│       └── .gitkeep
├── README.md
├── requirements.txt
└── .gitignore
```

## Archivos de audio

Los archivos de audio **no están incluidos** en este repositorio.

Cada estudiante debe colocar sus propios archivos `.wav` en:

```text
data/audio/
```

Los audios están excluidos del control de versiones mediante `.gitignore`.

## Ambiente de trabajo

```bash
conda activate acus099_2026
```

Instalar dependencias si fuera necesario:

```bash
pip install -r requirements.txt
```

## Revisar archivos WAV disponibles

Desde la raíz del proyecto:

```bash
python scripts/check_audio_files.py
```

## Abrir el cuadernillo

Desde VS Code:

```bash
code .
```

Luego abrir:

```text
notebooks/01_leer_un_archivo_wav_con_librosa.ipynb
```

## Conceptos fundamentales

Con `librosa.load` obtenemos:

```python
x, sr = librosa.load(file_path, sr=None, mono=True)
```

donde:

- `x` es la señal de audio como arreglo NumPy.
- `sr` es la frecuencia de muestreo en Hz.

El número de muestras es:

```python
num_samples = len(x)
```

La duración es:

```python
duration = num_samples / sr
```

Todo procesamiento por lotes nace de repetir este flujo básico muchas veces.
