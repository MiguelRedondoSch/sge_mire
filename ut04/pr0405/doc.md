## **1.- Filtrado de una lista de números**
Usa filter para obtener solo los números pares de una lista de enteros.

```python
numeros = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
print(list(filter(lambda numero: numero % 2 == 0, numeros)))
```

## **2.- Mapeo de temperaturas**
Dada una lista de temperaturas en Celsius, usa map para convertirlas a Fahrenheit.

```python
celsius = [0, 20, 37, 100]
print(list(map(lambda Fahrenheit: (Fahrenheit * 9/5) + 32, celsius)))
```

## **3.- Suma acumulativa**
Utiliza reduce para obtener la suma acumulativa de una lista de números.

```python
from functools import reduce
numeros = [1, 2, 3, 4, 5]
print(reduce(lambda acc, numero: numero+acc,numeros,0))
```

## **4.- Palabras con cierta longitud**
Dada una lista de palabras, usa filter para encontrar las que tienen más de cinco letras y luego map para convertirlas en mayúsculas.

```python
palabras = ["perro", "gato", "elefante", "oso", "jirafa"]
print(list(filter(lambda palabra: len(palabra)>5, palabras)))
```

## **5.- Multiplicación de pares**
Dada una lista de números, utiliza filter, map y reduce para obtener el producto de los números pares.

```python
from functools import reduce
numeros = [1, 2, 3, 4, 5, 6]
pares = list(filter(lambda par: par%2==0, numeros))
resultado = reduce(lambda acc,numero: numero*acc,pares,1)
print(f"{resultado} (producto de {pares})")
```

## **6.- Combinar operaciones en listas anidadas**
Dada una lista de listas de enteros, usa map, filter, y reduce para obtener la suma de todos los números positivos.

```python
from functools import reduce
numeros = [[-3, 2, 7], [10, -5, 3], [0, 8, -2]]
positivos = []
for lista in numeros:
    positivos += list(filter(lambda positivo: positivo>0, lista))
resultado = reduce(lambda acc,numero: numero+acc,positivos,0)
print(f"{resultado} (suma de de {positivos})")
```

## **7.- Frecuencia de palabras**
Dado un texto, crea una función que use map y reduce para obtener la frecuencia de cada palabra. Ignora las mayúsculas y minúsculas y supón que no hay símbolos de puntuación.

```python
from functools import reduce

texto = "Hola hola mundo mundo cruel"
frase = texto.lower().split(" ")

def f(acc, value):
    if(value in acc):
        acc[value]+=1
    else:
        acc[value]=1
    return acc

acc = reduce(f,frase,{})
print(acc)
```

## **8.- Intersección de conjuntos**
Dadas dos listas de números, usa filter para obtener una lista de los elementos que están en ambas listas (sin usar conjuntos).

```python
from functools import reduce

lista1 = [1, 2, 3, 4, 5]
lista2 = [3, 4, 5, 6, 7]


def f(acc, value):
    if value in lista2:
        acc.append(value)
    return acc

result = reduce(f, lista1,[])
print(result)
```

## **9.- Agrupación de palabras por longitud**
Dada una lista de palabras, crea un diccionario donde la clave es la longitud de la palabra y el valor es una lista de palabras de esa longitud. Usa map y filter.

```python
from functools import reduce

palabras = ["sol", "luna", "estrella", "cielo", "mar"]

def f(acc, value):
    longPalabra = len(value)
    if longPalabra in acc:
        acc[longPalabra].append(value)
    else:
        acc[longPalabra] = [value]
    return acc

solution = reduce(f,palabras,{})
print(solution)
```

## **10.- Concatenación de listas de caracteres**
Dadas dos listas de caracteres, usa reduce para concatenarlas en una sola lista sin utilizar + o métodos de concatenación.

```python
from functools import reduce

lista1 = ['a', 'b', 'c']
lista2 = ['x', 'y', 'z']

def f(acc, char):
    return acc + [char]

resultado = reduce(f, lista1, []) + reduce(f, lista2, [])
print(resultado)
```

## **11.- Calificación de alumnos**
Dada una lista de tuplas con el nombre del alumno y su calificación, utiliza map y filter para obtener una lista con los nombres de los alumnos que han aprobado (nota >= 5).

```python
alumnos = [("Ana", 4), ("Bruno", 7), ("Clara", 5), ("David", 8)]

aprobados = list(filter(lambda alumno: alumno[1]>=5, alumnos))
print(list(map(lambda aprobado: aprobado[0], aprobados)))
```

## **12.- Calcular producto cartesiano**
Dadas dos listas de números, usa map para obtener el producto cartesiano de ambas listas, devolviendo una lista de tuplas.

```python
lista1 = [1, 2]
lista2 = [3, 4]

result=[]
print(list(map(lambda val: [lista1[0], val], lista2)) + list(map(lambda val: [lista1[1], val], lista2)))
```

## **13.- Pipe de transformaciones de listas**
Implementa una función que tome una lista de funciones y una lista de números, y aplique cada función de la lista en secuencia sobre la lista de números usando reduce.

```python
from functools import reduce

funciones = [lambda x: x*2, lambda x: x+3, lambda x: x-1]
numeros = [1, 2, 3]
result=[]
for num in numeros:
    result.append(reduce(lambda acc, func: func(acc), funciones, num))
print(result)
```

## **14.- Aplicar operaciones de cadena**
Dada una lista de cadenas, usa map y filter para crear una nueva lista con las cadenas que tengan más de tres letras y en las que todas las letras sean mayúsculas. Además, convierte el primer carácter en minúscula.

```python
palabras = ["HOLA", "MUNDO", "SOL", "CIELO", "mar", "banana"]

filterWord = list(filter(lambda word: len(word)>3 and word==(word.upper()), palabras))

filterWord = [word[0].lower() + word[1::] for word in filterWord]
    
print(filterWord)
```