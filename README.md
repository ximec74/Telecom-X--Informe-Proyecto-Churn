# Telecom-X--Informe-Proyecto-Churn
Informe sobre el análisis de Churn (evasión) de clientes en Telecom X

🔹 Introducción

El siguiente es un análisis exploratorio, realizado de manera gráfica para buscar las principales causas que expliquen la alta tasa de evasión/ cancelaciones de clientes (Churn) de la empresa Telecom X, para lo cuál han implementado el proyecto "Churn de Clientes".

El análisis se realizó sobre una base de datos con información de 7.266 clientes, con contratos de antigüedad de hasta 6 años.

🔹 Limpieza y Tratamiento de Datos:

La base de datos se importó de la API de Telecom X, disponibles en formato JSON.

Después de importarla, al revisar el Data Frame (DF) obtenido nos dimos cuenta que las columas de información personal de los clientes y la de los tipos de servicios contratados e información de contratos estaban anidadas, por lo que procedimos a aplanar el DF con normalize().

Ya aplanado del DF se procedio a revisar los datos, antes de trabajar con ellos, buscando:

• Valores únicos y contarlos de todas las columnas • Buscando valores faltantes (nulos) • Filas duplicadas, no se detectaron. • Detectar strings vacíos o espacios en blanco • Tipos de datos, se transformó una columna a valor numérico. • Valores vacios, se eliminaron filas vacias de la columna Churn (224). • Consistencia y validez de datos categóricos • Normalización de textos, revisar mayúsculas y minúsculas, no fue necesario.

 🔹 Análisis Exploratorio de Datos
Después de eliminar las filas vacias de la columna Churn, la base de datos quedó con 7042 filas de clientes. 

**Análisis descriptivo de variables numéricas**
1. customer.tenure (antigüedad del contrato, en meses)
Media: 32,37 meses
Mediana: 29 meses
Mínimo: 0 → hay clientes recién incorporados
Máximo: 72 → contratos de hasta 6 años
Distribución: asimétrica hacia la derecha, con alta dispersión (std: 24,56)
IQR (25% a 75%): de 9 a 55 meses → gran variabilidad
✅ Hay una mezcla de clientes nuevos y antiguos, pero con fuerte concentración en los primeros y últimos tramos del ciclo de vida.

2. account.Charges.Monthly (cargo mensual)
Media: 64,76
Mediana: 70,35
Mínimo: 18,25
Máximo: 118,75
Distribución: ligeramente asimétrica hacia la izquierda (media < mediana)
IQR: de 35,50 a 89,85
✅ Mayoría de clientes tiene cargos entre 35 y 90; algunos con planes básicos, otros premium. Existe un segmento sensible a los cargos mensuales altos.

3. account.Charges.Total (cargo acumulado total)
Media: 2283,30
Mediana: 1397,48
Mínimo: 18,80
Máximo: 8684,80
Distribución: fuertemente asimétrica a la derecha (media > mediana, alta std)
IQR: de 401,45 a 3794,74
✅ Muchos clientes con cargos bajos acumulados (recién ingresados o que abandonaron), y unos pocos con cargos muy altos. Variable claramente asociada a duración del contrato.

4. cuentas_diarias (uso promedio diario)
Media: 2,16
Mediana: 2,34
Mínimo: 0,61
Máximo: 3,96
Distribución: ligeramente asimétrica hacia la izquierda (media < mediana)
IQR: de 1,18 a 2,99
✅ Uso moderado en general, con una tendencia a 2–3 cuentas diarias. Clientes muy activos superan 3,5.

**Conclusión general**
El dataset tiene alta variabilidad y asimetría en las tres variables clave: antigüedad, cargos totales y actividad.
Tenure y cargos totales están fuertemente correlacionados, mientras que cuentas_diarias y cargos mensuales se relacionan más con el comportamiento de churn.
Estos patrones sugieren que la retención de clientes está vinculada a una combinación de antigüedad de contrato, valor económico y frecuencia de uso.

