Abrir @Risk y start tools

statistical inference -> hypothesis test mean/ \n
standar desviation\n
Null hypotesis = se da planteada en el ejercicio\n

Rechazo desde @Risk\n
p < alfa (La rentabilidad promedio de la empresa es estadisticamente significativa)\n
No se rechaza\n
p>=alfa (La rentabilidad promedio diaria de empresa es estadisticamente igual a cero)\n
------------------------------------------------------------------------------------------------
Excel -> PH para la media\n
-Media -> +promedio(dato1:ultimoDato)\n
-Desviacion -> +desvEst.M(dato1:ultimoDato)
-ValorCrit -> +distr.t.inv(alpha;n-1)
-Estadistico de prueba -> +(Media-Ha)*raiz(n)/desvEstan
-Decision -> +Si(ABS(estadistico)>valorCrit;"Se rechaza Ho; "No se rechaza Ho)
-ValorP -> +2*distr.t.cd(abs(estadistico);n-1)

interpretacion:
-Se rechaza Ho ya que la rentabilidad promedio diaria es diferente de cero

-Se acepta Ho ya que la rentabilidad promedio es estadisticamente igual a cero

--------------------------------------------------------------------------------------------------