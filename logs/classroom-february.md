# Bitácora de clase

Historial de temas visto en clase

## 2018-02-18 Sabado

### Swift basico
- Introduccion basica de swift sintaxis, gramatica:
  - Tipos de tipado
  - Toma de deciciones
    ```swift
      if cond {
        // do something
      } else {
        // do something else
      }
    ```
  - Condiciones *(==, >, <, =>, <=, !=)*
  ```swift
    var condicion: Bool = true
    if condicion {
      // do something
    } else {
     // do something else
   }
   ```
  - Rangos *(0...10, 0..<10, 0..10.reversed())*
  ```swift
    var rangos = 0...10
    var rangos2 = 0..<10
    var rangos3 = (0...10).reversed()              
    var renagos4 = stride(from: 10, to: 100, by: 4)
  ```
  - Ciclos *(While, Repeat, For)*.
  ```swift
    var valor = 0

    while valor < 10{
      print(valor)
      valor += 1
    }

    repeat{
      print(valor)
      valor += 1
    }while valor < 20

    for _ in 0...10{                
      valor += 1
    }
  ```
- Funciones
  ```swift
    func multiplica(_ x: Int, por y: Int)-> Int{           
      return x * y
    }
    multiplica(5, por: 10)
  ```
- Overloading
  ```swift
  func getValue(_ x: Int) -> Int{
    return x
  }

  func getValue(_ x: String) -> String{
    return x
  }
  ```
- Ejercicio
  - Factorial
  ```swift
    func fact(x) -> Int {
      if x < 2 {
        return 1
      } else {
        return x * fact(x-1)
      }
    }
  ```
- Se comentaron detalladamente cada uno de los siguientes aspectos:
  - Editing a Storyboard
  - Xcode Utilities
  - Centring labels
  - Model-View-Controller (MVC)

Tarea:

- Realizar Capitulo 1: A Simple iOS Applicatio1n

 Libro: iOS Programming THE BIG NERD RANCH GUIDE -
*CHRISTIAN KEUR & AARON HILLEGASS*



## 2018-02-17 Viernes

### Swift basico
- Se comento como funciona swift (frontend, optimizador, backend).
- Introduccion Xcode
  - Se comentaron los procesos que se realizan en Xcode para poder generar un app.
  - Se comento sobre las herramientas y los pasos que se necesitan para poder desarrollar una app.


### Git workflows
- Se comento el flujo de trabajo con ayuda de branch para tener una mejor organizacion.
- Se realizo un ejercicio para modificar las branch de un repositorio de git.
- Se presento un demo de como crear y eliminar una branch.

 Ejercicio:
 - Se realizo un branch dentro de un git personal.
 - Se creo un equipo dentro de un git se delegaron permisos a miembros que se integraron.
---

## 2018-02-10 Sábado

### General
- Se comentó sobre markdown y el cómo facilita hacer documentos de forma rápida y con formato
- Se dio lo básico de git y github para crear repositorio y hacer commits
- Se presento Swift en general
- Swift
  - Variables, constantes
  - Inferencia de tipos
  - Todo en swift son objetos

### Configuraciones
Se configuró git y github: Se instaló homebrew, se instaló git, se configuraron las llaves de github y se hicieron ejercicios de editar y agregar archivos.

Ejercicios:

- Se terminó de hacer los Pitch de tu App. Presentación individual de la idea a desarrollar en una app. Objetivo y descripción
- Individualmente, crear un archivo pages en el iCloud personal, poner la información de objetivo y descripción de la app que se presentó en el Pitch. Incluir las imágenes o fotos al material que hice para mi Pitch. Poner ese archivo como compartido por liga y poner esa liga en el archivo de iCloud compartido: "recursos_comunes_diplo_ios.numbers", la liga esta en la presentación de la clase.

Tareas:

- Ir al documento compartido de iCloud "recursos_comunes_diplo_ios.numbers", entrar al menos a 3 documentos de Pitch de otros compañeros y hacerles comentarios que ayuden a mejorar su aplicación o su presentación. Los comentarios se harán a pie de documento con su nombre y no tendrán una extensión mayor a 2 párrafos. Si el docuemento que voy a editar ya tiene muchos comentarios, buscar uno que no tenga o no repita lo que se quiera comentar.
- En el mismo documento compartido "recursos_comunes_diplo_ios.numbers", en la pestaña de "iCloud y github de todos", completar la infor mación faltante y la liga al repo de github donde se irán haciendo los cambios de entregas y archivos del diplomado (poner la liga no el nombre de usuario).
- Repasar git y github
- Repasar lo visto en swift
- Algortimos: Traer el pseudocódigo del Factorial y serie de Fibonacci

## 2018-02-09 Viernes

### General
- Panorama general de las personas y profesiones involucradas en el desarrollo de apps
- Presentación de instructores
- Presentación del lab y de la filosofía de trabajo
- Presentación forma de trabajo, de evaluar, reglas del laboratorio

### Configuraciones
Se creo cuenta en MacBooks para los que usan equipo del lab y se configuró Internet en los que traen equipo propio.

Ejercicios:

- Pitch de tu App. Presentación individual de la idea a desarrollar en una app. Objetivo y descripción