**Análisis Grafico**
El primer análisis realizado corresponde a graficar la proporción del clientes que han abandonado (churn) el contrato vs los que han permanecido.
Observamos en el gráfico que la proporción de clientes que han abandonado corresponde al 26,5% (1.866 clientes) de los clientes, mas del 25% del total de clientes, un valor muy alto comparado al 5,36% de la industría Digital Media & Entertainment(https://recurly.com/research/churn-rate-benchmarks/).

![Churn 01](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/d807671fb9026935977d57065408b6593cd5aa1c/01.%20Clientes_Proporcion_Evasion_Permanencia.png)

Lo siguiente que analizaremos son los graficos relacionados con las variables categóricas y como se relacionan con Churn.
Las variables categoricas que se consideraron son: 1)SeniorCitizen 1) customer.gender, 2)customer.Partner, 3) customer.Dependents, 4) phone.PhoneService, 5) internet.InternetService, 6) account.Contract, 7) account.PaymentMethod.

![Churn 02](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/22654deaafd0fa5706c98d1feaab40a8d401e0dd/02.Churn_por_variables_categoricas_compacto.png)
**Grafico y Customer.SeniorCitizen**. 83.8% de los clientes que contrataron no son Senior, y de estos un 23,6% abandonaron el contrato, lo que a nivel global representan un 19,8% . Es decir, considerar que cualquier esfuerzo para mantener los clientes están enfocados en un gran porcentaje sobre clientes No Senior.
**Grafico Churn y Genero**. Nos muestra que el abandono de los clientes es del mismo porcentaje por Genero, no se observa una diferencia en los porcentajes que nos indique que manipulando esta variable podamos contener el abandono.
**Grafico Churn y Customer.Partner**. En este grafico se observa que el nivel de abandono cuando la persona no tiene pareja es mayor que si la tuviera, un 17,0% vs 9,5%.
**Grafico Churn y Customer.Dependents**.El grafico nos muestra que existe una fuernte diferencia en el porcentaje de abando cuando la persona tiene o no dependientes, siendo este de un 21,9% cuando el cliente no tiene dependientes vs 4,6% cuando los tiene. Además nos muestra, que los clientes sin dependientes representan un actualmente 48,1% del total, y que son los que mas se tiene que cuidar por su fuerte tasa de abandono.
**Grafico Churn y PhoneService**. El grafico nos muestra que existe una fuernte diferencia en el porcentaje de abando cuando la persona tiene o no PhoneService, siendo este de un 24,9% cuando el cliente tiene PhoneService vs 2,4% cuando no los tiene.
**Grafico Churn y InternetService**. 78,3% de los clientes tuvo en algún momento servicio de internet, DSL o Fibra optica, de los clientes de Fibra optica, 18,4% abandonaron el servicio y de DSL 6.5%.
**Grafico Churn y Contrato**. La empresa tiene contratos mes a mes, por año y dos años. 23,5% de los clientes que abandonaron la empresa tenían contrato mes a mes. Si bien este tipo de contrato es el que tiene la mayor cantidad de clientes actualmente 31,5%, también son los que mas abandonos tienen.
**Grafico Churn y Payment.Method**. La mayoría de los clientes al contratar los servicios opta por Electronic Check 33,6%, el resto de los medios de pago, Bank transfer (automatic), Mail check y Credit Card (automatic), es seleccionado casi en la mima proporción que ronda un 22%. La tase de abandono es mayor bajo la opción Electronic Check representando un 45,2% del total de clienes que contratan bajo esa opción y un 15,2% del total de clientes que contrato en algún momento.

![Churn_03](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/e76ee1cfb42fbbb6b9dd6f4346f3a549206caf49/03.%20Extra_Churn_segun_tipo_servicio_excluyente.png)
Del 26,5% de clientes que han abandonado el contrato, 22,5% tienen servicios de internet y telefonía.

#**Conteo de evasión por variables numéricas**#

![Churn_04](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/147161e9446fdb20fea37fca72c036bdafa10c5c/04.%20Boxplot_Churn_y_var_numericas.png)

