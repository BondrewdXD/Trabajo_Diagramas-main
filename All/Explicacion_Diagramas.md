# Explicación Diagramas Proyecto Sistema de Restaurante
---
## Diagramas Comportamentales
---
### Diagramas de Actividad
---
```js
@startuml Actividad
|Cliente|
start
:Decide qué mesa ocupar;
:Selecciona tipo de servicio;
if (Comer en el restaurante?) then (sí)
  :Escoge comida;
  if (¿Desea sopa?) then (sí)
    :Selecciona sopa;
  else (no)
    :No selecciona sopa;
  endif
  if (¿Desea postre?) then (sí)
    :Selecciona postre;
  else (no)
    :No selecciona postre;
  endif
else (no)
  :Selecciona comida para llevar;
endif

:Ordena;
:Se le sirve la orden;
:Genera factura;
:Factura detallada para el dueño;

stop
@enduml
```

![actividad](/All/Images_Diagrams/Actividad.png)




### Diagramas de Comunicación
---
```js
@startuml Comportamental
skinparam actorPadding 10
skinparam rectanglePadding 10

actor Cliente
actor Camarero
actor "Dueño del Restaurante" as Dueño

rectangle "Sistema de Pedido" {
    Cliente -> Sistema : SeleccionaMesa()
    Cliente -> Sistema : EligeServicio(tipo)
    Cliente -> Sistema : SeleccionaComida(opciones)
    Cliente -> Sistema : RealizaPedido()

    Sistema -> Camarero : TomaPedido()
    Camarero -> Cliente : SirveOrden()
    Sistema -> Cliente : RecibeOrden()
    Sistema -> Cliente : GeneraFactura()
    Sistema -> Dueño : EnviaFacturaDetallada()
}
@enduml
```

![comportamental](/All/Images_Diagrams/Comportamental.png)



### Diagramas de Secuencia
---
```js
@startuml Secuencia
actor Cliente
participant "Sistema de Restaurante" as Sistema
participant "Dueño del Restaurante" as Dueno

Cliente -> Sistema : Mostrar mesas disponibles

Cliente -> Sistema : Seleccionar mesa (ej. Mesa 1)

Cliente -> Sistema : Elegir tipo de servicio (1: Restaurante, 2: Para llevar)
Sistema --> Cliente : Confirmar tipo de servicio

alt Servicio en Restaurante
    Sistema -> Cliente : Mostrar menú del día
    Cliente -> Sistema : Seleccionar sopa (Sí/No)
    alt Sopa
        Sistema -> Cliente : Mostrar opciones de sopa
        Cliente -> Sistema : Seleccionar sopa
    end

    Cliente -> Sistema : Seleccionar plato principal
    Cliente -> Sistema : Seleccionar postre (Sí/No)
    alt Postre
        Sistema -> Cliente : Mostrar opciones de postre
        Cliente -> Sistema : Seleccionar postre
    end

    Cliente -> Sistema : Confirmar pedido
    Sistema --> Cliente : Servir pedido
    Sistema -> Dueno : Generar factura
    Dueno --> Sistema : Generar factura detallada

else Servicio para llevar
    Sistema -> Cliente : Mostrar menú del día
    Cliente -> Sistema : Seleccionar sopa (Sí/No)
    alt Sopa
        Sistema -> Cliente : Mostrar opciones de sopa
        Cliente -> Sistema : Seleccionar sopa
    end

    Cliente -> Sistema : Seleccionar plato principal
    Cliente -> Sistema : Seleccionar postre (Sí/No)
    alt Postre
        Sistema -> Cliente : Mostrar opciones de postre
        Cliente -> Sistema : Seleccionar postre
    end

    Cliente -> Sistema : Preguntar por desechables (Sí/No)
    alt Desechables
        Sistema -> Cliente : Costo adicional por desechables
    else
        Sistema -> Cliente : Sin costo adicional
    end

    Cliente -> Sistema : Confirmar pedido
    Sistema --> Cliente : Preparar pedido para llevar
    Sistema -> Dueno : Generar factura
    Dueno --> Sistema : Generar factura detallada
end
@enduml
```

![secuencia](/All/Images_Diagrams/Secuencia.png)


### Diagramas de Estado
---
```js
@startuml estado-transicion
[*] --> SeleccionMesa

SeleccionMesa --> EligeServicio : Mesa seleccionada
EligeServicio --> EscogeComida : Servicio elegido

EligeServicio --> EscogeComidaParaLlevar : Llevar
EligeServicio --> EscogeComidaRestaurante : Comer en restaurante

EscogeComidaRestaurante --> EscogeSopa : Comida seleccionada
EscogeSopa --> EscogePostre : Sopa seleccionada
EscogeSopa --> RealizaPedido : No sopa

EscogePostre --> RealizaPedido : Postre seleccionado
EscogePostre --> RealizaPedido : No postre

EscogeComidaParaLlevar --> RealizaPedido : Comida seleccionada para llevar

RealizaPedido --> SirveOrden : Pedido realizado
SirveOrden --> GeneraFactura : Orden servida
GeneraFactura --> [*] : Factura generada
@enduml
```

