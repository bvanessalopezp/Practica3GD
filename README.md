[![Open in MATLAB Online](https://www.mathworks.com/images/responsive/global/open-in-matlab-online.svg)](https://matlab.mathworks.com/open/github/v1?repo=bvanessalopezp/Practica3GD)

# Practica 3. Liberación controlada de fármacos por hidrogeles

## Información de la estudiante
Brianna Vanessa Lopez Pardo \[22212261]; l22212261@tijuana.tecnm.mx

Gemelos Digitales

Ingeniería Biomédica

## Docente
Dr. Paul Antonio Valle Trujillo; paul.valle@tectijuana.edu.mx

Departamento de Ingeniería Eléctrica y Electrónica, Tecnológico Nacional de México/IT Tijuana, Blvd. Alberto Limón Padilla s/n, Tijuana, C.P. 22454, B.C., México.

## Descripción de la asignatura
La asignatura de Gemelos Digitales forma parte del plan de estudios de la carrera en Ingeniería Biomédica con la siguiente competencia general del curso: Formula el gemelo digital a través de datos experimentales para el desarrollo estrategias de control mediante teorías de sistemas dinámicos no lineales y la experimentación in silico. Esta asignatura pretende aportar al perfil del Ingeniero Biomédico la capacidad de realizar investigación científica en el área de Biología de Sistemas con la finalidad de dirigir y participar en equipos de trabajo interdisciplinarios en contextos nacionales e internacionales, así como de proporcionar soluciones informáticas para resolver problemas en el campo de la Ingeniería Biomédica con ética profesional.

En el contexto de sistemas dinámicos que describen sistemas biológicos o fisiológicos, el modelizado in silico es una extensión lógica de la experimentación in vitro controlada, es el resultado natural del gran aumento de la potencia computacional disponible a un costo que disminuye continuamente, combinando las ventajas de la experimentación in vivo e in vitro, sin someterse a las consideraciones éticas y la falta de control asociadas con los experimentos in vivo. A diferencia de los experimentos in vitro, que existen de forma aislada, los modelos in silico permiten incluir un conjunto prácticamente ilimitado de variables y parámetros, lo que hace que los resultados sean más aplicables en problemas del mundo real. La experimentación in silico ha dado lugar al paradigma denominado como "gemelos digitales" (en inglés digital twins); en esencia, los gemelos digitales son una réplica o representación digital de un proceso o sistema del mundo real, donde por replica se refiere a un modelo computacional desarrollado con base en datos experimentales y características especiales que le permiten conectar lo físico con lo virtual con el propósito de mejorar el rendimiento de un sistema, detectar y prevenir fallas, y realizar predicciones sobre su respuesta ante diferentes estímulos o escenarios de operación; una definición más formal establece que: un gemelo digital es un conjunto de modelos adaptativos que emulan el comportamiento de un sistema físico en un sistema virtual obteniendo datos en tiempo real para actualizarse a lo largo de su ciclo de vida; replica al sistema físico para predecir fallas y oportunidades de cambio, prescribir acciones en tiempo real para optimizar y/o mitigar eventos inesperados observando y evaluando el perfil operativo del sistema. En el campo particular de la Biología de Sistemas, un gemelo digital se presenta como un algoritmo o conjunto de algoritmos computacionales desarrollados con base en modelos mecanicistas de un organismo vivo, esto con el objetivo de emular su fisiología para ilustrar su dinámica en el corto y en el largo plazo, así como predecir su respuesta a diferentes estímulos endógenos y exógenos.

## Objetivo y descripción del sistema
# Práctica: Liberación Controlada de Fármacos por Hidrogeles

**Departamento de Ingeniería Eléctrica y Electrónica, Ingeniería Biomédica**  
Tecnológico Nacional de México [TecNM - Tijuana]  
Blvd. Alberto Limón Padilla s/n, C.P. 22454, Tijuana, B.C., México


## Objetivo

Determinar la tasa de liberación del fármaco 5-fluorouracilo (5FU) desde el nanohidrogel **N36-2MBA3**, con base en los datos experimentales reportados en González-Ayón et al. (2015), mediante el ajuste de modelos matemáticos a través de regresión no lineal, bioestadística y experimentación *in silico* implementadas en MATLAB.

## Descripción del Sistema

Un tipo particular de sistema farmacocinético es aquel en el que la liberación de un fármaco desde un vehículo polimérico depende de las condiciones del entorno, como la temperatura y el pH. A continuación, se presentan los modelos matemáticos empleados para describir la liberación controlada de 5FU desde el nanohidrogel N36-2MBA3, un sistema núcleo-coraza sintetizado a partir de NVCL, 2MBA y PEGMA.

Los modelos considerados son los siguientes:

$$x(t) = k t^n \quad (1)$$

$$x(t) = \beta(1 - e^{-kt}) \quad (2)$$

$$x(t) = \rho_1 + t - \rho_2 \cdot t^2 \quad (3)$$

$$\dot{x} = 2.28 - \rho_1 \cdot x \quad (4)$$

donde la Ecuación (1) corresponde al **modelo de Peppas**, la Ecuación (2) al modelo de **farmacocinética de primer orden**, y las Ecuaciones (3) y (4) a modelos empíricos obtenidos mediante descubrimiento simbólico de ecuaciones con la herramienta **Eureqa**. La descripción de cada modelo se realiza a continuación.

En la Ecuación (1), $x(t)$ representa la fracción acumulada de fármaco liberado al tiempo $t$. El parámetro $k$ es la constante de liberación y $n$ es el exponente difusional, cuyo valor determina el mecanismo de transporte: valores de $n \leq 0.43$ indican una **difusión Fickiana** a través de una geometría esférica, consistente con la morfología nanométrica del hidrogel.

En la Ecuación (2), $x(t)$ es igualmente la fracción liberada, $\beta$ representa la fracción máxima alcanzable de liberación y $k$ es la constante de velocidad asociada al proceso de primer orden. Este modelo asume que la tasa de liberación es proporcional a la cantidad de fármaco aún retenida en el hidrogel.

En la Ecuación (3), $\rho_1$ y $\rho_2$ son parámetros empíricos identificados por Eureqa a partir de los datos experimentales. El término lineal en $t$ representa una tendencia de liberación creciente, mientras que el término cuadrático $\rho_2 \cdot t^2$ modela la desaceleración de la liberación conforme el sistema se agota.

En la Ecuación (4), formulada como una ecuación diferencial ordinaria (EDO), $\dot{x}$ es la tasa instantánea de liberación, el término constante $2.28$ representa una tasa basal de liberación y $\rho_1 \cdot x$ modela el efecto inhibitorio de la fracción ya liberada sobre el proceso de liberación restante.

El sistema es evaluado bajo dos condiciones fisiológicas contrastantes: **pH 7.4 y 37 °C**, que simulan tejido sano, y **pH 6.0 y 40 °C**, que simulan las condiciones del microambiente tumoral. La diferencia en el comportamiento de liberación entre ambas condiciones está vinculada al carácter dual temperatura/pH del nanohidrogel, cuya temperatura de transición $T_{tr}$ se desplaza en función del pH debido a la ionización parcial de los grupos carboxílicos del 2MBA.

Palabras clave: Nanohidrogeles, Solución de EDOs, Simulaciones numéricas, Liberación controlada, Modelo matemático

## Actividades a realizar 
1. **Carga de datos experimentales**
Se ingresaron los datos tabulados de liberación acumulada de 5FU en función del tiempo (en minutos) para cuatro nanohidrogeles: N45, N32, N35 y N36-2MBA3. Dichos datos fueron extraídos directamente de las figuras del artículo de referencia (González-Ayón et al., 2015).

2. **Implementación de funciones de ajuste en MATLAB**
Se programaron las cuatro funciones de ajuste como funciones anónimas o de handle en MATLAB, correspondientes a los modelos de Peppas, farmacocinética de primer orden, Eureqa algebraico y Eureqa EDO, para su uso posterior en la regresión no lineal.

3. **Regresión no lineal con el modelo de Peppas**
Se ajustó la ecuación $x(t) = kt^n$ a los datos experimentales del nanohidrogel N36-2MBA3. Se estimaron los parámetros $k$ y $n$, y se evaluó la calidad del ajuste mediante el coeficiente de determinación $r^2$.

4. **Regresión no lineal con el modelo de farmacocinética de primer orden**
Se ajustó el modelo $x(t) = \beta(1 - e^{-kt})$ a los mismos datos experimentales. Se estimaron los parámetros $\beta$ y $k$, y se comparó su desempeño con el modelo de Peppas.

5. **Ajuste con modelos empíricos de Eureqa**
Se ajustaron los modelos empíricos obtenidos por descubrimiento simbólico de ecuaciones: el modelo algebraico $x(t) = \rho_1 + t - \rho_2 t^2$ y la EDO $\dot{x} = 2.28 - \rho_1 x$. Para el caso de la EDO, se resolvió numéricamente con `ode49` dentro del proceso de optimización.

6. **Comparación estadística de modelos**
Se compararon los cuatro modelos ajustados mediante criterios bioestadísticos, principalmente el coeficiente de determinación $r^2$, para determinar cuál describe mejor la cinética de liberación del fármaco desde el nanohidrogel N36-2MBA3.

7. **Visualización de resultados**
Se generaron gráficas en MATLAB que superponen los datos experimentales con las curvas ajustadas de cada modelo, permitiendo una evaluación visual del desempeño de cada uno bajo las condiciones fisiológicas y tumorales estudiadas.

## Lista de archivos incluidos en el repositorio
1. Cuaderno computacional de MATLAB [.mlx].
2. Imagénes de las simulaciones [.pdf].

## Referencias
\[1] P. A. Valle, Syllabus para Gemelos Digitales, Tecnológico Nacional de México / Instituto Tecnológico de Tijuana, Tijuana, B.C., México, 2025. Permalink: https://biomath.xyz/course/

\[2] González-Ayón, M. A., Sañudo-Barajas, J. A., Picos-Corrales, L. A., & Licea-Claverie, A. (2015). PNVCL-PEGMA nanohydrogels with tailored transition temperature for controlled delivery of 5-fluorouracil. *Journal of Polymer Science, Part A: Polymer Chemistry, 53*(23), 2662–2672. https://doi.org/10.1002/pola.27766
