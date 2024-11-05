## **1. Buscar un valor en un diccionario:**
Crea un diccionario de frutas y precios. Permite al usuario ingresar el nombre de una fruta y muestra su precio si existe en el diccionario, o un mensaje de que no está disponible en caso contrario.

```python
frutas = {"Manzana": 1, "Pera": 1.20, "Platano": 1.50}

fruta = input("De que fruta quieres saber el precio? ")
if fruta in frutas:
    print(frutas.get(fruta))
else:
    print("No tenemos esa fruta")
```

## **2. Contar elementos en un diccionario:**
Suponiendo un diccionario con al siguiente estructura, crea un programa que calcule cuántas categorías hay, cuántos productos tiene cada categoría y cuántos productos hay en total.

```python
productos = {
    "Electrónica": ["Smartphone", "Laptop", "Tablet", "Auriculares", "Smartwatch"],
    "Hogar": ["Aspiradora", "Microondas", "Lámpara", "Sofá", "Cafetera"],
    "Ropa": ["Camisa", "Pantalones", "Chaqueta", "Zapatos", "Bufanda"],
    "Deportes": ["Pelota de fútbol", "Raqueta de tenis", "Bicicleta", "Pesas", "Cuerda de saltar"],
    "Juguetes": ["Muñeca", "Bloques de construcción", "Peluche", "Rompecabezas", "Coche de juguete"],
}

print(f"Hay {len(productos)} categorias")

total=0
for categoria in productos:
    print(f"{categoria}: {len(productos[categoria])}")
    total+=len(productos[categoria])

print(f"Total: {total}")
```

## **3. Contador de frecuencias de palabras:**
Escribe un programa que tome una frase y use un diccionario para contar la frecuencia de cada palabra.

```python
frase = input("Dame una frase: ")

fraseDic = {}
for palabra in frase.split():
    palabra = palabra.lower()
    if palabra in fraseDic:
        fraseDic[palabra] += 1
    else:
        fraseDic[palabra] = 1
print(fraseDic)
```

## **4. Diccionario de listas:**
Supón un diccionario donde cada clave es una asignatura y el valor correspondiente una lista de estudiantes matriculados, tal como se muestra en el diccionario de ejemplo. Crea un programa que tenga un menú con tres opciones:

- Listar estudiantes matriculados en una asignatura
- Matricular un estudiante en una asignatura
- Dar de baja un estudiante de una asignatura.

```python
def menu():
    option = input(
"""

1. Listar estudiantes matriculados en una asignatura
2. Matricular un estudiante en una asignatura
3. Dar de baja un estudiante de una asignatura.
4. Salir
""")
    match(int(option)):
        case 1:
            asignatura = input("Dime que asignatura: ")
            if asignatura in asignaturas:
                print(asignaturas[asignatura])
            else:
                print("No existe esa asignatura")
            menu()
        case 2:
            alumno = input("Nombre de alumno: ")
            asignatura = input("Asignatura: ")
            asignaturas[asignatura].append(alumno)
            print(asignaturas[asignatura])
            menu()
        case 3:
            alumno = input("Nombre de alumno: ")
            asignatura = input("Asignatura: ")
            if asignatura in asignaturas:
                asignaturas[asignatura].remove(alumno)
                print(asignaturas[asignatura])
            else:
                print("No existe el alumno")
            menu()
        case 4:
            print("Adios, vuelva pronto")
        case _:
            print("Solo existe las opciones 1, 2, 3 y 4")
            menu()

asignaturas = {
    "Matemáticas": ["Ana", "Carlos", "Luis", "María", "Jorge"],
    "Física": ["Elena", "Luis", "Juan", "Sofía"],
    "Programación": ["Ana", "Carlos", "Sofía", "Jorge", "Pedro"],
    "Historia": ["María", "Juan", "Elena", "Ana"],
    "Inglés": ["Carlos", "Sofía", "Jorge", "María"],
}
menu()
```

## **5. Diccionario invertido:**
Escribe una función que tome un diccionario y devuelva otro con las claves y valores intercambiados (lo que antes eran valores ahora son claves, y viceversa).

```python
dict = {"Miguel":9, "Piero":10, "Digule":7}
dict2 = {}
for value in dict.items():
    dict2.update({reversed(value)})
print(dict2)
```

## **6. Combinar dos diccionarios:**
Escribe un programa que tome dos diccionarios de productos y precios, y combine los productos comunes sumando sus precios, sin duplicar los elementos únicos.

```python
tienda1 = {"Moviles": 2030, "Laptops":1300, "Tablets":500}
tienda2 = {"Moviles": 970, "Laptops":700, "Tablets":500}
tienda3 = {}

for product in tienda1:
    tienda3[product] = tienda1[product]

for product in tienda2:
    if product in tienda3:
        tienda3[product] += tienda2[product]
    else:
        tienda3[product] = tienda2[product]

print(tienda3)
```

