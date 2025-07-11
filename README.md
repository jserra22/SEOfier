# SEOfier

# 🧠 Excel SEO Optimizer con Groq API

Este script en Python te permite generar **nombres y descripciones optimizadas para SEO** a partir de un archivo Excel con información de productos. Utiliza modelos de lenguaje de Groq para generar contenido automáticamente.

## 📌 Requisitos

- Python 3.8 o superior
- Una cuenta en [Groq](https://groq.com/) con una API key válida
- Archivo Excel (`.xlsx` o `.xls`) con los datos del producto

## 📦 Instalación

1. Cloná el repositorio o descargá el script.

2. Instalá las dependencias necesarias:
   ```bash
   pip install pandas python-dotenv groq openpyxl
   ```

3. Creá un archivo `.env` en el mismo directorio que el script con el siguiente contenido:

   ```env
   GROQ_API_KEY=tu_api_key_de_groq
   ```

   > ⚠️ No compartas tu API Key. Este archivo está en `.gitignore` por defecto.

## ⚙️ Uso

1. Ejecutá el script:
   ```bash
   python nombre_del_archivo.py
   ```

2. Se abrirá un diálogo para seleccionar tu archivo Excel.

3. En consola, se te pedirá que indiques qué columnas usar como contexto para generar el contenido SEO. Escribí los nombres separados por coma. Por ejemplo:

   ```
   nombre, categoria, descripcion
   ```

4. El script procesará cada fila, generando:
   - ✅ `Nombre_SEO`
   - ✅ `Descripcion_SEO`

5. Al finalizar, se abrirá un cuadro de diálogo para guardar el nuevo archivo Excel con el contenido generado.

## 🔄 Personalización del modelo

Por defecto se usa:

```python
model = "meta-llama/llama-4-scout-17b-16e-instruct"
```

Podés cambiarlo fácilmente en el constructor de la clase `ExcelSEOOptimizer`:
```python
optimizer = ExcelSEOOptimizer(model="otro-modelo-de-groq")
```

Consultá los modelos disponibles en la [documentación oficial de Groq](https://console.groq.com/docs).

## 🪄 Ejemplo de salida

| nombre       | categoria | descripcion breve      | Nombre_SEO               | Descripcion_SEO                               |
|--------------|-----------|------------------------|---------------------------|------------------------------------------------|
| Yerba Mate   | Bebidas   | Tradicional y suave    | Yerba Mate Suave Premium | Descubrí el sabor auténtico con nuestra yerba mate suave, ideal para cada momento. |

## 🛑 Manejo de errores

- Si ocurre un error con la API, se mostrará un mensaje y se marcará la fila como `"API Error"`.
- Si hay errores al procesar filas individuales, se marcarán como `"Row Processing Error"`.
- Si cancelás la selección o el guardado, el proceso se interrumpe de forma segura.

## 🖥️ Interfaz

Este script utiliza `Tkinter` para manejar diálogos de selección de archivos y mensajes de error, pero **se ejecuta desde la terminal**.

## 🧪 Pruebas

Podés probarlo con un archivo como este:

```csv
nombre,categoria,descripcion breve
Yerba Mate,Bebidas,Tradicional y suave
Café,Bebidas,Intenso y aromático
```

## 📄 Licencia

MIT License
