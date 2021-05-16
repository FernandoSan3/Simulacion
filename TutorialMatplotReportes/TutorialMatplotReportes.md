---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.11.2
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

<!-- #region papermill={"duration": 0.013336, "end_time": "2021-05-15T15:50:10.460290", "exception": false, "start_time": "2021-05-15T15:50:10.446954", "status": "completed"} tags=[] -->
# Tutorial de Matplot para graficas y de Reportes pagermill

A continuación se detalla un pequeño tutorial de como utilizar matplotlib y pagermill para la generacion de graficas y reportes respectivamente, este tutorial se basa en tres librerias:
- Matplotlib
- Numpy
- Pandas

Al finalizar el estudiante estará en la capacidad de generar graficas y enviar parametros para la realización de reportes utilizando Notebook. Además permite la lectura de archivos .csv y de diferentes tipos de graficos.

<!-- #endregion -->

```python papermill={"duration": 0.696447, "end_time": "2021-05-15T15:50:11.168976", "exception": false, "start_time": "2021-05-15T15:50:10.472529", "status": "completed"} tags=[]
#importar las librerias necesarias
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd

```

```python
#Trabajar con otro tipo de datos Fifa
fifa = pd.read_csv('fifa_datos.csv')
#imprimir los primeros 5 datos del archivo
fifa.head(5)
```

<!-- #region papermill={"duration": 0.014808, "end_time": "2021-05-15T15:50:12.882797", "exception": false, "start_time": "2021-05-15T15:50:12.867989", "status": "completed"} tags=[] -->
## Tarea

1 Con los datos de Fifa, organizar a los jugadores de acuerdo al peso en las siguientes escalas y generar un cuadro tipo PIE

* Debajo 125 Lbs.
* 125-150
* 150-175
* 175 o superior

2 Generar un grafico de barras (histograma) de acuerdo a su habilidad (Overall)  en base a los siguientes segmentos contando el número de jugadores

* 40
* 50
* 60
* 70
* 80
* 90
* 100

3 Investigar como pasar parametros y generar reportes utilizando Notebook, una de las formas es utilizar papermill
<!-- #endregion -->

```python papermill={"duration": 0.182873, "end_time": "2021-05-15T15:50:13.080132", "exception": false, "start_time": "2021-05-15T15:50:12.897259", "status": "completed"} tags=[]
# 1 Con los datos de Fifa, organizar a los jugadores de acuerdo al peso en las siguientes escalas
#y generar un cuadro tipo PIE

Debajo125Lbs = fifa.loc[fifa.Weight  <= '125' ].count()[0]
entre125150 = fifa.loc[fifa.Weight < '151' ].count()[0] - fifa.loc[fifa.Weight <= '126' ].count()[0] 
#entre125150 = fifa.loc[fifa['Weight'] >= '125' ].count()[0] and fifa.loc[fifa['Weight'] <= '150' ].count()[0] 
entre150175 = fifa.loc[fifa.Weight < '176' ].count()[0] - fifa.loc[fifa.Weight <='151' ].count()[0]
#entre150175 = fifa.loc[fifa['Weight'] >= '150' ].count()[0] and fifa.loc[fifa['Weight'] <= '175' ].count()[0] 
superior = fifa.loc[fifa.Weight  >= '176' ].count()[0]
plt.figure(figsize=(8,5))

etiquetas = ['Debajo 125 Lbs.', 'Entre 125-150 Lbs.','Entre 150-175 Lbs.','175 o superior Lbs.']
colores = ['#a0522d', '#aabbcc', '#ff7f50', '#ffbb11']
plt.pie([Debajo125Lbs, entre125150, entre150175, superior], labels=etiquetas, colors=colores, autopct='%.2f %%')
plt.title('Jugadores de acuerdo al peso')
plt.show()
```

```python papermill={"duration": 0.020118, "end_time": "2021-05-15T15:50:13.118032", "exception": false, "start_time": "2021-05-15T15:50:13.097914", "status": "completed"} tags=[]
f = Debajo125Lbs + entre125150 + entre150175 + superior
print(f)
```

