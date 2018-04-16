# Bitácora de clase

Historial de temas visto en clase


## 2018-04-14 Sabado

### Swift

- Se explico detalladamente el programa de la clase pasada

- Se realizo una exposicion donde se nos proporciono unos tips de como convertirse en un buen desarrollador

- Se dieron consejos para la elaboracion de un proyecto
  - Las clases no pueden tener más de cien líneas de código
  - Los métodos no pueden tener más de cinco líneas de código
  - Pasar no más de cuatro parámetros en un método
  - Los controladores pueden instanciar solo un objeto


- Persistencia de datos
  - UserDefaults
  - FileManager
    - Documents
    - Cache
    - Temporal
  - NSCache
  - Keychain
  - CoreData
    - Guide
    - Persistent Store Features


- Se explico el funcionamiento del ejercicio LocalSettings analizandolo detalladamente

## 2018-04-13 Viernes

### Swift

- Se comentaron los siguientes temas:

- Persistence: I want to persist my application data
  - Where
  - What
  - How
  - When


  - Application Sandbox
    - Documents
    - Library
      - Cache
      - Preferences
    - tmp   


  - Locating the Documents Directory


  - Read/Write Binary Data
    - Disk
    - System
    - Default
    - Cache


  - Read/Write Textual Data


  - Read/Write Custom Objects
  ```Swift
  protocol NSCoding {
    //When we want to load an object from disk...
    init?(coder aDecoder: NCoder)

    //When we want to save an object to disk...
    func encode(with aCoder: NSCoder)
  }
  ```

  - Conforming to NSCoding
  ```Swift
  class Item: NSOject, NSCoding{
      required init(coder aDecoder: NSCoder){
        // do something
      }
  }
  ```

  - NSKeyedArchiver and NSKeyedUnarchiver
  ```Swift
  func saveChanges() -> Bool {
      print("Saving items to: \(itemArchiveURL.path)")
      return NSKeyedArchiver.archiveRootObject(allItems, toFile: itemArchiveURL.path)
  }
  ```

  - Archiving an Array of Items


  - When to save


  - Application Lifecycle: Application States and Transitions
    - Not Running
    - Active
    - Inactive
    - Background
    - Suspended


  - Basic Core Data


  - Core Data: Classes


  - Model


  - NSPersistentContainer
  ```Swift
    let persistentContainer: NSPersistentContainer = {
    let container = NSPersistentContainer(name: "Photorama")
    container.loadPersistentStores { (description, error) in
      if let error = error {
        print("Error setting up Core Data (\(error)).")
      }
    }
    return container
    }()
  ```

  - Fetching

  - Predicates

  - NSManagedObject

- Se proporciono un programa para analizar y verlo la siguiente clase

---

## 2018-04-07 Sabado

### Swift

- Concluimos el ejercicio de la clase pasada donde por medio de un servicio realizabamos el llenado de una tabla

- Genericos
  ```swift
  func swapGenerics<generico>(a: inout generico, b: inout generico){
    let temp = a
    a = b
    b = temp
  }

  var a1 = 5
  var b1 = 10
  swapGenerics(a: &a1, b: &b1)
  print("\(a1) - \(b1)")

  ---------------------------------------------

  class generica<T>{
    // do something
  }

  class Generica<T, E>{

  }

  let objetoGenerico = Generica<String, Int>()

  enum enumGenerico<T>{
    // do something
  }
  ```

- Tipos asociados
  ```swift
  struct List<T>{
    var items = [T]()
    mutating func add(item: T){
        items.append(item)
    }

    func getItemAtIndex(index: Int) -> T?{
        if items.count > index{
            return items[index]
        }else{
            return nil
        }
    }

    subscript(index: Int) -> T?{
        return getItemAtIndex(index: index)
    }

    subscript(r: CountableClosedRange<Int>) -> [T]{
        get{
            return Array(items[r.lowerBound ... r.upperBound])
        }
    }
  }

    var MyList = List<Int>()
    MyList.add(item: 3)
    MyList.add(item: 7)
    MyList.add(item: 29)
    MyList.add(item: 13)
    MyList.add(item: 58)

    var valores = MyList[0...3]
    print(valores)
  ```


## 2018-04-06 Viernes

### Swift

- Se realizo un repaso general de los closures para posteriormente consumir un servicio por medio de un json

- Se realizaron dos ejercicios en los que por medio de json se consumian servicios diferentes:

  - Capturar el lugar y el clima a traves de un servicio
  - LLenar una tabla con imagenes, nombre, caracteristica y descripcion de los objetos a traves de un servicio

