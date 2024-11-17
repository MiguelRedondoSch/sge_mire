# **Sistema de Gestión de Tareas Pendientes**
### **Descripción del proyecto**
Crear una aplicación de consola que permita gestionar una lista de tareas. Cada tarea tendrá, por lo menos, las siguientes propiedades:

- Nombre de la tarea
- Prioridad
- Fecha límite
- Si está completada o no.
- Opcionalmente, podrás añadirle nuevas propiedades si quieres ampliar la funcionalidad de tu aplicación.

### **Funcionalidades**
- **Añadir tarea:** solicitará al usuario los datos de la tarea (nombre, prioridad y fecha límite) y los guardará en una lista de diccionarios.
- **Listar tareas:** mostrará todas las tareas pendientes, indicando sus detalles y resaltando si alguna está vencida.
- **Marcar tarea como completada:** cambiará el estado de una tarea a completada usando el índice.
- **Eliminar tarea:** permitirá al usuario borrar tareas que ya no necesita.
- **Guardar y cargar desde fichero:** Al salir, guardar las tareas en un fichero CSV, y al iniciar, cargar las tareas previamente guardadas.
- **Tareas vencidas:** opcionalmente dispondrá de la posibilidad de notificar al usuario sobre las tareas que han vencido.

```python
from datetime import datetime

tareas = []

def añadirTarea():
    """
    Añade una tarea a la lista de tareas. 
    Solicita al usuario el nombre, la prioridad y la fecha límite de la tarea.
    """
    nombre = input("Nombre: ")
    prioridad = input("Prioridad: ")
    fechaLimite = input("Fecha limite: ")
    while True:
        try:
            datetime.strptime(fechaLimite.strip(), "%d/%m/%Y")
            break
        except:
            fechaLimite = input("El formato de fecha debe ser (dd/mm/yyyy) por ejemplo 31/12/2005: ")
    tareas.append({"nombre": nombre, "prioridad": prioridad, "fechaLimite": fechaLimite, "completada":False})
    print(f"Tarea añadida: Nombre: {nombre}, Prioridad: {prioridad}, FechaLimite: {fechaLimite}, Completada: No")


def listarTareas():
    """
    Lista todas las tareas actualmente almacenadas en la lista de tareas.
    Muestra el nombre, la prioridad, la fecha límite y si la tarea está completada o no.
    """
    i = 0
    print("----- Tareas -----")
    for tarea in tareas:
        i+=1
        print(f"Tarea {i}: Nombre: {tarea["nombre"]}, Prioridad: {tarea["prioridad"]}, FechaLimite: {tarea["fechaLimite"]}, Completada: {"Si" if tarea["completada"] else "No"}")
    print("----- Tareas -----")

def marcarComoCompletada():
    """
    Permite al usuario marcar una tarea como completada. 
    Muestra la lista de tareas y solicita al usuario que ingrese el número de la tarea a marcar.
    """
    listarTareas()
    while True:
        index = input("Dame el número de la tarea que quieres marcar como completada: ")
        if index.isdigit() and int(index) >= 0 and int(index) <= len(tareas):
            index = int(index) - 1
            break
        else:
            print(f"Entrada inválida. Debe ser un número entre {1} y {len(tareas)}.")
    if 0 <= index < len(tareas):
        tareas[index]["completada"] = True
    else:
        print("No se ha encontrado la tarea")
    listarTareas()

def eliminarTarea():
    """
    Permite al usuario eliminar una tarea de la lista. 
    Muestra la lista de tareas y solicita al usuario que ingrese el número de la tarea a eliminar.
    """
    listarTareas()
    while True:
        index = input("Dame el número de la tarea que quieres eliminar: ")
        if index.isdigit() and int(index) >= 0 and int(index) <= len(tareas):
            index = int(index)-1
            break
        else:
            print(f"Entrada inválida. Debe ser un número entre {1} y {len(tareas)}.")
    if 0 <= index < len(tareas):
        tareas.pop(index)
    else:
        print("No se ha encontrado la tarea")
    listarTareas()

def guardarYCargar():
    """
    Permite al usuario cargar tareas desde un archivo. 
    Solicita el nombre del archivo y lee las tareas en el formato especificado (nombre, prioridad, fecha límite).
    Valida el formato de la fecha límite.
    """
    filename = input("Que cual es el fichero que quieres importar (en el directorio padre) (las propiedades separdas por comas y tareas por lineas: nombre, prioridad, fecha limite): ")
    try:
        with open(filename, "r") as file:
            for line in file:
                properties = line.strip().split(",")
                try: 
                    fechaLimite = properties[2]
                    datetime.strptime(fechaLimite.strip(), "%d/%m/%Y")
                    tareas.append({"nombre": properties[0], "prioridad": properties[1], "fechaLimite": fechaLimite, "completada": False})
                except Exception:
                    print("El archivo no tiene el formato solicitado de la fecha, debe ser (dd/mm/yyyy) por ejemplo 31/12/2005:")
    except FileNotFoundError:
        print(f"Error: El archivo '{filename}' no se encontró.")

def listarVencidas():
    """
    Lista las tareas que han vencido, es decir, cuya fecha límite ha pasado.
    Muestra el nombre, la prioridad, la fecha límite y si la tarea está completada o no.
    """
    i = 0
    print("----- Tareas Vencidas -----")
    for tarea in tareas:
        i += 1
        if datetime.now() > datetime.strptime(tarea["fechaLimite"].strip(), "%d/%m/%Y"):
            print(f"Tarea {i}: Nombre: {tarea['nombre']}, Prioridad: {tarea['prioridad']}, FechaLimite: {tarea['fechaLimite']}, Completada: {'Si' if tarea['completada'] else 'No'}")
    print("----- Tareas Vencidas -----")

def menu():
    """
    Muestra el menú principal de la aplicación y permite al usuario seleccionar una opción.
    Llama a las funciones correspondientes según la opción elegida.
    """
    print("""
------------------- MENU -------------------
0. Salir de Menu
1. Añadir Tarea (Fecha: dd/mm/yyyy)
2. Listar Tareas
3. Marcar como completada
4. Eliminar Tarea
5. Guardar y Cargar tarea desde fichero
6. Tareas vencidas""")
    while True:
        eleccion = input("Elige una opción (0-6): ")
        if eleccion.isdigit() and int(eleccion) >= 0 and int(eleccion) <= 6:
            eleccion = int(eleccion)
            break
        else:
            print("Entrada inválida. Debe ser un número entre 0 y 6.")
    match eleccion:
        case 0:
            SystemExit
        case 1:
            añadirTarea()
            menu()
        case 2:
            listarTareas()
            menu()
        case 3:
            marcarComoCompletada()
            menu()
        case 4:
            eliminarTarea()
            menu()
        case 5:
            guardarYCargar()
            menu()
        case 6:
            listarVencidas()
            menu()

menu()
```