**Boxplot Tenure/ Antigüedad del Contrato y Churn**. Considera la distrubución de antigüedad de contratos desde 0 a 72 meses, los clientes que mantienen el contrato presentan una distribución simétrica con alta dispersión. La mayoría de los datos se encuentran entre 15 y 61 meses de antigüedad, con una mediana de 38 meses. Aunque hay valores mínimos de 0, no hay indicios claros de valores extremos por encima del rango normal.
✅Contratos más antiguos y distribución simétrica centrada en 38 meses.
✅ Alta permanencia asociada a mayor antigüedad.
Los clientes que abandonan tienen una distribución sesgada a la izquierda, con una mediana de apenas 10 meses y el 50% de los casos entre 2 y 29 meses. La media (18) mayor a la mediana refuerza la presencia de una cola derecha, es decir, unos pocos clientes antiguos que se van, pero la mayoría abandona temprano. Esta diferencia sugiere que la antigüedad del contrato es una variable fuertemente predictiva del churn, especialmente en los primeros meses. Los clientes que no superan el primer año son significativamente más propensos a abandonar el servicio.
➡️ Contratos mucho más recientes.
➡️ Distribución asimétrica hacia la izquierda (la media está más alta que la mediana).
➡️ Alta concentración de clientes que se van en los primeros meses.

**Boxplot Cargos mensuales y Churn**. Los clientes que abandonan el servicio presentan cargos mensuales significativamente más altos que aquellos que permanecen. La mediana de este grupo (79,7) está muy por encima de la de los clientes que permanecen (64,4), y su primer cuartil (56,1) ya supera la mediana del grupo que no hace churn.
Esto indica que **el riesgo de abandono aumenta con el valor de la tarifa mensual.** Además, los cargos de clientes que hacen churn están más concentrados (IQR más estrecho), lo que refuerza la idea de que hay un segmento específico de alto costo que es más sensible o insatisfecho.
En cambio, los clientes que pagan menos presentan mayor dispersión en sus cargos, y tienden a permanecer más tiempo, posiblemente por percepción de valor o menor presión económica.

**Boxplot Cargos Totales y Churn**. Los clientes que permanecen presentan :
✅ Distribución asimétrica a la derecha (media > mediana), indicando presencia de clientes con cargos acumulados altos.
✅ IQR amplio: 3687,1, alta dispersión.
✅ Valores acumulados mucho mayores, coherente con contratos largos.
Clientes que abandonan presentan:
➡️ Distribución también asimétrica a la derecha.
➡️ IQR más estrecho (2199,8), con valores más concentrados en la parte baja.
➡️ Cargos totales notablemente más bajos que los clientes que permanecen.

**Comparación con boxplot Cargos Mensuales:**
  **Clientes con Churn:**
Pagan cargos mensuales más altos, pero tienen cargos totales más bajos.
Esto indica que abandonan el servicio temprano, antes de acumular altos montos.
  **Clientes que Permanecen:**
Pagan menos al mes, pero acumulan más cargos totales, coherente con una mayor duración del contrato.

**Boxplot Cuentas diarias y Churn**. Se observa que los clientes que presentan churn tienen una actividad diaria significativamente más alta, con una mediana de 2,7 cuentas por día, en contraste con 2,1 en los que permanecen. 
La diferencia en los cuartiles también es clara: los clientes que se van rara vez tienen menos de 1,9 cuentas diarias, mientras que los que permanecen están por debajo de ese valor en el 25% de los casos.
Esta diferencia indica que una mayor frecuencia de uso diario podría estar asociada al abandono, posiblemente por una mayor exposición a fallos, frustraciones, o percepción negativa del servicio.
Alternativamente, podría reflejar a un perfil más intensivo, exigente o transaccional, con menor fidelización.

🧩 **Relación con los otros boxplots**
✅ Este patrón complementa el de cargos mensuales altos y baja antigüedad como predictores de churn.
✅ Clientes con alta actividad diaria + cargos altos parecen más propensos a irse rápidamente, lo que puede apuntar a una experiencia de cliente deficiente para los usuarios más activos.

![Churn_05](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/ed4ebdc177ed6e50d619dd72f1ad7758df18ab8c/10.%20Churn_y_%20antiguedad_%20del_%20contrato.png)
Este grafico, reafirma los hallazgos de los boxplot, donde el 50% de los clientes que abandonan se concentran en los primeros 10 meses, unos pocos clientes antiguos que se van, pero la mayoría abandona temprano. **Esta diferencia sugiere que la antigüedad del contrato es una variable fuertemente predictiva del churn, especialmente en los primeros meses. Los clientes que no superan el primer año son significativamente más propensos a abandonar el servicio.**