---

## 2018-03-24 Sabado

### Swift

- Se hizo un repaso de los siguientes temas:


  - Definiciones
    - Log
    - Tarea
    - Thread
    - Proceso
    - Programa
    - Stacktrace
    - Paralelismo
    - Concurrencia
    - Sistema Operativo
    - Programa de ejecucion
    - Vartiables temporales y locales


  - Problematicas
    - Deadlocks
    - Condiciones de carrera


  - Necesidades
    - Diseño Simple
    - Expresividad
    - Eficiencia de Ejecucion
    - Facilidad para Depuracion
    - Escalabilidad y balanceo de cargas
    - Diversidad de HW
    - Uso multiple de Closures


  - Modelos

  - Tecnologias


- Se comento las funciones que realiza el main thread para realizar las conexiones:
  - UIAplication
  - AppDelegate
  - UIWindow
  - RootViewController


- Loop infinito del thread principal resumido:
  - Espera evento
  - Ruteo evento
  - Ejecuto metodo viewController
  - Indico vistas a volver a pintar
  - Repintado
  - Libero memoria
  - Se repite el ciclo


- Se realizo un analisis sobre: Storage Latency How far away is the data?


- Se realizo un repaso sobre:
  - Protocolos
  - Delegate
  - Singleton
  - Tipos asociados a protocolos