```python papermill={"duration": 0.326837, "end_time": "2021-05-15T15:50:13.460099", "exception": false, "start_time": "2021-05-15T15:50:13.133262", "status": "completed"} tags=[]
# Grafico de Barras
# 2 Generar un grafico de barras (histograma) de acuerdo a su habilidad (Overall) 
# en base a los siguientes segmentos contando el número de jugadores

etiquetas = ['40', '50', '60','70', '80', '90', '100']
valor40 = fifa.loc[fifa.Overall <= 40 ].count()[0]
valor50 = fifa.loc[fifa.Overall < 51 ].count()[0] - fifa.loc[fifa.Overall < 41 ].count()[0] 
valor60 = fifa.loc[fifa.Overall < 61 ].count()[0] - fifa.loc[fifa.Overall < 51 ].count()[0] 
valor70 = fifa.loc[fifa.Overall < 71 ].count()[0] - fifa.loc[fifa.Overall < 61 ].count()[0] 
valor80 = fifa.loc[fifa.Overall < 81 ].count()[0] - fifa.loc[fifa.Overall < 71 ].count()[0] 
valor90 = fifa.loc[fifa.Overall < 91 ].count()[0] - fifa.loc[fifa.Overall < 81 ].count()[0] 
valor100 = fifa.loc[fifa.Overall >= 91 ].count()[0]
valores = [valor40,valor50,valor60,valor70,valor80,valor90,valor100]

plt.figure(figsize=(15,6))

barras = plt.bar(etiquetas, valores)

```

```python papermill={"duration": 0.021438, "end_time": "2021-05-15T15:50:13.499769", "exception": false, "start_time": "2021-05-15T15:50:13.478331", "status": "completed"} tags=[]
#valorCom = valor40 + valor50 + valor60 + valor70 + valor80 + valor90 + valor100
#print(valorCom)
```

```python papermill={"duration": 0.060612, "end_time": "2021-05-15T15:50:13.577626", "exception": false, "start_time": "2021-05-15T15:50:13.517014", "status": "completed"} tags=[]
valorT = fifa.loc[fifa['Overall']].count()[0]
print(valorT)
```

<!-- #region papermill={"duration": 0.01677, "end_time": "2021-05-15T15:50:13.611892", "exception": false, "start_time": "2021-05-15T15:50:13.595122", "status": "completed"} tags=[] -->
3 Investigar como pasar parametros y generar reportes utilizando Notebook, una de las formas es utilizar papermill
<!-- #endregion -->

```python papermill={"duration": 1.117634, "end_time": "2021-05-15T15:50:14.745653", "exception": false, "start_time": "2021-05-15T15:50:13.628019", "status": "completed"} tags=[]
pip install -r requirements.txt
```

1. Seleccione la barra de herramientas "View, Cell Toolbar", luego "Tag"
2. Ingrese parámetros en un cuadro de texto en la parte superior derecha de una celda
3. Haga clic en "Add tag"

```python tags=["parameters"]
alpha = 0.1 
ratio = 0.1
```

Se puede llamar a la función inspect_notebook para inspeccionar un cuaderno:

```python
import papermill as pm
pm.inspect_notebook('TutorialMatplotReportes.ipynb')
```

La función execute_notebook se puede llamar para ejecutar un cuaderno de entrada cuando se pasa un diccionario de parámetros:

    execute_notebook(<input notebook>, <output notebook>, <dictionary of parameters>)

```python papermill={"duration": 2883.247868, "end_time": "2021-05-15T16:38:18.107810", "exception": true, "start_time": "2021-05-15T15:50:14.859942", "status": "failed"} tags=[]
import papermill as pm
pm.execute_notebook(
    'TutorialMatplotReportes.ipynb',
    'utput_TutorialMatplotReportes.ipynb',
    parameters = dict(alpha=0.6, ratio=0.1),
    engine_name=None,
    request_save_on_cell_execute=True,
    prepare_only=False, 
    kernel_name=None, 
    language=None, 
    progress_bar=True, 
    log_output=False, 
    stdout_file=None, 
    stderr_file=None, 
    start_timeout=60, 
    report_mode=False, 
    cwd=None
)
```
