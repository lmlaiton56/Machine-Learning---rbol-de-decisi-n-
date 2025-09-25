# Machine-Learning---rbol-de-decisi-n-
Trabajo de Machine Learning utilizando un modelo de árbol de decisión 

INTRODRUCCIÓN
En este trabajo se desarrolla un sistema de clasificación de correos electrónicos en dos categorías: 
SPAM (correo no deseado) y HAM (correo legítimo). Para esto se hace uso de un árbol de decisión 
CART (Classification and Regression Trees) utilizando la librería scikit-learn, teniendo en cuenta que 
hace la toma de decisiones por medio de reglas de forma clara. El objetivo es entrenar y evaluar un 
clasificador a partir de un conjunto de características representativas de los correos, tales como la 
presencia de palabras clave, número de enlaces, tamaño de adjuntos e indicadores de envío masivo. 
El modelo se ejecutó en 50 repeticiones independientes, lo que permitió analizar la variabilidad de 
su desempeño y ver su rendimiento. Las métricas empleadas para la evaluación fueron Accuracy y 
F1-score, ya que permiten medir tanto el desempeño global como la precisión específica en la 
detección de correos SPAM.

DATASET
El dataset utilizado está compuesto por un conjunto de correos electrónicos, previamente procesados 
y transformados en variables cuantitativas y categóricas que reflejan correos spam y ham. Entre las 
características incluidas se encuentran:
• palabras_free_gratis: indicador de si el correo contiene términos promocionales como "free" 
o "gratis".
• num_enlaces_ip: número de enlaces en formato de dirección IP.
• tamano_adjuntos_kb: tamaño total de los archivos adjuntos en kilobytes.
• num_imagenes: cantidad de imágenes incrustadas.
• num_frases: número de frases detectadas en el texto.
• caracteres_repetidos: frecuencia de aparición de secuencias repetitivas de caracteres.
• envio_masivo: variable binaria que indica si el correo fue distribuido de manera masiva.
La variable objetivo, denominada clase, toma dos valores posibles: HAM (correo legítimo) y SPAM 
(correo no deseado). Estas características permiten capturar tanto el contenido del correo como 
aspectos de la estructura.

METODOLOGÍA
El procedimiento de entrenamiento y evaluación se llevó a cabo de la siguiente manera, primero fue 
separado el dataset en un 70% para entrenamiento y un 30% para prueba, utilizando diferentes 
valores de random_state. Después se implementó un clasificador DecisionTreeClassifier configurado 
con los parámetros: criterion="gini", max_depth=10, min_samples_split=5 y min_samples_leaf=2, 
estos valores se eligieron porque ayudan a controlar la complejidad del árbol y prevenir sobreajuste. 
Luego el modelo se entrenó con los datos de entrenamiento y aplicado sobre el conjunto de prueba 
en cada iteración.
Para la evaluación se tomaron como referencia dos métricas principales: la Accuracy, que es el 
porcentaje de aciertos globales, y el F1-score, que mide el equilibrio entre la precisión y la sensibilidad
pero solo para la clase SPAM que era la que más interesaba en este caso. Este procedimiento se repitió 
un total de 50 veces, con el propósito de tener una visión más clara de los resultados, obtener 
promedios de las métricas, la desviación estándar y también ver cuáles ejecuciones dieron los mejores 
valores y cuáles tuvieron los peores. Finalmente, después de completar todas las repeticiones, se 
generaron gráficos que muestran la comparación entre Accuracy y F1-score en cada ejecución, además 
de la visualización completa del árbol de decisión correspondiente al modelo con mejor desempeño, 
el cual permite analizar de manera más clara cómo fue que se tomaron las decisiones internas en la 
clasificación de los correos electrónicos entre SPAM y HAM.

CONCLUSIONES
El modelo de árbol de decisión aplicado al dataset de correos mostró un desempeño muy bueno, 
alcanzando métricas cercanas al 100% tanto en Accuracy como en F1-score. Esto evidencia que el 
problema de clasificación SPAM/HAM en este conjunto de datos resulta altamente efectivo para este 
tipo de modelo.
Se observó que ciertas características, como la presencia de palabras promocionales 
(palabras_free_gratis), el número de enlaces en formato IP (num_enlaces_ip) y el indicador de envío 
masivo (envio_masivo), permiten distinguir de manera muy clara los correos SPAM de los HAM. Estas 
variables hacen que el proceso de clasificación sea relativamente sencillo para el árbol, generando 
reglas directas y fáciles de interpretar.
La estabilidad del modelo quedó reflejada en las 50 ejecuciones realizadas, donde incluso en los peores 
casos las métricas se mantuvieron en valores muy altos (cercanos al 99.7%). Esto indica que la división 
aleatoria de los datos apenas afecta su desempeño.
La visualización del árbol de decisión confirma que las reglas generadas son claras y que las variables 
más influyentes permiten separar de manera rápida y efectiva los correos SPAM de los HAM, lo que 
explica el excelente rendimiento alcanzado en todas las repeticiones. 
