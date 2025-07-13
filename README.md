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

![Churn_04](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/fe1975e237d2d3e039aaf472fd2a58613fab36d5/04.%20Boxplot_Churn_y_var_numericas.png)

![Churn_05](https://github.com/ximec74/Telecom-X--Informe-Proyecto-Churn/blob/b64ac33437f67b183dd87189e67fac07e58a9c70/05.%20Churn_y_Clientes_Senior.png)







