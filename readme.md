# Proyecto 1 - Predicción Energía Eólica

## Consideraciones generales

* **Objetivo:** Preveer la **cantidad de electricidad** que se generará con 24H de anticipación usando *predicciones meteorológicas*
* **Componentes:**
  * *Atributos de entrada:* Variables meteorológicas
  * *Variables* *de salida:* Energía eléctrica en Sotavento
* **Datos:** 22 variables meteorológicas de las que solo se usará la *13*, que corresponde a Sotavento
* **Consideraciones del código:**
  * *Lectura de los datos*

    ```python
    # Lectura de los datos de entrada:
    wind_ava = pd.read_csv("wind_available.csv.gz", compression="gzip")
    # Los otros datos que nos proporcionan (wind_competition) son para el modelo final
    # No poseen la variable de respuesta ya que debe ser el modelo final el que lo prediga
    ```

## Estructura:

* Código con **3 notebooks:**
  * *EDA_analisis.ipynb* : contiene todo el EDA y el análisis de los modelos (predicciones y selección mejor modelo)
  * *modelo_final.ipynb* : contiene el modelo final y la ejecución del mismo con los datos a predecir
  * *sol_problema_class.ipynb* : contiene la resolución del problema de clasificación
* **Otros archivos:**
  * Los archivos siguientes se almacenarán en un ZIP
    * *predicciones.csv* : contiene las predicciones generadas
    * *modelo_final.plk* : archivo que corresponde al modelo final generado

## Tareas a realizar

* [ ] (0.3 puntos) Realizar un **EDA simplificado**:
  * [ ] ¿Cuántas características e instancias hay?
  * [ ] ¿Qué variables son categóricas/numéricas?
  * [ ] ¿Hay valores faltantes (missing values)?
    * [ ] ¿Qué variables los tienen?
  * [ ] ¿Hay columnas constantes (que deberían eliminarse)?
  * [ ] ¿Es un problema de regresión o de clasificación?
  * [ ] Otras cuestiones relevantes
* [ ] (0.1 puntos) Decidir cómo se va a llevar a cabo la **evaluación outer** (estimación de rendimiento futuro/evaluación de modelo) y la **evaluación inner** (para comparar diferentes alternativas y ajustar hiper-parámetros).                                                                                                                                                                        - Decidir qué métrica(s) se van a usar y justificar las decisiones.
* [ ] (0.2 puntos) Decidir, usando **KNN**, el **método de escalado más apropiado** para este problema y usarlo
  de aquí en adelante cuando sea necesario.
* [ ] (1.2 puntos) A continuación, se considerarán estos **métodos**: KNN, árboles de regresión, regresión
  lineal (la normal y al menos, la variante Lasso) y SVM:
  * [ ] Se evaluarán dichos modelos con sus hiperparámetros por omisión. También se medirán los
    tiempos que tarda el entrenamiento.
  * [ ] Después, se **ajustarán los hiperparámetros más importantes** de cada método y se obtendrá
    su evaluación. Medir tiempos del entrenamiento, ahora con HPO.
  * [ ] Obtener algunas **conclusiones**, tales como:
    * [ ] ¿cuál es el mejor método?
    * [ ] ¿Cuál de los métodos básicos de aprendizaje automático es más rápido?
    * [ ] ¿Los resultados son mejores que los regresores triviales/naive/dummy? ¿El ajuste de hiperparámetros mejora con respecto a los valores por omisión?
    * [ ] ¿Hay algún equilibrio entre tiempo de ejecución y mejora de resultados?
    * [ ] ¿Es posible extraer de alguna técnica qué atributos son más relevantes?
    * [ ] etc.
* [ ] (0.2 puntos) Seleccionar el **mejor método** (usando la **evaluación inner**), evaluarlo, construir modelo
  final, hacer predicciones para la competición:
  * [ ] Seleccionar la mejor alternativa de las evaluadas en los puntos anteriores.
  * [ ] Estimar el rendimiento / desempeño futuro del modelo (**evaluación outer**). Esta es una
    estimación de cómo se desempeñaría el modelo en la competición.
  * [ ] Entrenar el modelo final. Guardarlo en un fichero (llamado «modelo_final.pkl»).
  * [ ] Utilizar el modelo final para obtener predicciones para el conjunto de datos de la
    competición. Guardar estas predicciones en un fichero (llamado «predicciones.csv»).
* [ ] (0.8 puntos) Sotavento está interesada en saber si las predicciones de los modelos son de más calidad
  cuando la energía producida es baja o cuando es alta. Primero, se pide **comprobar** con el mejor
  modelo obtenido hasta el momento, si las **predicciones** para **valores altos** son *peores* que para **valores
  bajos**. Además, se nos propone **convertir el problema** de regresión **en** uno de **clasificación**, de la
  siguiente manera: cuando la energía sea menor que el tercer cuantil, se considerará clase“baja”, y
  cuando sea mayor, clase “alta”. **Resolver** el **problema** **utilizando** ahora algún **método** para
  **clasificación**, eligiendo *métricas adecuadas*, intentando obtener los mejores resultados y alcanzando
  *conclusiones*.
* [ ] (0.2 puntos) Explicar brevemente **cómo se ha usado ChatGPT** en esta práctica. Se pueden incluir
  prompts (y respuestas) relevantes, casos en los que ChatGPT estaba equivocado, etc. **No más de 2
  páginas en el informe.**
* [ ] (0.5 puntos) Este punto se supone que lo tengo yo completo porque he hecho el trabajo solo. Es el de hacer commits al github semanal cada uno, pero al final lo he hecho solo el trabajo

### Datos relevantes dentro de las tareas

- La variable de respuesta es "*energía*".
- ***Importante***: de los datos originales, hay que quitar todas las variables meteorológicas que no correspondan a la localización de Sotavento (la localización 13).

## Nombres de los atributos/variables de entrada al modelo

• **t2m**: 2 metre temperature `<br>`
• **u10**: 10 metre U wind component `<br>`
• **v10**: 10 metre V wind component `<br>`
• **u100**: 100 metre U wind component `<br>`
• **v100**: 100 metre V wind component `<br>`
• **cape**: Convective available potential energy `<br>`
• **flsr**: Forecast logarithm of surface roughness for heat `<br>`
• **fsr**: Forecast surface roughness `<br>`
• **iews**: Instantaneous eastward turbulent surface stress `<br>`
• **inss**: Instantaneous northward turbulent surface `<br>`
• **lai_hv**: Leaf area index, high vegetation `<br>`
• **lai_lv**: Leaf area index, low vegetation `<br>`
• **u10n**: Neutral wind at 10 m u-component `<br>`
• **v10n**: Neutral wind at 10 m v-component `<br>`
• **stl1**: Soil temperature level 1 `<br>`
• **stl2**: Soil temperature level 2 `<br>`
• **stl3**: Soil temperature level 3 `<br>`
• **stl4**: Soil temperature level 4 `<br>`
• **sp**: Surface pressure `<br>`
• **p54.162**: Vertical integral of temperature `<br>`
• **p59.162**: Vertical integral of divergence of kinetic energy `<br>`
• **p55.162**: Vertical integral of water vapour `<br>`