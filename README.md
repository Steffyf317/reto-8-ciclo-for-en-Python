# reto 8: ciclo for en Python
## 1.Imprimir un listado con los números del 1 al 100 cada uno con su respectivo cuadrado.
```python
for i in range(1,101,1): # se define una lista desde 1 a 100 (definiendola hasta n+1) con tamaño de paso igual a 1
  print(i,i**2) #se imprime cada elemento de la lista con su respectivo cuadrado
```
## 2.Imprimir un listado con los números impares desde 1 hasta 999 y seguidamente otro listado con los números pares desde 2 hasta 1000.
```python
range(1,1000,2) #se crea el rango de números
for num in range(1,1000,2): #se crea el ciclo 'para cada número del rango':
   print(num) #imprimir los elementos

range(2,10001,2)
for i in range(2,1001,2):
  print(i)
```
## 3.Imprimir los números pares en forma descendente hasta 2 que son menores o iguales a un número natural n ≥ 2 dado
```python
n = int(input("Ingrese un numero entero mayor o igual a 2: ")) # valor ingresado por teclado
for i in range(n, 0, -1): #recorre todos pero solo imprime los pares, por eso el tamaño del paso es 1
  if i % 2 ==0:
    print(i)
```
## 4.Imprimir los números de 1 hasta un número natural n dado, cada uno con su respectivo factorial.
```python
n = int(input("Ingrese un numero entero positivo: ")) #valor ingresado por teclado
f = 1 #se define el factorial del primer número de la lista
for i in range(1,n+1,1): #hacer una lista con los números hasta n
  f = i # se establece f en i para que la variable i no se altere en la siguiente iteraciòn
  for j in range(1, i): # el j es cada factor para cada i de la lista:
    f = f * j
  print(i, f)
```
## 5.Calcular el valor de 2 elevado a la potencia n usando ciclos for.
```python
n = int(input("Ingrese un numero entero: ")) #valor ingresado por teclado
resultado:int = 1 #primer numero de la iteracion
if n == 0: 
  print("2 elevado a la 0 es 1 ") #condicional que imprime el 2 elevado a la potencia 0 = 1
else:
  for i in range(n): #aqui se define el numero de veces que se debe multiplicar 2 por sí mismo 
    resultado = 2*resultado # resultado que guarda la potencia de la iteración anterior
  print ("2 elevado a la " +str(n)+ " es " +str(resultado))
```

## 6.Leer un número natural n, leer otro dato de tipo real x y calcular x^n usando ciclos for. Disclaimer: Trate de no utilizar el operador de potencia (**).
```python
x = float(input("Ingrese un número ")) #valores ingresados por teclado
n = int(input("Ingrese un número entero positivo ")) 
resultado:int = 1 #primer número de la iteración
if n == 0:
  print(+str(x)+ " elevado a la 0 es igual a 1 ") #condicional que imprime el x elevado a la potencia 0 = 1
else:
  for i in range(n): #número de veces que se multiplica x por sí mismo
    resultado = x*resultado #actualización de la variable de la potencia, teniendo en cuenta la iteración anterior
  print(str(x)+ " elevado a la " +str(n)+ " es " +str(resultado))
```