![estado](/All/Images_Diagrams/estado-transicion.png)


### Diagramas de Tiempo
---
```js
@startuml Tiempo
title Diagrama de Tiempo del Sistema de Restaurante

participant Cliente
participant Sistema
participant Camarero
participant Dueño

Cliente -> Sistema : SeleccionaMesa() 
note right of Cliente : t1: Selecciona mesa
Cliente -> Sistema : EligeServicio(tipo) 
note right of Cliente : t2: Elige servicio

alt Comer en el restaurante
    Cliente -> Sistema : EscogeComida() 
    note right of Cliente : t3: Escoge comida
    alt ¿Desea sopa?
        Cliente -> Sistema : SeleccionaSopa() 
        note right of Cliente : t4: Selecciona sopa
    else
        Cliente -> Sistema : NoSeleccionaSopa()
        note right of Cliente : t4: No selecciona sopa
    end
    alt ¿Desea postre?
        Cliente -> Sistema : SeleccionaPostre() 
        note right of Cliente : t5: Selecciona postre
    else
        Cliente -> Sistema : NoSeleccionaPostre()
        note right of Cliente : t5: No selecciona postre
    end
else Para llevar
    Cliente -> Sistema : EscogeComidaParaLlevar() 
    note right of Cliente : t6: Escoge comida para llevar
end

Cliente -> Sistema : RealizaPedido() 
note right of Cliente : t7: Realiza pedido
Sistema -> Camarero : TomaPedido() 
note right of Sistema : t8: Toma pedido
Camarero -> Cliente : SirveOrden() 
note right of Camarero : t9: Sirve orden
Sistema -> Cliente : GeneraFactura() 
note right of Sistema : t10: Genera factura
Sistema -> Dueño : EnviaFacturaDetallada() 
note right of Sistema : t11: Envia factura detallada
@enduml
```

![tiempo](/All/Images_Diagrams/Tiempo.png)


### Diagramas de Casos de uso
---
```js
@startuml Casos_De_Uso
left to right direction
actor Cliente
actor Camarero
actor "Dueño del Restaurante" as Dueño
package "Restaurante" {
    usecase "Seleccionar Mesa" as UC1
    usecase "Elegir Servicio" as UC2
    usecase "Escoger Comida" as UC3
    usecase "Seleccionar Sopa" as UC4
    usecase "Seleccionar Postre" as UC5
    usecase "Realizar Pedido" as UC6
    usecase "Servir Orden" as UC7
    usecase "Generar Factura" as UC8
    usecase "Enviar Factura Detallada" as UC9

    Cliente --> UC1
    Cliente --> UC2
    Cliente --> UC3
    UC3 --> UC4 : <<include>>
    UC3 --> UC5 : <<include>>
    Cliente --> UC6
    Camarero --> UC7
    UC6 --> UC8
    Dueño --> UC9
}
@enduml
```

![casouso](/All/Images_Diagrams/Casos_De_Uso.png)

## Diagramas Estructurales
---
### Diagramas de Clases
---
```js
@startuml Clases

class Plato {
    - ID_Plato: int
    - Nombre: string
    - Descripción: string
    - Precio: decimal
    - Foto: string
}

class Detalle_Orden {
    - ID_Detalle: int
    - ID_Orden: int
    - ID_Plato: int
    - Cantidad: int
    - Sopa: boolean
    - Postre: boolean
    - Domicilio: boolean
    - Recipiente: boolean
}

class Orden {
    - ID_Orden: int
    - ID_Mesa: int
    - HoraPedido: datetime
    - Total: decimal
}

class Mesa {
    - ID_Mesa: int
    - Numero_Mesa: int
    - Capacidad: int
    - Estado: string
}

class Usuario {
    - ID_Usuario: int
    - Nombre: string
    - Teléfono: string
    - Dirección: string
}

class Factura {
    - ID_Factura: int
    - ID_Orden: int
    - Fecha: date
    - Total: decimal
    - MetodoPago: string
}


Plato o--  Detalle_Orden : contiene > 
Orden  --*  Detalle_Orden : compone >
Orden  o--  Mesa : se realiza en >
Usuario  o--  Orden : realiza >
Factura  -- Orden : se genera para >

@enduml
```

![clases](/All/Images_Diagrams/Class_Diagram.png)

