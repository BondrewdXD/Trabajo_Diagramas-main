# Trabajo Diagramas
## Este repositorio pertenece al trabajo realizado por Jose Miguel Vera Garzón & Maria Juliana Ferro Bonilla
---
# Sistema de Gestión de Restaurante

Este documento detalla el diseño de un sistema de gestión para un restaurante, representado mediante un conjunto de diagramas. A continuación, se describen las entidades principales del sistema y sus atributos.

## Entidades y Atributos

### 1. Plato
Representa los diferentes platillos que ofrece el restaurante.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Plato       | int     | Identificador único del plato.               |
| Nombre         | string  | Nombre del plato.                            |
| Descripción    | string  | Descripción del plato.                       |
| Precio         | decimal | Precio del plato.                            |
| Foto           | string  | URL de la imagen del plato.                 |

### 2. Orden
Representa el pedido realizado por un cliente en una mesa.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Orden       | int     | Identificador único de la orden.            |
| ID_Mesa        | int     | Identificador de la mesa asociada a la orden.|
| HoraPedido     | datetime| Hora en que se realizó el pedido.           |
| Total          | decimal | Total a pagar por la orden.                 |

### 3. Detalle_Orden
Representa los detalles de cada orden, incluyendo los platos seleccionados y opciones adicionales.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Detalle     | int     | Identificador único del detalle de la orden.|
| ID_Orden       | int     | Identificador de la orden asociada.         |
| ID_Plato       | int     | Identificador del plato pedido.              |
| Cantidad       | int     | Cantidad del plato solicitado.               |
| Sopa           | boolean | Indica si se incluye sopa en el pedido.     |
| Postre         | boolean | Indica si se incluye postre en el pedido.   |
| Domicilio      | boolean | Indica si el pedido es para entrega a domicilio.|
| Recipiente     | boolean | Indica si se solicita recipiente para el pedido. |

### 4. Mesa
Representa las mesas disponibles en el restaurante.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Mesa        | int     | Identificador único de la mesa.             |
| Numero_Mesa    | int     | Número de identificación de la mesa.        |
| Capacidad      | int     | Número máximo de personas que puede acomodar.|
| Estado         | string  | Estado actual de la mesa ("disponible", "ocupada"). |

### 5. Usuario (Cliente)
Representa a los clientes del restaurante.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Usuario     | int     | Identificador único del cliente.             |
| Nombre         | string  | Nombre del cliente.                          |
| Teléfono       | string  | Número de teléfono del cliente.              |
| Dirección      | string  | Dirección del cliente.                       |

### 6. Factura
Representa la factura generada para una orden.

| Atributo       | Tipo    | Descripción                                  |
|----------------|---------|----------------------------------------------|
| ID_Factura     | int     | Identificador único de la factura.          |
| ID_Orden       | int     | Identificador de la orden asociada a la factura.|
| Fecha          | date    | Fecha de emisión de la factura.             |
| Total          | decimal | Total a pagar indicado en la factura.       |
| MetodoPago     | string  | Método de pago utilizado (efectivo, tarjeta, etc.). |
