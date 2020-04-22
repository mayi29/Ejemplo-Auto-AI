# Watson Studio IBM - AutoIA
La automatización y la inteligencia artificial (IA) están transformando las empresas y contribuirán al crecimiento económico a través de contribuciones a la productividad. También ayudarán a abordar los desafíos en áreas de atención médica, tecnología y otras áreas. Al mismo tiempo, estas tecnologías transformarán la naturaleza del trabajo y el propio lugar de trabajo. En este patrón de código, nos centraremos en la creación de sistemas de vanguardia para producir predicciones que se puedan usar en diferentes escenarios. Intentaremos predecir transacciones fraudulentas que sabemos que pueden reducir la pérdida monetaria y la mitigación de riesgos. Se puede utilizar el mismo enfoque para predecir la rotación de clientes, la previsión de demanda y oferta y otros. La construcción de modelos predictivos requiere tiempo, esfuerzo y un buen conocimiento de los algoritmos para crear sistemas efectivos que puedan predecir el resultado con precisión. Con eso dicho,IBM ha introducido Auto AI que automatizará todas las tareas involucradas en la construcción de modelos predictivos para diferentes requisitos. Veremos cómo Auto AI puede producir grandes modelos rápidamente, lo que ahorrará tiempo y esfuerzo y ayudará en un proceso de toma de decisiones más rápido.