## **7. Filtrar claves y valores:**
Dado un diccionario de empleados y salarios, filtra e imprime solo los empleados con un salario mayor a un umbral definido.

```python
filtro = int(input("Dime un maximo de salario: "))
empleados = {"Miguel":1600, "Piero":1800, "Digule":1400}

i=0
for salario in empleados.values():
    if(salario >= filtro):
        print(f"{list(empleados.keys())[i]}: {salario}")
    i+=1
```

## **8. Anidación de diccionarios:**
Partiendo de un diccionario donde las claves son nombres de departamentos y los valores, diccionarios de empleados y sus puestos, tal como se ve en el código de ejemplo, crea un programa que permita realizar las siguientes funciones:

- Mostrar el listado de todos los empleados de un departamento
- Añadir un empleado a un departamento
- Eliminar un empleado de un departamento

```python
def menu():
    option = input(
"""

1. Mostrar el listado de todos los empleados de un departamento
2. Añadir un empleado a un departamento
3. Eliminar un empleado de un departamento
4. Salir
""")
    match(int(option)):
        case 1:
            departamento = input("Dime que departamento: ")
            if departamento in departamentos:
                for empleado, oficio in departamentos[departamento].items():
                    print(f"{empleado}: {oficio}")
            else:
                print("No existe ese departamento")
            menu()
        case 2:
            empleado = input("Nombre del empleado: ")
            oficio = input("Oficio del empleado: ")
            departamento = input("Departamento: ")
            if departamento in departamentos:
                departamentos[departamento][empleado] = oficio
                print(departamentos[departamento])
            else:
                print("No existe el departamento")
            menu()
        case 3:
            empleado = input("Nombre del empleado: ")
            departamento = input("Departamento: ")
            if departamento in departamentos:
                if empleado in departamentos[departamento]:
                    del departamentos[departamento][empleado]
                else:
                    print("No existe el empleado en el departamento")
                print(departamentos[departamento])
            else:
                print("No existe el departamento")
            menu()
        case 4:
            print("Adios, vuelva pronto")
        case _:
            print("Solo existe las opciones 1, 2, 3 y 4")
            menu()


departamentos = {
    "Recursos Humanos": {
        "Ana": "Gerente de Recursos Humanos",
        "Luis": "Especialista en Reclutamiento",
        "Elena": "Asistente de Recursos Humanos"
    },
    "Tecnología": {
        "Carlos": "Desarrollador Backend",
        "María": "Desarrolladora Frontend",
        "Pedro": "Administrador de Sistemas"
    },
    "Marketing": {
        "Sofía": "Directora de Marketing",
        "Jorge": "Especialista en SEO",
        "Laura": "Community Manager"
    },
    "Finanzas": {
        "Juan": "Analista Financiero",
        "Lucía": "Contadora",
        "Raúl": "Asesor Financiero"
    }
}
menu()
```

## **9. Transformación de datos:**
Dado un diccionario con claves como nombres de estudiantes y valores como una lista de calificaciones, haz un programa que:
- Cree un nuevo diccionario que contenga el promedio de calificaciones para cada estudiante
- Crea otro diccionario que contengan la nota promedio en cada asignatura

```python
estudiantes = {
    "Ana": {"Matemáticas": 8.5, "Física": 9.0, "Programación": 7.8},
    "Carlos": {"Matemáticas": 9.2, "Física": 8.8, "Programación": 9.4},
    "Luis": {"Matemáticas": 7.6, "Física": 8.0, "Programación": 8.5},
    "María": {"Matemáticas": 9.5, "Física": 10.0, "Programación": 9.8},
    "Jorge": {"Matemáticas": 8.8, "Física": 8.4, "Programación": 7.9},
    "Sofía": {"Matemáticas": 9.1, "Física": 8.9, "Programación": 9.3}
}

mediaAlumno=0
mediasAlumnos={}
for alumno in estudiantes:
    for nota in estudiantes.get(alumno).values():
        mediaAlumno+=nota
    mediasAlumnos[alumno] = mediaAlumno / len(estudiantes.get(alumno))
    mediaAlumno = 0
print(mediasAlumnos)

mediasAsignaturas = {}

for notas in estudiantes.values():
    for asignatura, nota in notas.items():
        if asignatura in mediasAsignaturas:
            mediasAsignaturas[asignatura] = (mediasAsignaturas[asignatura] + nota)/2
        else:
            mediasAsignaturas[asignatura] = nota

print(mediasAsignaturas)
```