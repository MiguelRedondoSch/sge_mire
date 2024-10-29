## **1. Contar vocales y consonantes**
Escribe una función que reciba una cadena y cuente cuántas vocales y consonantes contiene.

```python
s = input("Dime que quieres contar: ")
vocales = ["a","e","i","o","u"]
countVocales = 0
for i in vocales:
    countVocales += s.count(i)
countConsonantes = len(s) - countVocales
print(f"""Vocales: {countVocales}
Consonantes: {countConsonantes}""")
```

## **2. Invertir una cadena**
Crea un programa que invierta una cadena.

```python
s = "Pablito clavo un clavito, que clavito clavo Pablito"
invertido = []
for letra in list(s)[::-1]:
    invertido.append(letra)
print(''.join(invertido))
```

## **3. Verificar palíndromo**
Escribe un programa que verifique si una cadena es un palíndromo (se lee igual de izquierda a derecha y de derecha a izquierda).

```python
s = input("Dime un palíndromo: ")
print(f"La palabra {s} {"es" if s == s[::-1] else "NO es"} un palíndromo")
```

## **4. Contar palabras**
Crea una función que cuente cuántas palabras hay en una cadena, suponiendo que las palabras están separadas por espacios.

```python
s = input("Dime una frase: ")
palabras = s.split(" ")
print(f"Me has introducido {len(palabras)} palabras")
```

## **5. Eliminar caracteres repetidos**
Escribe una función que elimine los caracteres duplicados en una cadena, manteniendo solo la primera aparición de cada uno.

```python
s = input("Dime una frase: ")
letras = []
for letra in s:
    if(letra not in letras):
        letras.append(letra)
print("".join(letras))
```

## **6. Mayúsculas y minúsculas**
Escribe un programa que convierta las letras minúsculas de una cadena en mayúsculas y viceversa.

```python
s = input("Dame una frase: ")
result:str = ""
for letra in s:
    if(letra.isupper()):
        result+=letra.lower()
    else:
        result+=letra.upper()
print(result)
```

## **7. Invertir palabras de una cadena**
Escribe un programa que invierta el orden de las palabras de una cadena, manteniendo las palabras originales intactas.

```python
s = input("Dame un frase: ")
palabras = s.split(" ")
palabras.reverse()
print(" ".join(palabras))
```

## **8. Anagrama**
Crea un programa que verifique si dos cadenas son anagramas. Se considera que dos palabras son anagramas si tienen las mismas letras en diferente orden, por ejemplo, lácteo y coleta.

```python
word1 = input("Introduce una palabra: ")
word2 = input("Introduce otra palabra: ")
letras1 = sorted(list(word1))
letras2 = sorted(list(word2))
print(f"{word1} y {word2} {"son" if letras1 == letras2 else "NO son"} palabras anagromas")
```

## **9. Frecuencia de caracteres**
Crea una función que reciba una cadena y devuelva un diccionario con la frecuencia de cada carácter.

```python
#NO HECHO
```

## **10. Quitar caracteres alfanuméricos**
Escribe un programa que elimine todos los caracteres no alfanuméricos (como signos de puntuación) de una cadena.

```python
s = input("Dime una frase: ")
chars = list(s)
result = []
for char in chars:
    if char.isalnum():
        result.append(char)
    if char == " ":
        result.append(char)
print("".join(result))
```

## **11. Transformar a camelCase**
Escribe un programa que transforme una cadena de palabras separadas por espacios o guiones en formato camelCase (la primera letra de cada palabra, excepto la primera, debe ser mayúscula y no debe haber espacios ni guiones).

```python
s = input("Dime una frase: ")
s = s.title().replace(" ", "").replace("-", "")
s = s[0].lower() + s[1::]
print(s)
```

## **12. Codificación RLE (Run-Length Enconding)**
Escribe una función que implemente la codificación por longitud de ejecución (RLE), que consiste en comprimir una cadena representando las secuencias consecutivas de caracteres iguales con el carácter seguido de la cantidad de repeticiones.

Por ejemplo, la cadena aaron la reemplazaría por a2r1o1n1. Por simplicidad, puedes asumir que un carácter no se va a repetir más de 9 veces consecutivas.

```python
s = input("Dime una frase: ")
s+="*"
result=""
contador = 0
lastLetter = s[0]

for letter in s:
    #si la ultima letra es igual a la letra que toca ahora en la lista
    if(lastLetter == letter):
        contador+=1
        lastLetter = letter
    #si ya es una letra distinta poner contador a 1 y añadir la anterior letra y contador
    else:
        result+=lastLetter+str(contador)
        contador = 1
        lastLetter = letter
print(result)
```

## **13. Decodificar RLE**
Crea una función que decodifique una cadena que ha sido comprimida usando el método RLE.

```python
s = input("Dime una frase codificada en RLE: ")
result=""
letterToWrite = ""

for letter in s:
    if(letter.isnumeric()):
        result+= letterToWrite * int(letter)
    else:
        letterToWrite=letter
print(result)
```

## **14. Formateo de cadenas con plantillas**
Escribe un programa que tome una plantilla de cadena y un diccionario, y reemplace los marcadores en la plantilla por los valores correspondientes en el diccionario.

Ejemplo: la cadena "Hola, {nombre}" con el diccionario {"nombre": "Victor"} debería devolver "Hola, Victor"

```python
#NO HECHO
```

## **15. Comparar cadenas por valor ASCII**
Escribe una función que compare dos cadenas sumando el valor ASCII de cada carácter y devuelva cuál tiene un mayor valor total. Para este ejercicio ten en cuenta que la función integrada ord() devuelve el valor ASCII de un carácter

```python
str1 = input("Dime la primera frase: ")
str2 = input("Dime la segunda frase: ")
valorStr1 = 0
valorStr2 = 0

for letter in str1:
    valorStr1 += ord(letter)
    
for letter in str2:
    valorStr2 += ord(letter)

print(f"La primera frase es mayor" if valorStr1 > valorStr2 else "La segunda frase es mayor")
```

## **16. Contar la longitud de palabra más larga**
Escribe un programa que reciba una cadena y devuelva la longitud de la palabra más larga

```python
s = input("Dime una frase: ")
maxLen = 0
longWord = ""
words = s.split()
for word in words:
    if(len(word) > maxLen):
            maxLen = len(word)
            longWord = word
print(longWord)
```

## **17. Formatear número con separador de miles**
Escribe una función que tome un número de forma de cadena y le agregue separadores de miles.

Ejemplo: "123456756" debería convertirse en "123.456.789".

```python
num = input("Dame un numero: ")
contador=0
result = ""
for i in range(len(num) - 1, -1, -1):
    contador+=1
    if(contador%3==0):
        result+="."
    result+=num[::-1][i]
print(result)
```

## **18. Rotar caracteres de una cadena**
Escribe una función que rote una cadena hacia la izquierda un número dado de veces.

Ejemplo: "abcdef" rotado 2 veces convierte la cadena en "cdefab".

```python
inp = input("Dime una frase: ")
rotations = int(input("Cuantas veces quieres moverlo: "))
result = inp[rotations:]
result+= inp[:rotations]
print(result)
```