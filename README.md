# DatosingresantesUNCP
Grafico de ingresantes a la UNCP:

## Nos planteamos las preguntas
- De que distrito mas ingreson a la uncp el 2023-1?

## Buscamos la base de datos
- en este caso tenemos un xlsm

## Utilizareos la herramienta de google colaboratory
- cargamos los archivos
  ```py
  from google.colab import files
  uploaded = files.upload()
  ```
- leemos un archivo xlsx y lo llamaos con read_excel
  ```py
  import pandas as pd
  datosingresantes = pd.read_excel('ingresates.xlsx')
  print(datosingresantes)

  ```
- sacaremos in grafico de barras para saber o para visualziar mejor
  ```py
  import pandas as pd
  import matplotlib.pyplot as plt
  
  # Suponiendo que ya tienes los datos cargados en un DataFrame llamado 'datosingresantes'
  
  # Agrupar los datos por el campo 'Distrito' y contar cuántos ingresantes hay en cada distrito
  alumnos_por_distrito = datosingresantes.groupby('Distrito').size().reset_index(name='Cantidad de Alumnos')
  
  # Ordenar los distritos por cantidad de alumnos de mayor a menor
  alumnos_por_distrito = alumnos_por_distrito.sort_values(by='Cantidad de Alumnos', ascending=False)
  
  # Tomar solo los primeros 5 distritos con mayor cantidad de alumnos
  top_5_distritos = alumnos_por_distrito.head(5)
  
  # Crear una figura y ejes para el gráfico de barras
  fig, ax = plt.subplots(figsize=(10, 6))
  
  # Dibujar el gráfico de barras para los 5 primeros distritos
  ax.bar(top_5_distritos['Distrito'], top_5_distritos['Cantidad de Alumnos'])
  
  # Agregar etiquetas en el eje x para mejorar la legibilidad
  ax.set_xticklabels(top_5_distritos['Distrito'], rotation=90, ha='right')
  
  # Configurar el título y las etiquetas de los ejes
  ax.set_title('Top 5 distritos con mayor cantidad de ingresantes')
  ax.set_xlabel('Distrito')
  ax.set_ylabel('Cantidad de Ingresantes')
  
  # Mostrar el gráfico
  plt.tight_layout()
  plt.show()
  ```
- Finalmente ponemos el grafico
  - ![Visualizacio ](/src/barras.png)
 
- Interpretacion:
    - Se puede llegar a la conclusion de que el distrito del tambo tiene mas ingresantes con un total de 310 alumnos.
- Otras conclusiones:
- Se puede sacar de  porque o cuales son las causas que los del tambo tenga mas ingresantes
- se puede analizar como la alimentacion o el tipo de educacion
- o finalmente de como se preparan antes de llegar a tomar una examen de admision 
  

  
