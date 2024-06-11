## APUNTES DE PYTHON

### Introducción 
Este apunte contiene informacion basica sobre los fundamentos de Python. Al final del documento, se incluyen algunos recursos para profundizar más en cada tema.


1. [Variables](#variables)
2. [Estructuras de Control](#estructuras-de-control)
3. [Listas](#listas)
4. [Tuplas](#tuplas)
5. [Diccionarios](#diccionarios)
6. [Iterables](#iterables)
7. [Funciones](#funciones)
8. [POO](#clases-y-objetos)
9. [Recursos adicionales ](#recursos)

#### VARIABLES

name_var = value
``` python
x = 10
real = 8.5
nombre = "Messias"
esJueves = False
var_sinValor = None
```

#### CONVERSION DE DATOS
``` python
numString = "8.5" (String)
numInt = 4 (Entero) 
# Conversion
conversion1 = float(numString)
conversion2 = str(numInt)  

print(type(nameVar)) #Imprimo el tipo 
```

#### ESTRUCTURAS DE CONTROL

**IF ELSE**
Se utiliza para tomar decisiones. **if** evalua una condición, si es verdadera ejecuta el bloque de codigo correspondiente. Si la condición es falsa, el bloque de código no se ejecuta. <br>
En este ejemplo, en caso de que la primera condicion (a < b) sea falsa, se evalua la segunda condición, si es verdadera se imprime: *a es mayor que b*. En caso de No ser verdadera, se ejecuta la tercera accion  **else**.
``` python
if a < b:
   print('a es menor que b')
elif a > b:
   print('a es mayor que b')
else:
   print('a y b son iguales')
```

**FOR** <BR>
*for (elemento) in (elementos a iterar):* <BR>
Se coloca la sentencia **for** seguida de la variable donde se almacenarán los ítems y luego del operador **in** el elemento a iterar.

``` python
numeros = [1,2,3,4,5]
for num in numeros:
    suma= num+1
    print(suma)

SALIDA: 2,3,4,5,6
```

**WHILE** <br>
Evalua la condicion, si es verdadera se ejecuta el bloque de acciones.<br> El bloque se puede ejecutar 0, 1 o mas veces.
``` python
num=1
while num < 6:
    print("num: ", num)
    num =num +1

SALIDA: num: 1, num: 2, num: 3, num: 4, num: 5, num: 6
```   

*Diferencia entre For y While*<br>
**For** : Se usa cuando sabemos la cantidad de veces a iterar. <br>
**While** : Se Cuando no sabemos cuantas veces debe ejecutarse. Se deja de ejecutar cuando la condicion se cumple.

Sentencia **BREAK** <br>
Permite alterar el comportamiento del bucle FOR y WHILE.
Cuando se encuentra "break" el bucle se termina.
```python
cadena = 'Python'

for letra in cadena:
    if letra == 'h':
        print("Se encontró la h")
        break
    print(letra)
``` 

### LISTAS []
Nos permiten almacenar una colección de elementos en una sola variable. Son dinamicas.
Pueden tener elementos duplicados y de distintos tipos.
```python
mi_lista = ["rojo", "azul", "amarillo","verde"]
rebanada = mi_lista[1:3]
print(rebanada)  # salida: ["azul", "amarillo"]
```
#### Metodos de Lista

- **APPEND()**: Agrega un elemento al final de la lista.
`mi_lista.append("blanco")`
- **INSERT()**: Inserta un elemento en una posición específica.
`mi_lista.insert(2, "negro")`

- **EXTEND()**: Agrega los elementos de otra lista al final de la lista actual.
`mi_lista.extend(["rosa", "gris"])`

- **INDEX()**: Devuelve el índice de la primera aparición de un elemento en la lista. `mi_lista.index("azul")` <br>

- **REMOVE()**: Elimina la primera aparición de un elemento de la lista.
`mi_lista.remove("blanco")`

- **SORT()**: Ordena los elementos de la lista en orden ascendente (por defecto) o descendente.
- **POP()**:  Es utilizado para eliminar y devolver el último elemento de una lista.
`ultimo= mi_lista.pop() || mi_lista.pop(1)`

### TUPLAS()
Es una lista de valores, que no se puede modificar.
```python
tupla_dias=("martes","jueves","viernes","sabado")
```
- **in**: se utiliza para verificar si un elemento está presente en la tupla.
 ` "jueves" in tupla_dias  #Salida: True ` <br>

 - **count**: Cuenta las veces q aparece un elemento especifico.
 ` tupla_dias.count("sabado")  #Salida: 1 `

**Empaquetado de tuplas**<br>
Es cuando se crea una tupla asignando a 1 variable un conjunto de variables separadas x coma.<br>
`x=11  | y=22 | z="hola"    creacion: tupla=x,y,z`

- **List**
Convierte una tupla en una lista: `newLista= list(miTupla)`. Lo mismo para las listas con: tuple

### DICCIONARIOS {}

Secuencia de valores con indices de cualquier tipo. Cada *clave* apunta a un *valor*.
Son mutables (se pueden Agregar, Eliminar, Modificar). Se puede acceder a los valores solo atraves de las *Claves*
```python
          key    value
dicc={  "tercero": 3, "ciudad": "Baradero"}

#En este ejemplo, podemos notar que el diccionario incluye 1 lista y 1 tupla como valores
mi_dicc ={ 'Colores Primarios': ['Rojo','Azul','Amarillo'], 
           'Colores secundarios': ('Naranja','Violeta'), 
           'Clave3': 10,
           'Clave4': False}
print(mi_dicc)
```

### Metodos
-  **DEL** elimina un elemento especificando su clave. `del mi_dicc["Clave 4"]` 
- **KEYS** devuelve una lista con todas las claves que hay en un diccionario `mi_diccionario.keys()`
- **VALUES** devuelve una lista con los valores del diccionario `mi_diccionario.values()`
- **LEN** devuelve la cantidad de elementos de en un diccionario. `len(mi_diccionario)`

Podemos utilizar una TUPLA como Clave de un DICCIONARIO.
```python
#Esta asignando en el diccionario como clave a cada valor de la tupla, ej: "Argentina": "Buenos Aires"
mi_tupla = ("Argentina", "Italia", "Inglaterra")
mi_diccionario = {mi_tupla[0]: "Buenos Aires",
                  mi_tupla[1]: "Roma",
                  mi_tupla[2]: "Londres"}
```

#### ITERABLES

 Un **ITERABLE** *es una clase que puede ser iterada*, lo que significa que se puede recorrer elemento por elemento.<br>
Estas son: STRING, LISTA, DICCIONARIO, TUPLA, PILA, ARBOL, entre otras

- **ENUMERATE()**: Agrega un indice a cada elemento de una secuencia.
```python
  cadena =" Hola"
   for c in enumerate(cadena):
     print(c)
#Salida: (0,'H')  (1,'o')  (2,'l') ....etc
```
- **ISINTANCE()**: Para saber si un objeto Es o no Iterable 
```python
cadena = "Hola"
isinstance(cadena,Iterable) #Salida: true
```

*Otros Metodos para clases iterales*
- LIST(): Convierte a lista una clase iterable
`print(list("Hola"))  #Salida: ['H','o','l','a']`
- SUM(): Suma todos los elementos de una lista o iterable
`print(sum([1,2,3]))  #Salida: 6`
- JOIN(): Para concatenar elementos de clase iterable en 1 cadena
 `print("-".join("Hola))  #Salida: H-o-l-a`


 **ZIP()** <br>
Es una funcion que toma 2 o mas secuencias y las combina en una secuencia de tuplas de elementos.
Es util para combinar datos de multiples fuentes, tambien columnas de una tabla o datos de diferentes archivos.<br>
La sintaxis es:
zip(iterable1, iterable2, iterable3,...)
```python
lista_1 = [1, 2, 3]
lista_2 = ['a', 'b', 'c']
combinacion = zip(lista_1, lista_2)

for elemento in combinacion
  print(elemento)

#Salida: (1,'a')  (2,'b')  (3,'c')
```
### FUNCIONES
Conjunto de intrucciones, que pueden reutilizarse cada vez que las necesitemos.

#### Ambito de Variables
**Variables Locales**: Son las declaradas dentro de la funcion solo pueden ser utilizadas aqui dentro.<br>
**Variables Globales**: Son las declaradas fuera de la fucion pueden ser utilizadas en todo el programa.
```python
def nombre_funcion (parametros):  
         instrucciones              
    return valor

#Para invocarla: nombre_funcion(parametros)
```
1) *Una funcion puede no devolver valor*
```python
def imprimir_mensaje():
    print("¡Hola, mundo!") 

#Invoco la funcion
imprimir_mensaje()
```

2) *Una funcion puede devolver 1 valor*
```python
def sumar(num1,num2):
    resultado = num1+num2
    return resultado

#Invoco la funcion
sumar(10,9)  
```
3) *Una funcion puede devolver varios valores*
```python
def dividir(dividendo,divisor):
    cociente = dividendo / divisor
    resto = dividendo % divisor
    return cociente,resto

#Invoco la funcion
dividir(14,3)  
  ```

## CLASES Y OBJETOS

Los **Objetos** se crean a partir de una plantilla llamada "**Clase**". Cada objeto es una instancia de su clase. <br>
Los objetos tienen **Atributos** que son como caracteristicas o propiedades que los definen.<br>
Ejemplo: En una clase "Persona" los atributos podrian ser *Nombre, Edad, Altura*.<br>
Los objetos tienen **Metodos** que son como acciones que los objetos pueden realizar. <br>

Sintaxis en python
  ```python
 class Nombre_clase:
 def __init__ (self,parametros):  #Metodo Constructor
  ```

*Declaracion de atributos*

**Metodo Constructor** <br>Su funcion es inicializar los atributos del objeto creado a partir de la clase que lo posea.
```python
class Gato:

  def __init__(self,nombre,edad,raza): #Constructor
       self.nombre = nombre
       self.edad = edad
       self.raza = raza
    
gato1 = Gato('michi',2,'Siames') #creacion de Objeto

#Metodo para imprimir los Datos
   def presentar(self):
      return print('nombre:',self.nombre,'edad:',self..)

#Invoco el metodo
gato1.presentar() 
```

### Encapsulamiento
Se utiliza cuando es necesario q ciertos metodos o propiedades sean inviolables o inalterables. Se refiere a la ocultacion de los detalles internos de una clase para proteger los datos de accesos no autorizados o modificaciones accidentales.
```python
class CuentaBancaria:
     def __init__(self,saldo):   #Constructor
         self.__saldo = saldo  #Atributo privado con __ para encapsulamiento
   
     def depositar(self,monto):   #Metodo
         if monto > 0:
            self.__saldo += monto
         else:
            print("Error, el monto debe ser un numero positivo")

     def obtener_saldo(self):  # Método 
         return self.__saldo

# Crea una instancia de la clase CuentaBancaria
cuenta = CuentaBancaria(1000)

#Invoco el metodo depositar y le paso el monto 500 como argumento
cuenta.depositar(500)  
print(cuenta.obtener_saldo())  # Salida: 1500
```
`self.__saldo` es un atributo encapsulado, lo que significa que no debe ser accedido directamente desde fuera de la clase.

### Herencia
Permite crear nuevas clases a partir de otras. Permite a la clase hija acceder a todos los metodos y tener las propiedades de la clase padre.
Se utiliza cuando tenemos clases q se parecen entre si pero tienen ciertas particularidades. <br>

Ej: Si tengo la clase Persona y la clase Empleado, un empleado es una persona, entonces puede heredar todo.
```python
class Persona:
   def __init__(self,nombre,edad):
       self.nombre = nombre
       self.edad = edad
   
   def hablar(self):     #Metodo de la clase Persona
       print("Hola, estoy hablando")
```
`SUPER()` Se utiliza para indicar que Atributos va a heredar la clase hija.
```python

class Empleado(Persona):  #Asi va a heredar
   def __init__(self,nombre,edad,trabajo):
      super().__init__(nombre,edad) #Atributos que hereda
      self.trabajo = trabajo

  
roberto = Empleado("roberto",43,"Programador")
roberto.hablar()   #Heredo el metodo de la clase Persona
```
*Los metodos que sean creados en la clase hija no se pueden usar en la clase padre*

### RECURSOS

**Cursos Youtube**
- Python desde 0 ( **Pildorasinformaticas** ) [LINK](https://www.youtube.com/watch?v=G2FCfQj-9ig&list=PLU8oAlHdN5BlvPxziopYZRd55pdqFwkeS)
- Python desde 0 ( **SoyDalto** ) [LINK](https://www.youtube.com/watch?v=nKPbfIU442g&t=71s)

**Apuntes** 
- El libro de Python [LINK](https://ellibrodepython.com/)
- Aprende Python [LINK](https://aprendepython.es/)

- Python de cero a experto ( **jvadillo** ) [LINK](https://github.com/jvadillo/aprende-python-desde-cero-a-experto?tab=readme-ov-file)

- Programacion Orientada a Objetos ( **Apuntes de Nico** ) [LINK](https://apuntesdenico.notion.site/POO-Programaci-n-Orientada-a-Objetos-eba7559e26054df3a1b80cef90101f8e)

**Ejercicios**
- Ejercicios de Programación con Python [LINK](https://aprendeconalf.es/docencia/python/ejercicios/)


