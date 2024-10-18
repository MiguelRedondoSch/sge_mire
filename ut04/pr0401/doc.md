## **1. Lectura de un número válido**
Crea un programa que solicite un número por pantalla al usuario y siga pidiéndolo hasta que el usuario introduzca un número válido.

```python
n = input("Dame un numero: ")
while not n.isdigit():
    n = input("Dame un numero: ")
print(f"{n} es un numero")
```

## **2. Tabla de multiplicar**
Crea un programa que solicite un número n y un valor k y que muestre por la terminal los primeros k elementos de la tabla de multiplicar de n.

```python
n = int(input("Dame el numero del que quieras saber la tabla de multiplicar: "))
k = int(input("Cuantos quieres?: "))
i = 1
for num in range(k):
    print(f"{n} * {i} = {n * i}")
    i += 1
```

## **3. Triángulo de asteriscos**
Crea un programa que solicite un número al usuario y dibuje un triángulo con asteriscos cuya base sea el número introducido.

```python
n = input("Cuantas lineas quieres?: ")
texto = ""
for i in range(0,int(n)+1):
    for i in range(0, i):
        texto = texto + "*"
    print(texto)
    texto = ""
```

## **4. Pirámide de asteriscos**
Modifica el programa anterior para que en lugar de crear un triángulo cree una pirámide. Si el usuario introduce un número par se lo volverá a pedir hasta que introduzca un número par.

```python
while True:
    n = int(input("Cuantas lineas quieres?: "))
    if n % 2 == 0:
        break
    else:
        print("Debes de introducir un numero par")
texto = ""
for i in range(1, n + 1):
    texto = " " * (n - i) + "*" * (2 * i - 1)
    print(texto)
```

## **5. Número mayor y menor**
Crea un programa que pida al usuario que introduzca 5 números y luego le diga cuál es el mayor y el menor de todos ellos de la forma: El número mayor es <mayor> y el menor es <menor>

```python
min = 9999999
max = -1000000

for i in range(5):
    n1 = int(input("Dame un numero: "))
    if n1 < min:
        min = n1
    elif n1 > max:
        max = n1

print (f"El número mayor es {max} y el menor es {min}")
```

## **6. Conversión de unidades**
Crea un programa que convierta entre diferentes unidades de longitud (milímetros, centímetros, metros y kilómetros). El usuario introducirá primero la cantidad, luego la unidad de medida en que está y finalmente la unidad de medida a la que se va a convertir.

```python
num = input("Dame un numero: ")
while not num.isdigit():
    num = input("Dame un numero: ")
currentUnidad = input("En que unidad esta? (mm, cm, m, km): ")
nextUnidad = input("En que unidad quieres pasar  (mm, cm, m, km): ")

match currentUnidad:
    case "mm":
        resultado = int(num) / (10 if nextUnidad == "cm" else
                               (1000 if nextUnidad == "m" else
                                (1000000 if nextUnidad == "km" else 1)))
    case "cm":
        resultado = int(num) * (10 if nextUnidad == "mm" else
                               (0.01 if nextUnidad == "m" else
                                (0.00001 if nextUnidad == "km" else 1)))
    case "m":
        resultado = int(num) * (1000 if nextUnidad == "mm" else
                               (100 if nextUnidad == "cm" else
                                (0.001 if nextUnidad == "km" else 1)))
    case "km":
        resultado = int(num) * (1000000 if nextUnidad == "mm" else
                               (100000 if nextUnidad == "cm" else
                                (1000 if nextUnidad == "m" else 1)))

```

## **7. Acierta el número**
Crea un programa que genere un número aleatorio entre 0 y 100 y el usuario tenga que adivinarlo. Cada vez que el usuario introduzca un número el programa le dirá si el número es más alto o más bajo.

Para generar un número aleatorio puedes utilizar la función randint(a, b) que devuelve un entero aleatorio entre a y b. Para poder utilizar esta función antes tienes que importar la librería con la orden from random import *

```python
from random import randint


random = randint(0,100)
n = int(input("Adivina el numero: "))
while int(n)!=random:
    if n<random:
        print(f"El numero en el que pienso es mayor que {n}")
    elif n>random:
        print(f"El numero en el que pienso es menor que {n}")
    n = int(input("Adivina el numero: "))
print(f"Exacto es {random}!!!")
```

## **8. Piedra, papel, tijeras, Lagarto y Spock**
Crea un programa que implemente el clásico juego de piedra, papel, tijeras, lagarto y spock.

Las normas de este juego son:

Piedra aplasta a lagarto
Lagarto envenena a Spock
Spock rompe las tijeras
Tijeras decapitan al lagarto
Lagarto come al papel
Papel desautoriza a Spock
Spock vaporiza la piedra
Piedra rompe a tijeras
Tijeras cortan papel
Papel envuelve a piedra
En el enlace anterior puedes ver un diagrama donde tal vez veas mejor las relaciones entre las diferentes elecciones.

Ganará el primero que gane 5 manos.

```python
from random import randint

botPoints = 0
userPoints = 0

while userPoints < 5 and botPoints < 5:
    botOption = randint(0, 4)
    userOption = input("piedra, papel, tijeras, lagarto o spock: ").lower()
    
    while userOption != "piedra" and userOption != "papel" and userOption != "tijeras" and userOption != "lagarto" and userOption != "spock":
        userOption = input("piedra, papel, tijeras, lagarto o spock: ").lower()

    if botOption == userOption:
        print("Empate")
    elif (botOption == 0 and (userOption == "tijeras" or userOption == "lagarto")) or \
         (botOption == 1 and (userOption == "piedra" or userOption == "spock")) or \
         (botOption == 2 and (userOption == "papel" or userOption == "lagarto")) or \
         (botOption == 3 and (userOption == "spock" or userOption == "papel")) or \
         (botOption == 4 and (userOption == "tijeras" or userOption == "piedra")):
        print(f"Gano el bot: {botOption} vs {userOption}")
        botPoints += 1
    else:
        print(f"Gano el usuario: {userOption} vs {botOption}")
        userPoints += 1

    print(f"Bot : User\n{botPoints} : {userPoints}")
```

## **9.- Secuencia de Fibonacci**
Crea un programa que genere los primeros n números de la secuencia de Fibonacci.

```python
n = int(input("Como numero quieres generar: "))
sequence = [1, 1]
for i in range(n):
    n1 = sequence[-1]
    n2 = sequence[-2]
    sequence.append(n1 + n2)

print(sequence)
```