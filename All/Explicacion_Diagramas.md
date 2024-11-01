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
![clases](Structure_Diagrams/Class_Diagram/IMG/Class_Diagram.png)
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