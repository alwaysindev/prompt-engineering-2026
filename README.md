# 🧠 Prompt Engineering 2026 – Material del vídeo

Este repositorio contiene los **notebooks y datos que se usan en el vídeo de prompt engineering**
del canal [Always In Dev](https://github.com/alwaysindev). Es para quien quiera ir un paso más allá
de lo que se ve en pantalla: ejecutar las demos, cambiar los textos, probar otros modelos y ver
con números lo que en el vídeo se cuenta con palabras.

> 🎬 Vídeo: _añade aquí el enlace cuando esté publicado_

Los notebooks son **exactamente los que se usaron durante la grabación**, con sus notas de locución
y su orden de ejecución. Se han dejado así a propósito: sirven de guion y de material de estudio.

---

## 📂 Contenido

**[01-tokenizadores.ipynb](01-tokenizadores.ipynb)** – Los tokenizadores y el mito del español
- Qué es un token y por qué las palabras raras se parten en varias piezas
- El mismo párrafo en español e inglés medido con tres generaciones de tokenizador
  (`r50k_base` de GPT-3, `cl100k_base` de GPT-4 y `o200k_base` actual)
- Cuánto ha bajado el "sobrecoste del español" con cada generación
- No necesita clave de API: solo `tiktoken`

**[02-prompt-vago-vs-estructurado.ipynb](02-prompt-vago-vs-estructurado.ipynb)** – El mismo archivo, dos prompts
- Un CSV de ventas con nulos a propósito
- El prompt vago: una línea y el archivo entero pegado
- El prompt estructurado: rol, objetivo, instrucciones, restricciones, formato de salida y **solo el agregado que hace falta**
- Comparación de tokens entre los dos prompts con `tiktoken`
- Necesita una clave de la API de OpenAI

**[ventas_trimestre.csv](ventas_trimestre.csv)** – Datos sintéticos: 480 filas, 6 meses (Q4 2025 y Q1 2026),
10 productos, con valores que faltan en `unidades`, `precio_unitario` e `ingresos`.

---

## 🚀 Requisitos

- Python 3.10 o superior
- Una clave de la API de OpenAI (solo para el notebook 02): https://platform.openai.com/api-keys
- Jupyter, o un editor que ejecute notebooks (VS Code, PyCharm, etc.)

---

## ▶️ Cómo usar este repo

1. Clona el repositorio:
   ```bash
   git clone https://github.com/alwaysindev/prompt-engineering-2026.git
   cd prompt-engineering-2026
   ```

2. Crea un entorno virtual e instala las dependencias:
   ```bash
   python -m venv .venv
   # Windows
   .venv\Scripts\activate
   # macOS / Linux
   source .venv/bin/activate

   pip install -r requirements.txt
   ```

3. Define la clave de OpenAI como variable de entorno (solo para el notebook 02):
   ```bash
   # Windows (PowerShell)
   $env:OPENAI_API_KEY = "sk-..."
   # macOS / Linux
   export OPENAI_API_KEY="sk-..."
   ```

4. Abre los notebooks:
   ```bash
   jupyter notebook
   ```

---

## 💡 Notas sobre el notebook 02

- La primera celda lista los modelos disponibles en tu cuenta. **Copia el ID exacto** en la
  variable `MODELO`: los nombres cambian cada pocos meses.
- La función `preguntar()` usa la Responses API. Si el modelo es razonador y rechaza `temperature`,
  reintenta sin ese parámetro. Si tu SDK es antiguo y no tiene `.responses`, cae a Chat Completions.
- El prompt vago manda el CSV completo (unos 15.500 tokens). El estructurado, unos 550.
  Ejecutarlo entero cuesta unos céntimos, pero conviene saberlo antes de darle a "Run All".
- La respuesta esperada para el prompt estructurado, para comprobar que el modelo no inventa nada:
  Robot aspirador R2 (−42 %), Auriculares BT Zen (−38 %) y Altavoz portátil Mini (−33 %).

---

## 📄 Licencia

Este proyecto está bajo la licencia MIT. Consulta el archivo [LICENSE](LICENSE) para más detalles.
