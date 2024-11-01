# Diagrama UML de Objetos para Sistema de Restaurante

Este documento describe el diagrama de objetos que representa instancias específicas de las clases en un sistema de gestión para un restaurante.

## Objetos

### 1. **plato**
- **ID_Plato**: 1
- **Nombre**: "Ensalada César"
- **Descripción**: "Ensalada fresca con pollo y aderezo César"
- **Precio**: 12.50
- **Foto**: "url_foto_ensalada"

### 2. **detalleOrden**
- **ID_Detalle**: 1
- **ID_Orden**: 1001
- **ID_Plato**: 1
- **Cantidad**: 2
- **Sopa**: false
- **Postre**: true
- **Domicilio**: false

### 3. **orden**
- **ID_Orden**: 1001
- **ID_Mesa**: 1
- **HoraPedido**: "2024-10-30 12:30"
- **Total**: 35.00

### 4. **usuario**
- **ID_Usuario**: 1
- **Nombre**: "Juan Pérez"
- **Teléfono**: "123456789"
- **Dirección**: "Calle Falsa 123"

### 5. **factura**
- **ID_Factura**: 5001
- **ID_Orden**: 1001
- **Fecha**: "2024-10-30"
- **Total**: 35.00
- **MetodoPago**: "tarjeta de crédito"

## Relaciones

- **plato** "es parte de" **detalleOrden**: El plato "Ensalada César" es parte del detalle de la orden.
- **orden** "contiene" **detalleOrden**: La orden con ID 1001 contiene el detalle de la orden.
- **orden** "genera" **factura**: La orden genera una factura asociada.
- **usuario** "realiza" **orden**: El usuario "Juan Pérez" realiza la orden.
- **detalleOrden** "incluye el plato" **plato**: El detalle de la orden incluye el plato "Ensalada César".

## Conclusión

Este diagrama de objetos muestra instancias específicas de clases del sistema, destacando cómo se relacionan entre sí. Cada objeto representa un elemento del sistema en un momento particular, proporcionando una vista detallada del estado de los datos y sus interacciones en el contexto de una orden en un restaurante.
