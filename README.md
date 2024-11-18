Abrir @Risk y start tools

statistical inference -> hypothesis test mean/ 

standar desviation

Null hypotesis = se da planteada en el ejercicio

Rechazo desde @Risk

p < alfa (La rentabilidad promedio de la empresa es estadisticamente significativa)

No se rechaza\n

p>=alfa (La rentabilidad promedio diaria de empresa es estadisticamente igual a cero)

----------------------------------------------------------------------------------------------
Excel -> PH para la media

*Media -> +promedio(dato1:ultimoDato)

*Desviacion -> +desvEst.M(dato1:ultimoDato)

*ValorCrit -> +distr.t.inv(alpha;n-1)

*Estadistico de prueba -> +(Media-Ha)*raiz(n)/desvEstan

*Decision -> +Si(ABS(estadistico)>valorCrit;"Se rechaza Ho; "No se rechaza Ho)

*ValorP -> +2*distr.t.cd(abs(estadistico);n-1)

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

