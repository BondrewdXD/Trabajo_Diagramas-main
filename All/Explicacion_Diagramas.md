# Explicación Diagramas Proyecto Sistema de Restaurante
---
## Diagramas Comportamentales
---
### Diagramas de Actividad
---
### Diagramas de Comunicación
---
### Diagramas de Secuencia
---
### Diagramas de Estado
---
### Diagramas de Tiempo
---
### Diagramas de Casos de uso
---
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