## 1. Componentes 📋 
- [IBM Watson Studio](https://translate.googleusercontent.com/translate_c?depth=1&hl=es&pto=aue&rurl=translate.google.com&sl=auto&sp=nmt4&tl=es&u=https://www.ibm.com/cloud/watson-studio&usg=ALkJrhgT0_qVcn95zvZfNTnGnfq5uHL9Wg) : Es posible analizar datos con RStudio, Jupyter y Python en un entorno configurado y colaborativo que incluye valores agregados de IBM, como Spark administrado.

- [IBM Auto AI](https://translate.googleusercontent.com/translate_c?depth=1&hl=es&pto=aue&rurl=translate.google.com&sl=auto&sp=nmt4&tl=es&u=https://dataplatform.cloud.ibm.com/docs/content/wsj/analyze-data/autoai-overview.html&usg=ALkJrhjQI5vcQ5VZ467IRPjEAf1IjokHwg) : Es una herramienta gráfica. AutoAI en Watson Studio analiza automáticamente los datos y genera tuberías de modelos candidatas personalizadas para problemas de modelado predictivo.

## 3. Auto-IA por medio de IBM CLOUD 🚀
### Cuenta IBM Cloud 
Regístrese en IBM Cloud, en caso no tener un cuenta, [activa una gratis](https://cloud.ibm.com/registration)

### Cree un nuevo proyecto de Watson Studio
Regístrece en [Watson Studio IBM](https://dataplatform.cloud.ibm.com/home?context=wdp)
Haz clic en create a project:

<img width="366" alt="1" src="https://user-images.githubusercontent.com/44415995/79924581-bf706480-83fd-11ea-954e-ad929975f657.PNG">

Cree un proyecto vacío:

<img width="842" alt="2" src="https://user-images.githubusercontent.com/44415995/79925056-ff841700-83fe-11ea-99ed-b1777645340d.PNG">

Dele un nombre al proyecto y asignele un object storage, en caso de no tener este servicio, [adquieralo](https://www.ibm.com/co-es/cloud/object-storage)

<img width="889" alt="3" src="https://user-images.githubusercontent.com/44415995/79925208-6a355280-83ff-11ea-898c-8088316c4179.png">

### Agregar Datos:
Descargue este repositorio, donde encontrará un archivo cvs.

Haga clic en los cuadros de la parte inferior y seleccione browser, agregue el archivo csv desde su máquina.

<img width="946" alt="4" src="https://user-images.githubusercontent.com/44415995/79925771-cc428780-8400-11ea-95ee-94155b8b63ad.png">

### Agregue Auto IA al proyecto:
Haga clic en Agregar al proyecto y seleccione AutoAI experiment.

<img width="585" alt="5" src="https://user-images.githubusercontent.com/44415995/79926015-77534100-8401-11ea-9f86-aba79221524c.png">

⚠️  Importante: La cuenta Lite para AutoAI viene con 50 unidades de capacidad por mes y AutoAI consume 20 unidades de capacidad por hora.⚠️ 

### Cree el experimento:
Haga clic en Nuevo experimento AutoAI y asigne un nombre al experimento.
<img width="670" alt="7" src="https://user-images.githubusercontent.com/44415995/79929647-f0f02c80-840b-11ea-8b03-a55f107c49c6.PNG">

Haga clic en Asociar una instancia de servicio de Machine Learning a este proyecto y seleccione la instancia de servicio de Machine Learning y presione recargar. Si no tiene una instancia del servicio de Machine Learning, siga los pasos en la pantalla para obtener una.
El botón Crear en la parte inferior derecha se resalta, continúa y presiona Crear.

<img width="920" alt="8" src="https://user-images.githubusercontent.com/44415995/79929760-4593a780-840c-11ea-989c-43bf33650547.PNG">

### Importe el CVS al experimento:
Tenga en cuenta que solo el formato de archivo csv es compatible con AutoAI. Haga clic en Examinar o Seleccionar del proyecto para elegir el archivo fraude_dataset.csv para importar.

<img width="464" alt="9" src="https://user-images.githubusercontent.com/44415995/79930056-16ca0100-840d-11ea-87de-610501d252fe.PNG">

### Ejecute el experimento
Tenemos que seleccionar la variable de destino, en este caso es Fraud_Risk. Observe que el Tipo de predicción y la Métrica optimizada se resaltan, lo que nos dice que estamos trabajando en el caso de uso de Clasificación binaria y la métrica de evaluación es ROC (Características operativas del receptor) y AUC (Área bajo la curva) que se utiliza para los casos de uso de clasificación.

<img width="563" alt="10" src="https://user-images.githubusercontent.com/44415995/79930165-67415e80-840d-11ea-822d-6eb79677efb0.PNG">

Podemos hacer clic en experiment setting para ajustar la muestra reservada y la muestra de entrenamiento en la configuración de origen, si no desea editar nada, haga clicl en run experiment.
Para este caso cambiamos la métrica de optimización por ROC AUC.

<img width="559" alt="10" src="https://user-images.githubusercontent.com/44415995/79930771-f3a05100-840e-11ea-9641-8a687dd2a911.PNG">

### Resultados
El experimento AutoAI se completó y  genero ocho tuberías. La duración del experimento depende completamente del tamaño de la BD.
AutoAI selecciona el algoritmo de aprendizaje automático apropiado que se adapta mejor al conjunto de datos.

Cada tubería se ejecuta con diferentes parámetros, en algunas tuberias se ejecuta en una secuencia de HPO (optimización de hiperparámetros) y FE (ingeniería de características), mientras que en otras incluye HPO (optimización de hiperparámetros), FE (ingeniería de características) y una combinación de ambos . ¡Todo esto se hace sobre la marcha! ¡¡No es sorprendente que solo tengamos que sentarnos y mirar mientras AutoAI se ocupa de las cosas por nosotros y genera increíbles modelos de aprendizaje automático !! Se requiere una intervención mínima para que todo funcione y en poco tiempo tenemos los canales generados para elegir.

<img width="679" alt="12" src="https://user-images.githubusercontent.com/44415995/79933147-cfe00980-8414-11ea-8496-4ce9a54dfb2c.PNG">

<img width="943" alt="13" src="https://user-images.githubusercontent.com/44415995/79933168-dc646200-8414-11ea-8660-c85d737841c6.PNG">

Haga clic en la tubería que ocupa el puesto 1 para ver las métricas de evaluación en el lado izquierdo.
el rendimiento del modelo en la muestra de espera y el puntaje de validación cruzada. Podemos observar que a nuestro modelo le ha ido muy bien al calificar> 95% en la recuperación, puntajes de precisión promedio y área bajo los puntajes de la curva. Estos puntajes también significan que nuestro modelo puede recordar e identificar transacciones fraudulentas con gran precisión

<img width="629" alt="14" src="https://user-images.githubusercontent.com/44415995/79933418-9956be80-8415-11ea-8a57-901e5489b8b6.PNG">

Haga clic en la importancia de la característica para identificar las características significativas que influyen en el resultado. 

<img width="418" alt="15" src="https://user-images.githubusercontent.com/44415995/79933647-3ca7d380-8416-11ea-9406-323343225b86.PNG">

seleccione el modelo con mayor ranking para la implementación. Dele clic Guardar como modelo y asigenle un nombre.

<img width="943" alt="16" src="https://user-images.githubusercontent.com/44415995/79934228-ae345180-8417-11ea-84b6-4a33a2f73793.png">


### Implemente el modelo:
El modelo guardado se puede encontrar Models debajo del proyecto en Watson Studio. Haga clic en tres puntos en el lado derecho debajo de Acciones y presione Deploy.

<img width="734" alt="17" src="https://user-images.githubusercontent.com/44415995/79934403-13884280-8418-11ea-80fa-ac4cd7dcd26f.png">

Haga clic en create Deployment en el lado derecho arriba.

<img width="934" alt="18" src="https://user-images.githubusercontent.com/44415995/79934576-7da0e780-8418-11ea-9df5-e6b8b4461598.png">

Defina la implementación dando un nombre y presione Save.Tenga en cuenta que el modelo se implementará como servicio web como una API ReST.

<img width="452" alt="19" src="https://user-images.githubusercontent.com/44415995/79934686-bc36a200-8418-11ea-8a11-859422d93223.PNG">

La implementación se inicializará y el estado se mostrará como readycuando se haya completado.

<img width="944" alt="20" src="https://user-images.githubusercontent.com/44415995/79937017-71b82400-841e-11ea-87c7-a716c82c226d.PNG">

### Pruebe el modelo:
Podemos hacer clic en el modelo implementado para ver las pestañas de , Overview, Implementation y Test.
Ingrese a la pestaña Test para probar el modelo.

## Construido con 🛠️
_Se uso IBM Cloud para utilizar los servicios de Watson Assistant que nos proporcionó las herramientas necesarias para crear el chat-bot_
* [IBM](https://www.ibm.com/cloud/watson-assistant/) - El servicio




## Mas información 📖
2. Tecnologías :	📎
Puede hacer uso de esto u otros servicios en la nube [IBM-CLOUD](https://www.ibm.com/co-es/cloud)

Es posible incorporar Watson Assitant en un portal web [IncorporaciónPortal](https://github.com/emeloibmco/Agente-Virtual-COVID-19/blob/master/Incorporaci%C3%B3nAssistantPortal.md)

Incorpore Watson Assitant en Facebook [IncorporaciónFacebook](https://github.com/emeloibmco/Agente-Virtual-COVID-19/blob/master/AsssistanIntegracionFacebook.md)

## Autores ✒️
* **IBM** - *Equipo IBM Cloud*

