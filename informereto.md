# Informe de la Calculadora de IVA

## Manual de Uso

Este programa de cálculo de IVA permite a los usuarios ingresar el precio de un producto sin IVA, calcular automáticamente el total con un IVA del 21% fijo y almacenar los cálculos en un historial. Los usuarios pueden ingresar sus nombres, ver el historial completo de cálculos realizados, y decidir si desean realizar otro cálculo o finalizar el programa. A continuación, se explica cómo utilizar el programa:

1. **Ingreso de Datos**: El usuario introduce su nombre y luego el precio sin IVA.
2. **Cálculo Automático**: El programa calcula automáticamente el IVA del 21% y muestra el precio total.
3. **Consulta del Historial**: Después de cada cálculo, el usuario puede optar por ver el historial de todos los cálculos realizados.
4. **Finalización del Programa**: Tras revisar los cálculos, el usuario puede decidir continuar con otro cálculo o finalizar el programa.

## Retos y Mejora del Proyecto en Equipo

### Retos
- **Comprensión de Requisitos**: Uno de los primeros desafíos fue interpretar correctamente las necesidades del cliente y las funcionalidades específicas del programa.
- **Modularidad y Simplicidad**: Mantener el programa lo más simple posible, sin perder de vista la funcionalidad, fue crucial. Encontrar el equilibrio adecuado entre simplicidad y funcionalidad también representó un reto.
- Límite de tiempo: 1 Hora de tiempo de producción para crear la actividad.

### Mejoras Implementadas
- **Opciones Simplificadas para el Usuario**: Al permitir que el usuario vea el historial mediante comandos claros (`si`, `historial` o `ver historial`), el programa se vuelve más accesible y fácil de usar.
- **Estructura del Historial**: Se mejoró la forma de almacenar los datos en una lista anidada, lo que facilita la recuperación y visualización de cálculos previos.
- **Control de Finalización**: Agregamos una opción clara para que el usuario pueda decidir entre continuar o finalizar el programa. Esto proporciona flexibilidad y control en la experiencia del usuario.

## Caso de Historia: COMO, QUIERO, PARA QUE

**COMO** usuario,  
**QUIERO** un programa sencillo para calcular el precio de un producto con IVA,  
**PARA QUE** pueda calcular precios rápidamente y consultar un historial de mis cálculos anteriores.

## Código Utilizado

```python
# Lista para almacenar el historial de cálculos
historial = []

# Programa principal
while True:
    # Solicitar el nombre del cliente
    nombre_cliente = input("Introduce tu nombre: ")
    
    # Solicitar monto al usuario y calcular con IVA fijo de 21%
    monto = float(input("Introduce el precio sin IVA (€): "))
    tasa_iva = 21.0
    iva = monto * (tasa_iva / 100)
    total_con_iva = monto + iva
    
    # Guardar el cálculo en el historial
    historial.append([nombre_cliente, monto, tasa_iva, iva, total_con_iva])
    
    # Mostrar resultados
    print("\nResultados:")
    print(f"Precio sin IVA: {monto:.2f} €")
    print(f"Porcentaje de IVA: {tasa_iva}%")
    print(f"IVA: {iva:.2f} €")
    print(f"Precio con IVA: {total_con_iva:.2f} €\n")
    
    # Preguntar si el usuario quiere ver el historial
    opcion = input("¿Quieres ver el historial? (escribe 'si', 'historial' o 'ver historial' para verlo): ")
    if opcion == "si" or opcion == "historial" or opcion == "ver historial":
        print("\nHistorial de cálculos:")
        if historial:
            for registro in historial:
                print(f"{registro[0]} calculó {registro[1]:.2f} € con IVA del {registro[2]}%: Total con IVA: {registro[4]:.2f} €")
        else:
            print("No hay cálculos en el historial.\n")
    
    # Preguntar si desea cambiar de usuario o finalizar el programa
    continuar = input("¿Quieres cambiar de usuario o finalizar? (escribe 's' para cambiar de usuario o 'finalizar' para terminar): ")
    if continuar == "finalizar":
        print("Programa finalizado.")
        break
