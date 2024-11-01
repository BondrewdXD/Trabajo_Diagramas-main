# Diagrama UML de Clases para Sistema de Restaurante

Este documento describe el diagrama de clases que representa el modelo de datos para un sistema de gestión de órdenes en un restaurante.

## Clases

### 1. Plato
- **ID_Plato**: Identificador único del plato (int)
- **Nombre**: Nombre del plato (string)
- **Descripción**: Descripción del plato (string)
- **Precio**: Precio del plato (decimal)
- **Foto**: URL o ruta de la foto del plato (string)

### 2. Detalle_Orden
- **ID_Detalle**: Identificador único del detalle de la orden (int)
- **ID_Orden**: Identificador de la orden asociada (int)
- **ID_Plato**: Identificador del plato pedido (int)
- **Cantidad**: Cantidad del plato pedido (int)
- **Sopa**: Indica si se incluye sopa (boolean)
- **Postre**: Indica si se incluye postre (boolean)
- **Domicilio**: Indica si se realiza un pedido a domicilio (boolean)
- **Recipiente**: Indica si se requiere recipiente para el pedido (boolean)

### 3. Orden
- **ID_Orden**: Identificador único de la orden (int)
- **ID_Mesa**: Identificador de la mesa donde se realiza la orden (int)
- **HoraPedido**: Fecha y hora en que se realiza el pedido (datetime)
- **Total**: Total a pagar por la orden (decimal)

### 4. Mesa
- **ID_Mesa**: Identificador único de la mesa (int)
- **Numero_Mesa**: Número de la mesa (int)
- **Capacidad**: Capacidad de la mesa (int)
- **Estado**: Estado actual de la mesa (string)

### 5. Usuario
- **ID_Usuario**: Identificador único del usuario (int)
- **Nombre**: Nombre del usuario (string)
- **Teléfono**: Número de teléfono del usuario (string)
- **Dirección**: Dirección del usuario (string)

### 6. Factura
- **ID_Factura**: Identificador único de la factura (int)
- **ID_Orden**: Identificador de la orden asociada (int)
- **Fecha**: Fecha de emisión de la factura (date)
- **Total**: Total de la factura (decimal)
- **MetodoPago**: Método de pago utilizado (string)

## Relaciones

- **Plato** o-- **Detalle_Orden**: Un plato puede estar contenido en múltiples detalles de orden.
- **Orden** --* **Detalle_Orden**: Una orden puede estar compuesta por múltiples detalles de orden.
- **Orden** o-- **Mesa**: Una orden se realiza en una mesa específica.
- **Usuario** o-- **Orden**: Un usuario realiza una o más órdenes.
- **Factura** -- **Orden**: Una factura se genera para una orden específica.