- Tarea:
  - Darse de alta en OpenWeatherMap (https://openweathermap.org)
  - Mockups, iconos, repasar capitulo 3, 4, 5 y 6


## 2018-03-23 Viernes

### Swift

- Se vio como implementar programaticamente:

  - Label
  ```swift
  titleLabel: UILabel = {
      let lbl = UILabel()
      lbl.text = "Hello Alerts"
      lbl.font = UIFont.systemFont(ofSize: 22, weight: .bold)
      lbl.tintColor = .white
      lbl.translatesAutoresizingMaskIntoConstraints = false
      return lbl
  }()
  ```
  - Constraints
  ```swift
  NSLayoutConstraint.activate([
      titleLabel.topAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.topAnchor),
      titleLabel.leadingAnchor.constraint(equalTo: self.view.leadingAnchor, constant: 10),
      titleLabel.trailingAnchor.constraint(equalTo: self.view.safeAreaLayoutGuide.trailingAnchor, constant: -10),
      titleLabel.heightAnchor.constraint(equalToConstant: 45)
  ])
  ```

  - Boton:
  ```swift
  let simpleBtn: UIButton = {
      let btn = UIButton(type: .system)
      btn.setTitle("Simple alert", for: .normal)
      btn.titleLabel?.font = UIFont.systemFont(ofSize: 18, weight: .bold)
      btn.tintColor = .white
      btn.translatesAutoresizingMaskIntoConstraints = false        
      btn.addTarget(self, action: #selector(tapOkAlert), for: .touchUpInside)
      return btn
  }()
  ```

  - ImageView:
  ```swift
  let image: UIImageView = {
        let imageU = UIImageView()
        imageU.image = UIImage(named: "M")
        imageU.contentMode = .scaleAspectFit
        imageU.translatesAutoresizingMaskIntoConstraints = false
        return imageU
    }()
  ```

  - TextField:
  ```swift
  let tituloTextField: UITextField = {
        let textFieldTitulo = UITextField()
        let font = UIFont(name: "Arial", size: 20.0)
        textFieldTitulo.font = font
        textFieldTitulo.placeholder = "Titulo"
        textFieldTitulo.text = ""
        textFieldTitulo.borderStyle = UITextBorderStyle.roundedRect
        textFieldTitulo.backgroundColor = UIColor.white
        textFieldTitulo.textColor = UIColor.black
        textFieldTitulo.translatesAutoresizingMaskIntoConstraints = false
        return textFieldTitulo
    }()
    ```

- Se implementaron los diferentes tipos de alertas:
  - Default
  - Destructive
  - Cancel


- Tarea:
  - Realizar los mockups, organizacion de menus, contenidos
---

## 2018-03-17 Sabado

### Swift

- Se realizo un repaso de la clase pasada sobre Table View Controller:
  - Setup
  - Add data source
  - Load data from data source
  - Setup sections and rows
  - Dequeued reusable cell


- Ejercicio
  - Crear un struct user
  - Crear un array de user
  - Populate and reder table view


- Se comentaron los ciclos de retencion

- Inicializadores requeridos
  ```swift
  required init(age: Int){                       
      //do something
  }
  ```
- Inicializadores convenientes
  ```swift
  convenience init(age: Int){
      //do something
  }
  ```
- Se comento la sobre carga de operadores y como implementarlos

- Protocols
  ```swift
  protocol Vehiculo{
      var wheels: Int { get }
      func acelerar()
      func frenar()
  }

  protocol Pintura{
      func colorear()
  }

  class Motito: Vehiculo, Pintura{
      var wheels: Int {
          get{
              return 2
          }
      }

      func colorear() {
          print("Pintar")
      }

      func acelerar() {
          print("Acelera...")
      }

      func frenar() {
          print("...Frena")
      }
  }
  ```

- Extension
```swift
  protocol Reflexion{
      var tipoReflexion: String { get }
  }

  extension String: Reflexion{
      var tipoReflexion: String{
          return "Muy pensativo el dia de hoy"
      }
  }

  let palabrita = "Hola mundo"
  palabrita.tipoReflexion
  ```

- Tarea -> Completar las caracteristicas de la app:
  - Nombre de la App
  - Categoria
  - Nombre de la empresa
  - Edad
  - Descripcion
  - Informacion
  - Navegacion

---

## 2018-03-16 Viernes

### Swift

- Se dejo una actividad para realizar nuestra aplicacion:
  - Nombre de la App
  - Categoria
  - Nombre de la empresa
  - Edad
  - Descripcion
  - Informacion
  - Navegacion


- Se realizo un proyecto para comprender el funcionamiento de forma programatica de los componentes:
  - Tab Bar Controller
  - Table View


- Actividad:
  - Insertar en cada una de las filas de nuestra tabla una imagen programaticamente dependiendo el genero


---

## 2018-03-10 Sabado

### Swift

- Enum
  ```swift
    enum Dia{
        case Lunes
        case Martes
        case Miercoles
        case Jueves
        case Viernes
    }

    var diaSemana: Dia
    diaSemana = .Lunes

    switch diaSemana{
    case .Lunes:
        print("Otra vez a trabajar")
    case .Martes:
        print("Ya quiero que acabe la semana")
    case .Miercoles:
        print("Apenas vamos a la mitad")
    case .Jueves:
        print("Ya casi es fin de semana")
    case .Viernes:
        print("Por fin es viernes")
    }
  ```
- Struct
  ```swift
    struct Cuerpo {
      var altura: Double = 0         
      var peso: Double = 0
    }

    var cuerpo = Cuerpo()
    cuerpo.altura = 1.85
    cuerpo.peso = 80.0
  ```

- Class
  ```swift
  class Alumno{
    var numCuenta: String

    init(numCuenta: String){
        self.numCuenta = numCuenta
      }
    }

  var marduk = Profesor(numEmpleo: "0000000000")

  class Cartera{
      var dinero: Double
      var abonado: Double{
          get{
              print("Intereses actuales: \(dinero * 0.16) pesos")
              return dinero * 0.16
          }
          set{
              print("Se ha abonado: \(newValue) ")
              dinero = (dinero * 0.16) + newValue
              print("Usted tiene: \(dinero)")
          }
      }

      init(dinero: Double, abonado: Double){
          print("Creando cartera con \(dinero) pesos")
          self.dinero = dinero
      }

      deinit {
          print("Destruye una cartera con \(dinero)")
      }
  }

  let carterita1 = Cartera(dinero: 23, abonado: 15)
  carterita1.dinero = 25
  print(carterita1.abonado)
  carterita1.abonado = 100
  ```

- Tarea:
  - Realizar Capitulo 4: Text Input and Delegation

    Libro: iOS Programming THE BIG NERD RANCH GUIDE - CHRISTIAN KEUR & AARON HILLEGASS

  - Elaborar icono y Navegacion de la app

---

## 2018-03-09 Viernes

### Swift

- Se realizo un repaso en xcode:
  - Button
  - Slider
  - TextView
  - Segues
  - NavigationController
  - BarButtonItem


- Se vieron los temas siguientes:
- Optionals and Optional Binding
  - Text Input and Delegation:     
  - Keyboard properties
  - How do I use it?
  - How do I get info back?
  - Protocolos
  - Conforming to a Protocol


- Se realizo de actividad:
  - First Responded con un boton quitar el teclado que levanta el SO del textField
  - First Responded al poner enter en el textField quitar el teclado

---

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

---

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

---

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

---

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

---

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
