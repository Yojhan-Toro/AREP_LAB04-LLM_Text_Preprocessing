# LLM Text Preprocessing & Embeddings

Implementación del Capítulo 2 de *Build a Large Language Model (From Scratch)* de Sebastian Raschka. El notebook recorre el pipeline completo desde texto crudo hasta embeddings posicionales listos para un transformador, con explicaciones propias en español y un experimento sobre ventana deslizante.

---

## Getting Started

Clona el repositorio y sigue los pasos de instalación para ejecutar el notebook en tu máquina local.

```bash
git clone https://github.com/tu-usuario/llm-embeddings.git
cd llm-embeddings
```

### Prerequisites

- Python 3.10 o superior
- pip

```bash
python --version   
pip --version
```

### Installing

1. Crea un entorno virtual e instala las dependencias:

```bash
python -m venv venv
source venv/bin/activate     
```

2. Instala las librerías requeridas:

```bash
pip install torch tiktoken jupyter
```

3. Lanza Jupyter y abre el notebook:

```bash
jupyter notebook embeddings.ipynb
```

4. Ejecuta todas las celdas en orden con **Kernel → Restart & Run All**. Al finalizar deberías ver el tensor de embeddings con forma `[8, 4, 256]`.

---

## Running the Tests

Este proyecto no incluye tests automatizados formales, pero puedes verificar que el pipeline funciona correctamente con las siguientes comprobaciones manuales.

### End-to-end check

Ejecuta la celda de resumen al final del notebook y confirma que imprime:

```
Embedding final (token + posición):
  Forma: torch.Size([8, 4, 256])
```

### Experimento de ventana deslizante

Ejecuta la sección de experimento y verifica que los conteos de muestras coincidan con la fórmula `(total_tokens - max_length) / stride`:

```
max=4,  stride=4  →  ~1285 muestras   (0% solapamiento)
max=4,  stride=2  →  ~2571 muestras  (50% solapamiento)
max=4,  stride=1  →  ~5141 muestras  (75% solapamiento)
```

---

## Deployment

Este proyecto es un notebook educativo y no requiere despliegue en producción. Para usarlo en Google Colab:

```
Archivo → Abrir cuaderno → GitHub → pega la URL del repo
```

---

## Built With

- **[PyTorch](https://pytorch.org/)** — capas de embedding y tensores
- **[tiktoken](https://github.com/openai/tiktoken)** — tokenizador BPE de GPT-2
- **[Jupyter](https://jupyter.org/)** — entorno de ejecución del notebook

---

## Authors

- **Yojhan Toro Rivera** — *Implementación y comentarios* 

Basado en el trabajo original de **Sebastian Raschka** — [rasbt/LLMs-from-scratch](https://github.com/rasbt/LLMs-from-scratch)

---

## Acknowledgments

- Sebastian Raschka por el libro y el código original del repositorio
- Edith Wharton por *The Verdict*, el corpus de texto utilizado en los ejemplos
