Abrir @Risk y start tools

statistical inference -> hypothesis test mean/ 

standar desviation

Null hypotesis = se da planteada en el ejercicio

Rechazo desde @Risk

p < alfa (La rentabilidad promedio de la empresa es estadisticamente significativa)

No se rechaza

p>=alfa (La rentabilidad promedio diaria de empresa es estadisticamente igual a cero)

----------------------------------------------------------------------------------------------
Excel -> PH para la media

*Media -> +promedio(dato1:ultimoDato)

*Desviacion -> +desvEst.M(dato1:ultimoDato)

*ValorCrit -> +distr.t.inv(alpha;n-1)

*Estadistico de prueba -> +(Media-Ha)*raiz(n)/desvEstan

*Decision -> +Si(ABS(estadistico)>valorCrit;"Se rechaza Ho; "No se rechaza Ho)

*ValorP -> +2 * distr.t.cd(abs(estadistico);n-1)

interpretacion:

*Se rechaza Ho ya que la rentabilidad promedio diaria es diferente de cero

*Se acepta Ho ya que la rentabilidad promedio es estadisticamente igual a cero

------------------------------------------------------------------------------------------------

PH volatilidad

Nota:

Menor: Ho: Sigma = 1.6%  Ha: Sigma < 1.6%

Mayor: Ho: Sigma = 1.6%  Ha: Sigma > 1.6%

diferente: Ho: Sigma = 1.6%  Ha: Sigma != 1.6%

si es menor -> chi(1-aplha)

si es mayor -> chi(alpha)

si es diferente -> si estadistico>chi(alpha/2) o estadistico<chi(1-alpha/2)

Ej con menor de 1.6%

Ho: Sigma = 1.6%  Ha: Sigma < 1.6%

*chi(1-alpha,n-1) -> +inv.chicuad.cd(1-alpha; n-1)

*Estadistico -> +((n-1)*Ha^2/desvEstan^2)

*Desicion