## 7.Diseñe un programa que muestre las tablas de multiplicar del 1 al 9.
```python
for i in range(1, 10): #se define una lista de 9 elementos (las 9 tablas)
  print("Tabla del", i) 
  for j in range(1, 11): #se definen los 10 elementos pertinentes para cada tabla, es decir, por cada i de la lista, se hace una sublista
    print(str(i) + " x " + str(j) + " = " + str(i*j))
```
## 8.Diseñar una función que permita calcular una aproximación de la función exponencial alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Maclaurin. Nota: use math para traer la función exponencial y mostrar la diferencia entre el valor real y la aproximación.
$$e^x \approx exp(x,n) \approx \sum_{i=0}^{n}\frac{x^i}{i!}$$
```python
import math #importar librería

x = float(input("Ingrese un valor para x en la serie de Mcclaurin ")) #valor ingresado por teclado
n: int = 30 #número de términos de la serie, estos se determinaron por ensayo y error de tal manera que el error fuese menor al requerido
suma : float = 0 # iniciar la sumatoria 
f:int = 1 #factorial del primer número i de la serie

for i in range(n+1): #lista de valores hasta n
  for j in range(1,i+1): #para cada i de la lista hacer una sublista de valores j hasta i
    f = j #se establece f en j para que la variable j no se altere en la siguiente iteración
    for k in range(1, j): # el k es cada factor para cada j de la lista
      f = f * k #actualizar la variable
  suma += (x**i)/f #definición de cada término de la serie para la exp

diferencia = abs((math.e**x - suma) /(math.e**x)) * 100 #cálculo del error
print("El valor de la función exponencial evaluado en " +str(x)+ " es aproximadamente de " +str(suma))
print("El error respecto a la función exponencial es del " +str(diferencia)+ " %")
```
## 9. Diseñar una función que permita calcular una aproximación de la función seno alrededor de 0 para cualquier valor x (real), utilizando los primeros n términos de la serie de Maclaurin. **Nota:** use *math* para traer la función seno y mostrar la diferencia entre el valor real y la aproximación.
$$sin(x) \approx sin(x,n) \approx \sum_{i=0}^{n} (-1)^i \frac{x^{2i+1}}{(2i+1)!}$$
```python
import math #importar librería

x = float(input("Ingrese un valor para x en la serie de Mcclaurin ")) #valor ingresado por teclado
n: int = 30 #número de términos de la serie, estos se determinaron por ensayo y error de tal manera que el error sea menor al requerido
suma : float = 0 #inicializar la variable de términos de la sumatoria
f:int = 1 #factorial del primer denominador de cada término de la sumatoria
for i in range(n+1): #lista de valores hasta n
  for j in range(1,(2*i+1)+1): #para cada i de la lista hacer una sublista de valores j hasta 2i+1
    f = j #se establece f en j para que la variable j no se altere en la siguiente iteración
    for k in range(1, j): # el k es cada factor para cada j de la lista
      f = f * k #actualizar la variable
  suma += ((-1)**i) * ((x**((2*i)+1))/(f)) #definición de cada término de la serie para el seno

diferencia = abs((math.sin(x) - suma) /(math.sin(x))) * 100 #cálculo del error
print("El valor de la función de seno en radianes, evaluado en " +str(x)+ " es aproximadamente de " +str(suma))
print("El error respecto a la función de seno reportada en la literatura es del " +str(diferencia)+ " %")
```
## 10.Diseñar una función que permita calcular una aproximación de la función arcotangente alrededor de 0 para cualquier valor x en el rango [-1, 1], utilizando los primeros n términos de la serie de Maclaurin. **Nota:** use *math* para traer la función arctan y mostrar la diferencia entre el valor real y la aproximación.
$$arctan(x) \approx arctan(x,n) \approx \sum_{i=0}^{n} (-1)^i \frac{x^{2i+1}}{(2i+1)}$$
```python
import math #importar librería

x = float(input("Ingrese un valor para x en la serie de Mcclaurin entre -1 y 1 ")) #valor ingresado por teclado
n: int = 10 #número de términos de la serie
suma : float = 0 # #inicializar la variable de términos de la sumatoria
for i in range(n+1): #lista de valores hasta n
  suma += (-1)**i * ((x**(2*i+1))/(2*i+1)) #definición de los términos de la serie para la arcotangente 

diferencia = abs((math.atan(x) - suma) /(math.atan(x))) * 100 #cálculo del error
print("El valor de la función arcotangente en radianes, evaluado en " +str(x)+ " es aproximadamente de " +str(suma))
print("El error respecto a la función reportada en la literatura es del " +str(diferencia)+ " %")
```