Este diagrama de clases representa la estructura de un sistema de gestión de restaurante, mostrando las principales entidades y sus relaciones. A continuación, se describen cada una de las clases y sus atributos, así como las relaciones entre ellas.

### Clases y Atributos

#### 1. Plato
- *ID_Plato*: int
- *Nombre*: string
- *Descripción*: string
- *Precio*: decimal
- *Foto*: string

Esta clase representa los diferentes platos disponibles en el restaurante. Cada plato tiene un identificador único, nombre, descripción, precio y una foto.

---

#### 2. Detalle_Orden
- *ID_Detalle*: int
- *ID_Orden*: int
- *ID_Plato*: int
- *Cantidad*: int
- *Sopa*: boolean
- *Postre*: boolean
- *Domicilio*: boolean
- *Recipiente*: boolean

Esta clase detalla cada elemento de una orden, indicando qué platos se han pedido, su cantidad, y opciones adicionales como si se incluye sopa, postre, si es para domicilio y si se requiere recipiente.

---

#### 3. Orden
- *ID_Orden*: int
- *ID_Mesa*: int
- *HoraPedido*: datetime
- *Total*: decimal

Representa una orden realizada en el restaurante. Incluye un identificador único, el número de mesa donde se realiza la orden, la hora en que fue pedido y el total de la orden.

---

#### 4. Mesa
- *ID_Mesa*: int
- *Numero_Mesa*: int
- *Capacidad*: int
- *Estado*: string

Esta clase describe las mesas del restaurante. Cada mesa tiene un identificador, un número, capacidad de personas y su estado (disponible, ocupada, reservada).

---

#### 5. Usuario
- *ID_Usuario*: int
- *Nombre*: string
- *Teléfono*: string
- *Dirección*: string

Representa a los usuarios que realizan las órdenes. Incluye un identificador, nombre, teléf


Este diagrama de clases representa la estructura de un sistema de gestión de restaurante, mostrando las principales entidades y sus relaciones. A continuación, se describen cada una de las clases y sus atributos, así como las relaciones entre ellas.

### Clases y Atributos

#### 1. Plato
- *ID_Plato*: int
- *Nombre*: string
- *Descripción*: string
- *Precio*: decimal
- *Foto*: string

Esta clase representa los diferentes platos disponibles en el restaurante. Cada plato tiene un identificador único, nombre, descripción, precio y una foto.

---

#### 2. Detalle_Orden
- *ID_Detalle*: int
- *ID_Orden*: int
- *ID_Plato*: int
- *Cantidad*: int
- *Sopa*: boolean
- *Postre*: boolean
- *Domicilio*: boolean
- *Recipiente*: boolean

Esta clase detalla cada elemento de una orden, indicando qué platos se han pedido, su cantidad, y opciones adicionales como si se incluye sopa, postre, si es para domicilio y si se requiere recipiente.

---

#### 3. Orden
- *ID_Orden*: int
- *ID_Mesa*: int
- *HoraPedido*: datetime
- *Total*: decimal

Representa una orden realizada en el restaurante. Incluye un identificador único, el número de mesa donde se realiza la orden, la hora en que fue pedido y el total de la orden.

---

#### 4. Mesa
- *ID_Mesa*: int
- *Numero_Mesa*: int
- *Capacidad*: int
- *Estado*: string

Esta clase describe las mesas del restaurante. Cada mesa tiene un identificador, un número, capacidad de personas y su estado (disponible, ocupada, reservada).

---

#### 5. Usuario
- *ID_Usuario*: int
- *Nombre*: string
- *Teléfono*: string
- *Dirección*: string

Representa a los usuarios que realizan las órdenes. Incluye un identificador, nombre, teléfono y dirección de contacto.

---

#### 6. Factura
- *ID_Factura*: int
- *ID_Orden*: int
- *Fecha*: date
- *Total*: decimal
- *MetodoPago*: string

Esta clase representa la factura generada para una orden específica. Incluye un identificador, la fecha de emisión, el total de la factura y el método de pago utilizado.

### Relaciones

- *Plato o-- Detalle_Orden*: Un plato puede estar contenido en múltiples detalles de orden.
- *Orden -- Detalle_Orden**: Una orden se compone de múltiples detalles de orden.
- *Orden o-- Mesa*: Una orden se realiza en una mesa específica.
- *Usuario o-- Orden*: Un usuario realiza una orden.
- *Factura -- Orden*: Se genera una factura para una orden específica.

Este diagrama es esencial para entender cómo interactúan las diferentes entidades dentro del sistema de gestión de un restaurante, permitiendo una mejor organización y seguimiento de las órdenes y los usuarios.


### Diagramas de Componentes
---
### Diagramas de Despliegue
---
### Diagramas de Objetos
---
### Diagramas de Paquetes
---
### Diagramas de Perfil
---