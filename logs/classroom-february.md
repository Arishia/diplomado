# Bitácora de clase

Historial de temas visto en clase

## 2018-03-03 Sábado

### Swift

- Se comentaron las funciones del AppDelegate y se mostro de forma practica que realizaba cada una
  - applicationWillResignActive
  - applicationDidEnterBackground
  - applicationWillEnterForeground
  - applicationDidBecomeActive


- Se comento de las operaciones que realiza el Sistema Operativo para el manejo de notificaciones
  - Memoria Virtual
  - Swap
  - Log


- Se realizo un proyecto en xcode donde se importo una imagen se puso un imageView y se colocaron los constrains

- Se vieron herramientas para el desarrollo estetico de los proyectos

- Tarea:
  - Realizar Capitulo 3: Views and the View Hierarchy

    Libro: iOS Programming THE BIG NERD RANCH GUIDE - CHRISTIAN KEUR & AARON HILLEGASS

## 2018-03-02 Viernes

### Swift

- Se comentaron los errores del ejercicio What Happened To Me

- Se elaboraron los ejercicios siguentes:

  - Una funcion como parametro de entrada es tenia que entrar un numero random y dependiendo de este era la salida de nuestra funcion

  - Se pidio codificar la logica de un arma de 200 disparos y una ves realizados estos se sobre calentaba el arma y se perdia un escudo al tener cero escudos nos mandaba Game Over

  - Se elaboro un proyecto en xcode donde vimos el launch screen and assents

- Introduccion a Closures
      var miClosure: (Int, Int) -> Int

      miClosure = {(a: Int, b: Int) -> Int in         
        return a + b
      }


      let resultado = miClosure(3, 2)

      func ejecutaOperacion(_ closure: (Int, Int) -> Int, a: Int, b: Int){
        let resultado = closure(a, b)
        print(resultado)
      }

      ejecutaOperacion(miClosure, a: 10, b: 20)

      miClosure = {(a, b) in
        a + b
      }

      miClosure = {
        $0 + $1                                  
      }


## 2018-02-24 Sábado

### Swift
- Se comento sobre la estructura del proyecto que realizamos de tarea: A Simple iOS Applicatio1n

- Se comento el proceso funcional de los siguientes puntos:
  - viewController (metodo Target - action)
  - UIWindow
    - subviews
  - UIResponde
  - UIView


- Se comentaron los temas siguientes:
  - Goal
    - View objects
    - How do wiews get on screen ?
    - Frame vs Bounds
    - What else does a view do ?
      - subviews
      - superview
      - addsubview
      - insertSubview
    - Auto Layout
    - Stack View
    - After Stack View


- Solucion de los ejercicios de la clase anterior:
  - Numero Primo
    ```swift
    func isPrime(n: Int) -> Bool{
      for i in 2..<n{
        if n % i == 0{
            return false
        }
      }
      return true
    }
    ```
  - Serie de Fibonacci
    ```swift
    func fibo(n: Int){
      var a = 0, b = 1
      while b < n{
        print(b)
        (a, b) = (b, a + b)
      }
    }
    fibo(n: 88)
    ```
  - Palindromo
    ```swift
    func palindromo(str: String) -> Bool{
      return str == String(str.reversed())
    }
    palindromo(str: "Cadena a evaluar")
    ```

  - Funcion que compare dos cadenas y verifique que contenga los mismos caracteres en el mismo o diferente orden
    ```swift
    func comparaCadenas(str:String, str2:String) -> Bool{
      return str.count == str2.count && str.sorted() == str2.sorted()
    }
    comparaCadenas(str: "hola", str2: "aloh")
    print(comparaCadenas(str: "hola", str2: "aloh"))
    ```
- Se comento sobre la referencia debil y referencia fuerte

- Se comentaron los diferentes tipos de opcionales
  - Optional Binding
    ```Swift
      var variable: String?
      if let saludo = variable{
        print("Saludo \(saludo)")
      }else{
        print("No hay nada")
      }
    ```
  - Guard
    ```Swift
      func saludos(cadena: String?){
        guard let saludo = cadena else{
          print("Algo paso")
          return
        }
        print("No paso nada")
      }
    saludos(cadena: (variable))
    ```
  - Nil Coalescing
    ```Swift
      //var edad: Int = 22                            
      var edad: Int? = nil                            
      var edadValida = edad ?? 18                     
      print(edadValida)
    ```
- Se comentaron los tres diferentes tipos de Collections
    - Array
    ```Swift
      var arreglo = [1, 2, 3, 4, 5, 6]
      let alumnos: [String] = []               
      let muchosCeros = Array(repeating: 0, count: 100)    
      print(arreglo[1])                                             

      //Propiedades de los arrays
      alumnos.isEmpty                                               
      arreglo.count                                                 
      arreglo.first                                                 
      arreglo.last                                                  

      //Tratarlo en caso de ser Optional
      print(arreglo.last! as Any)                                  

      var arreglo2 = [2,3,4,5,6]
      arreglo += arreglo2
      print(arreglo.sorted())                                      
      arreglo[1...4]
      arreglo.contains(20)                                        
      for i in arreglo.sorted(){
        print(i)
      }
    ```
    - Diccionarios
    ```Swift
      var diccionario = ["Pedro":18, "Ana": 22, "Juan": 30]
      print(diccionario)                                          

      print(diccionario["Pedro"]! as Any)

      var alumnos: [String:Int] = [:]                             
      alumnos.isEmpty
      alumnos.count

      var perfil = [
        "nombre" : "Parra",
        "carrera" : "Admin"
        ]

        //Agregar elementos
        perfil.updateValue("CDMX", forKey: "Estado")                
        perfil["Edad"] = "18"

        //Remover llave
        perfil.removeValue(forKey: "Edad")
        perfil["Estado"] = nil

        //Iterar los diccionarios
        for (llave, valor) in perfil{
          print("\(llave) - \(valor)")
        }

        for (llave) in perfil.keys{
          print("\(llave), " , terminator: "")
        }
    ```
    - Conjuntos
    ```Swift
      var conjunto: Set<Int> = [1,2,3,2,1]
      print(conjunto)
    ```

- Tareas Pendientes
  - Documento de Pitch integrar comentarios realizados y subir en pdf
  - Ejercicio 1 - Capitulo 1: A Simple iOS Applicatio1n
  - Ejercicio de Debug
  - Algoritmos Swift


- Proximas Tareas:
  - Ejercicio 3 - Capitulo 3: Views and the View Hierarchy

    Libro: iOS Programming THE BIG NERD RANCH GUIDE - CHRISTIAN KEUR & AARON HILLEGASS
  - Pitch integrando comentarios

---

## 2018-02-23 Viernes

### Swift

- Ejercicios:

  - Numero Primo
  - Serie de Fibonacci
  - Palindromo
  - Funcion que compare dos cadenas y verifique que contenga los mismos caracteres en el mismo o diferente orden


- Se menciono si swift es funcional

- Se hizo un repaso de la clase anterior de el ciclo de vida de una aplicacion:
  - Espera evento
  - Detecta interrupcion
  - Recibe el sistema operativo
  - windows server
  - Ingresa a la cola del programa
  - Application muestra los eventos
  - Se manda a la vista el evento

  - NSApplication -> AppDelegate -> UIWindow -> viewController
---

## 2018-02-18 Sábado

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
