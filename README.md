# 5 Trucos de python

Hoy os quiero presentar 5 maneras de python para programar que quizás sabias pero que nunca te han explicado de una manera que puedas entender. 

## 1 - Fucion Recursiva
Son funciones que se llaman así mismas. Suele utilizarse para dividir una tarea en subtareas más simples de forma que sea más fácil abordar el problema y solucionarlo. Estas funciones se detienen cuando alcanzan un caso base, es decir, una condición que les indica que deben dejar de llamarse a sí mismas y devolver un valor.

### Cuando la utilizaremos:
Resuelve problemas que implican la repetición de un proceso, como la búsqueda o el cálculo matemático. En lugar de una solución iterativa, la recursión utiliza funciones que se llaman a sí mismas para encontrar la solución final.

## Nota:
Algo muy importante a tener en cuenta es que si realizamos demasiadas llamadas a la función, podríamos llegar a tener un error del tipo RecursionError.
También tenemos que tener en cuenta que usar funciones recursivas tiene un coste de recursos, tanto de memoria como de calculo, importante por lo que si no es totalmente necesario siempre es preferible iterar, con bucles 'for' o 'while', que usar una función recursiva. 

### Ejemplo:
Os presento un ejemplo común de uso de la recursividad es, la función factorial. El factorial de un número n se define como la multiplicación de todos sus números predecesores hasta llegar a uno.

```python
def factorial(n):
    if n == 1:
        return 1
    else:
        return n * factorial(n-1)

print(factorial(5))
```

### Salida:

```text
120
```

### Explicación de la función:
En cada llamada a si misma va creando un stack en la pila de si misma con el valor de n pero sin devolver nigún valor hasta que n vale 1, en ese momento se cumple la condición 'if n == 1:' y retorna 1, al haber un retorno, 1, se van eliminando todos los stacks anteriores y se va ejecutando el 'else: return n * factorial(n-1)' que sería:

return ( 1 * 1 )
return ( 2 * 1 ) 
return ( 3 * 2 )
return ( 4 * 6 )
return ( 5 * 24)

En este link podréis ver como se ejecuta este código para poder entenderlo mejor:

[https://pythontutor.com](https://pythontutor.com/visualize.html#code=def%20factorial%28n%29%3A%0A%20%20%20%20%23%20print%28n%29%0A%20%20%20%20if%20n%20%3D%3D%201%3A%0A%20%20%20%20%20%20%20%20return%201%0A%20%20%20%20else%3A%0A%20%20%20%20%20%20%20%20return%20n%20*%20factorial%28n-1%29%0A%0Aprint%28factorial%285%29%29&cumulative=false&heapPrimitives=nevernest&mode=edit&origin=opt-frontend.js&py=3&rawInputLstJSON=%5B%5D&textReferences=false)



## 2 - Operador ternario
Los operadores ternarios son más conocidos en Python como expresiones condicionales. Estos operadores evalúan si una expresión es verdadera o no.

### Cuando la utilizaremos:
Se debe usar para situaciones muy sencillas y en ningún caso se debería abusar de él. Ante la duda, usa un if normal.

### Estructura:

```python
<Se evalúa si es cierto> if <condición> else <se evalúa si es falso>
```

### Ejemplo:
```python
x = 43
result = ‘respuesta correcta’ if x == 42  else ‘respuesta incorrecta’

result # contendrá  ‘respuesta incorrecta’
```


## 3 - Función Lambda
También conocidas como funciones anónimas, las funciones lambda son una forma corta de declarar funciones pequeñas y anónimas. Las llamamos “funciones anónimas” porque técnicamente carecen de nombre.

### Cuando la utilizaremos:
Una función lambda se usa cuando necesitas una función sencilla y de rápido acceso. 

### Estructura
La sintaxis de una función lambda es ```lambda args: expresión```. 

```text
Escribo p1 y p2 como parámetros 1 y 2 de la función.

lambda p1, p2: expresión
```

Primero escribes la palabra clave lambda, dejas un espacio, después los argumentos que necesites separados por coma, dos puntos :, y por último la expresión que será el cuerpo de la función.

### Ejemplo:

```python
#Aquí tenemos una función creada para sumar.
def suma(x,y):
    return(x + y)

#Aquí tenemos una función Lambda que también suma.
lambda x,y : x + y

#Para poder utilizarla necesitamos guardarla en una variable.
suma_dos = lambda x,y : x + y
```


## 4 - Función filter()
filter() es una función para iterar sobre un iterable exitente donde podrás filtrar su contenido mediante una función condicional. filter() creará un objeto iterable de tipo filter que podrás recorrer con un "for".

### Cuando la utilizaremos:
La función filter() puede usarse para crear un nuevo iterador a partir de un iterable existente (como una lista o un diccionario) que filtrará de forma eficiente los elementos usando una función que proporcionamos.

### Estructura
La sintaxis de una función filter() es ```filter(function, objecto iterable)```

### Ejemplo:
Por ejemplo, supongamos que tenemos una lista varios números y queremos filtrarla, quedándonos únicamente con los múltiples de 5...

```python
def multiple(numero):    # Primero declaramos una función condicional
    if numero % 5 == 0:  # Comprobamos si un numero es múltiple de cinco
        return True      # Sólo devolvemos True si lo es

numeros = [2, 5, 10, 23, 50, 33]

filter(multiple, numeros)
```

```python
<filter at 0x257ac84abe0>
```

Si ejecutamos el filtro obtenemos un objeto de tipo filtro, pero podemos transformarlo en una lista fácilmente haciendo un cast (conversión):

```python
list( filter(multiple, numeros) )

[5, 10, 50]
```

## 5 - Función map()
En Python, la función map nos permite aplicar una función sobre los items de un objeto iterable (lista, tupla, etc...).

### Cuando la utilizaremos:
El uso de map es especialmente útil si quieres aplicar una misma función a cada uno de estos elementos, que luego puedes pasar a la función como parámetro

### Estructura:
La sintaxis de la función map() es ```map(function, objeto iterable) ```

### Ejemplo:

Queremos multiplicar los números de dos listas:

```python
a = [1, 2, 3, 4, 5]
b = [6, 7, 8, 9, 10]

list( map(lambda x,y : x*y, a,b) )
```

```bash
[7, 9, 11, 13, 15]
```