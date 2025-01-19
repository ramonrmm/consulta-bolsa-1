# Consulta de Datos de Bolsa de Apple

Este proyecto tiene como objetivo consultar los datos financieros de **Apple** utilizando la librería `yfinance` en Python. Se crea una gráfica simple con la cotización de las acciones de Apple a lo largo del tiempo, desde su salida a bolsa hasta el momento actual, además de visualizar los dividendos repartidos por la empresa.


## Descripción
Este proyecto permite:
- Consultar los datos históricos de la cotización de las acciones de Apple desde su salida a bolsa en 1980.
- Visualizar gráficos sobre la evolución de las cotizaciones y los dividendos repartidos por la empresa.
- Acceder a información detallada de la empresa, como el sector al que pertenece y el precio actual de las acciones.

---

## Requisitos
Para ejecutar este proyecto, asegúrate de tener instalado:
- Python 3.7 o superior.
- Librerías de Python:
  - `yfinance`
  - `pandas`
  - `json` (viene incluida con Python)
  - `matplotlib` (para la visualización gráfica)

---

## Instalación

1. **Instala las dependencias necesarias**:
   ```bash
   pip install yfinance matplotlib
   ```
2. **Descargar el archivo apple.json: Puedes hacerlo con cualquiera de estos comandos**
    - Usando `wget`:
    ```bash
    wget https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/data/apple.json
    ```
    - Usando `curl`:
    ```bash
    curl -O https://cf-courses-data.s3.us.cloud-object-storage.appdomain.cloud/IBMDeveloperSkillsNetwork-PY0220EN-SkillsNetwork/data/apple.json
    ```

3. **Nota: Las librerías pandas y json no necesitan instalación adicional:**

    - pandas viene con yfinance.
    - json forma parte de las librerías estándar de Python.


##  Uso
### Consulta de datos
Los datos históricos de las acciones de Apple se consultan mediante el método `history` de `yfinance`.
Ejemplo de consulta:
```bash
import yfinance as yf
apple = yf.Ticker("AAPL")
cotizacion_acciones_apple = apple.history(period='max')
```
### Visualización
- Se puede utilizar la función `plot` de pandas para generar gráficos simples.
- Ejemplo de gráfico de cotización:
```bash
cotizacion_acciones_apple.plot(x='Date', y='Open')
```
### Dividendos
- Para obtener los dividendos históricos de Apple, se utiliza el atributo `dividends` de `yfinance`:
```bash
dividendos_apple = apple.dividends.reset_index()
dividendos_apple.plot(x='Fecha', y='Dividendo')
```

## Ejemplo de ejecución
**Este proyecto realiza los siguientes pasos principales:**

1. Consulta los datos históricos de las acciones y los almacena en un `DataFrame`.
2. Reindexa los datos para facilitar su manipulación.
3. Genera gráficos para visualizar:
    - La evolución de la cotización de las acciones.
    - Los dividendos distribuidos a lo largo del tiempo.
4. Consulta información detallada de la empresa:
    - Sector
    - Precio actual de la acción
Ejemplo de código para obtener el precio actual:
```bash
precio_actual = apple.info['currentPrice']
print(f"El precio actual de la acción es: {precio_actual}")

```
## Notas importantes
- Para identificar el código de cualquier empresa, puedes buscarla en `Yahoo Finances`.
- Los gráficos utilizan la librería `matplotlib` como backend de `pandas`, por lo que no necesitas instalarla explícitamente.