+si(estadistico<chi(1-alpha;n-1); "Se rechaza Ho"; "No se rechaza Ho"

interpretacion:

Se rechaza Ho:

La volatilidad promedio de empresa es menor o mayor o diferente que el valor de Ha(1.6)

se acepta Ho:

No se tiene suficiente evidencia estadistica

------------------------------------------------------------------------------------------------

PH razon de varianzas

Ej Ho: Sigma empresa1 = Sigma empresa2

Se usa alpha/2 cuando es diferente (!=)

*F(alpha/2, n-1, m-1) -> distr.f.inv(alpha/2;n-1;m-1)

*F(1-alpha,n-1,m-1) -> distr.f.inv(1-alpha;n1-1;n2-1)

*Estadistico de prueba -> DesEs^2Emperesa1/DesEst^2Empresa2

Desicion:

+Si((estadistico<f(1-alpha);"Se rechaza Ho";"No se rechaza Ho)

Si es diferente (!=):

+Si((estadistico<f(alpha/2);"Se rechaza Ho";"No se rechaza Ho")

Interpretacion:

La volatilidad de la empresa1 es menor que volatilidad empresa2

------------------------------------------------------------------------------------------------

PH para diferencia de medias

------------------------------------------------------------------------------------------------

IC Media
*alpha(lo que le falta de la probabildad 1-probalidad dada)

*t(alpha/2) -> Distr.t.inv()

*Encontrar n -> +contar(dato1:ultimoDato)

*Media -> +promedio(dato1;ultimoDato)

*Desviacion -> +desvest.M(dato1;ultimoDato)

*ValorCrit -> +distr.inv(alpha;n-1)

*Margen error -> (valorCrit * desviacion)/raiz(n)

*Limite inferior -> +media - margenError

*Limite sup -> +media+MargenError

*MargenErrorExc -> +intervalo.confianza.t(alpha;desvEstandar;n)

Interpretacion:

Media = La rentabilidad promedio es con una confianza del 95%(dado en el problema) se espera
que la verdadera rentabilidad promedio se encuentre entre LI y LS

------------------------------------------------------------------------------------------------

IC Varianza

*n-1 -> +contar(dato1:ultimoDato)-1

*Varianza muestral -> +var.s(dato1:UltimoDato)

*chi(alpha/2) -> +inv.chicuad.cd(alpha/2;n-1)

*chi(1-alpha/2) -> +inv.chicuad.cd(1-(alpha/2);n-1)

*LI -> n-1 * varianzaMueltral/chi(alpha/2)

*LS -> n-1 * varianzaMuestal/chi(1-alpha/2)

*LI desv -> +raiz(LI)

*LS desv -> +raiz(LS)

Interpretacion:

La volatilidad con una confianza del 95%(dada en el problema) de que la empresa mueva entre
LI desv y LS desv

------------------------------------------------------------------------------------------------

IC razon de varianza

*var1/var2 -> Dividir las varianzas de IC Varianza

*f(alpha/2)(empresa1)(empresa2) -> +distr.f.inv(alpha/2; n-1empresa1; n-1empresa2)

*LI -> +varianzaEmpresa1/varianzaEmpresa2/f(aplha/2)

*LS -> +varianzaEmpresa1/VarianzaEmpresa2/f(1-alpha/2)

si LS < sigma1 < sigma2 -> riesgo menor

si LI > sigma1 > sigma2 -> riesgo menor

si Li<1 y Li >1 (sigma1 = sigma2) -> riesgo igual

------------------------------------------------------------------------------------------------

IC Diferencia de medias

*n+m-2 -> +contar(n1+n2) - 2

*desviacionEstandar -> +raiz(((n-1) * varianzaMuestral1 + (n2-1) * varianzaMues2))/n+m-2)

*raiz(1/n+1/m) -> +raiz((1/n1 + (1/n2)))

*valor critico -> +distr.t.inv(alpha;n+m-2)

*Margen de error -> +ValorCritico * raiz(1/n+1/m)*desvEst

*LI -> +media1 - media2 - margenError

*Ls -> +media1 - media2 + margenError

interpretacion:

si LI > 0 u1 >u2

si LS < 0 u1<u2

si LI < 0 y LS > 0   u1 = u2  estadisticamente igual

------------------------------------------------------------------------------------------------

*Nota: si los datos son discretos se elige chi y no kolmogorov (discreto -> Numero ocurrencias)

Bondad de ajuste

Abrir risk y abrir starTools

Verificar que este el simbolo decimal este activiado para que funcione el risk
*Opciones -> avanzadas -> Usar separadores del sistema

*Señalar todo el vector de datos

entrar en @Riks -> Fit -> fit -> Data - continuos -> Bootstrap - activar -> Results - kolmogorov

luego seleccionar la distribucion que mas se ajuste a los datos (ej: Laplace, Logistic etc)

entrar a statical summary (una  malla en la parte de abajo) buscar ahi el kolmogorov y fijarse en el p-value
con ese p-value se toma la decision.

Ho: Empresa siguen una distribucion (la que se tome la decision)
Ha: Empresa no siguen una distribucion (la que se tome en la decision)

ahora el valor - p se compara con alfa(que lo da el probelma)

si se obtiene que 

valor-p >= alfa -> No se rechaza la hipotesis nula Ho por lo tanto los retornos diarios de le empresa
siguen una distribucion (la que se tomo la decision)

Valor-p < alfa -> se rechaza la hipotesis nula (Ho) por lo tanto la empresa no siguen una 
distribucion(La que se quiere evaluar)

*Luego de elegir una distribucion volvemos al grafico.

Write to excel -> next -> elegir la celda -> colocarle el nombre de la distribucion a la celda

*Ahora hace falta encontrar PT(es el ultimo precio empresa) y P(T+1)
-p(T+1) -> +PT * EXP(DistribucionEncontrada)

*Ahora hubicados en P(T+1) abrir @Risk

Output-> Define

Luego en el menu de arriba en iterations -> 10.000

Resivsar en settigns-> General -activar montecarlo -> sampling - multiple simulatuons (Different seeds)

*Luego darle simulate -> Start simulation

*Luego interpretar los resultados de la grafica (con una confianza del x% se espera que este 
entre xvalor y xvalor)

*Para encontrar un percentil (solo se modifican los valores que estan en % en la grafica del risk)

interpretacion pertentil(ej 92):

Con una confianza del 8% se espera que el precio de la empresa este por encima de 239

------------------------------------------------------------------------------------------------
Regression Lineal.
Ej:

y = consumo de cafe (medido en tazas diarias por persona)

x = precio del cafe en dolares

B1 = por cada dolar que se incremente el precio del cafe se espera que el consumo disminuya en x tazas
diarias

B0 = el consumo promedio de cafe que no depende del precio es de (valor sin la x) tazas diarias por persona

------------------------------------------------------------------------------------------------

Para regresion lineal

Vamos a Datos -> Analisis de datos -> Resion -Tomamos todos los valores de Y- -Tomamos todos los valores de x

Si tomamos los valores de x y de y con los nombres activamos rotulos, tambien activar

Residuos y residuos estandares 

el que esta asociado a la intercepcion es Bo y el que esta asociado al otro es B1

------------------------------------------------------------------------------------------------
Ej: Gastos semanales en cientos de dolares en publicidad (x)

Ventas semanales en cientos de dolares(Y)

*Interpretaciones 

Bo -> es en coeficientes el que esta en intercepcion

B1 -> el otro el que va en x

*y = Bo + B1xi -> asi se hace el modelo

por cada tales dolares en (lo que estan en la columna x en los datos) se espera que (el dato 
de la columna y)

------------------------------------------------------------------------------------------------

Ic en regrecion ej con 95%

si LI < 0 y LS > 0 -> esto indica que la variable xi no es significativa en el modelo

interpretacion.

por cada 100 dolares adicionales de gastos semanales en publicidad se espera que con una confianza
del 95% que las ventas semanales promedio se encuentren entre 9.19(LS) y 13.75(LI)

Limite estan en donde dice:

inferior y superior en la segunda fila la que esta abajo de intercepcion

------------------------------------------------------------------------------------------------
Prueba hipotesis pendiente.

Hay dos casos 

caso1:

Ho: B1 = 0    ha B1!= 0  -> Rechazar Ho indica que la variable x tiene un efecto lineal sobre las variaciones de yi

No rechazar Ho indica que la variable xi no es significativa par el modelo

Decision:

Se rechaza si abs(T) > t(alpha/2, n-2) o tambien si valor-p < alpha

caso 2:

Ho: B1 = 1     Ha: B1 != 1 -> Rechazar Ho significa que no existe una relacion uno a uno entre x e y

No rechazar indica que existe una relacion uno a uno entre x e y

Interpretacion:

*En el mismo cuadro en excel fijarse en el estadistico T segunda fila

sacar el t(alpha/2, n-2) -> +distr.t.inv(0,05;n-2)

comprar T>t(alpha/2, n-2) se rechaza entonces los gastos semanales tienen un efecto lineal sobre las variaciones que hay en las ventas

Tambien se puede mirar el valor-p en la misma fila

valor-p < alpha se rechaza -> en el ejemplo 0 < 0.05

------------------------------------------------------------------------------------------------

Probar si el modelo lineal es significativo (alpha dado por el problema)

Se rechaza Ho si F> f(alpha, 1, n-2)

En analisis de varianza en excel

F -> este valor esta solo sin nada mas en la columna

calcular el f(alpha,1, n-2) -> +distr.f.inv(alpha, regresion, residuos)

Si se rechaza:

F es mayor que f entonces se rechaza Ho por lo tanto el modelo lineal es significativo

------------------------------------------------------------------------------------------------

Calcule el coeficiente de determinacion y el coeficiente de correlacion:

R^2 -> se mira en el resumen (cambiar el valor a porcentual)

Interpretacion:

La variabilidad que hay en las ventas semanales son explicadas en un 79%(R^2) por la variabilidad que hay en
en los gastos semanales en publicidad

Rxy -> coeficiente de correlacion multiple en excel

Existe una relacion lineal fuerte entre los gastos y las ventas semanales 

------------------------------------------------------------------------------------------------

Calcule y interprete un intervalo de confianza del 95% - Pronosticos

LI < UYo|Xo < LS  -> Uyo|Xo el pronostico promedio de la variable Yi

Xo -> valor que da el problema por ejemplo 7820 si el enunciado dice cientos seria 7820/100

Beta0 -> intercepcion

Beta1 -> el de abajo de intercepcion

Yo ajustado -> +Bo+B1 * Xo

alpha

n -> observaciones

t(alpha/2;n-2) -> distr.t.inv(alpha/2; n-2)

s -> error tipico

promedio de x -> +promedio(todo el vector)

sxx -> +suma.cuadrados(TOdo el vector ejex) - n*orimediox

Margen error -> +t(alpha/2; n-2) * s * raiz((1/n) + (xo-promediox)^2/sxx)

LI -> +yo ajustado - margen error

ls -> +yo ajustado + margen error

se espera con una confianza del 95% que las ventas se encuentren entre LI y LS







