# Diagrama UML de Componentes para Sistema de Restaurante

Este documento describe el diagrama de componentes que representa la arquitectura del sistema de gestión para un restaurante.

## Componentes

### 1. **PlatoService**
- **Función**: Maneja las operaciones relacionadas con los platos, como la consulta y actualización de los mismos.
- **Interacciones**:
  - Se comunica con **BaseDeDatos** para consultar y actualizar información de los platos.
  - Proporciona información del plato a **DetalleOrdenService**.

### 2. **OrdenService**
- **Función**: Se encarga de gestionar las órdenes realizadas en el restaurante.
- **Interacciones**:
  - Se comunica con **BaseDeDatos** para consultar y actualizar órdenes.
  - Agrega detalles a las órdenes utilizando **DetalleOrdenService**.
  - Genera facturas a través de **FacturaService**.
  - Recibe solicitudes de órdenes de **UsuarioService**.

### 3. **DetalleOrdenService**
- **Función**: Maneja los detalles específicos de cada orden, como los platos seleccionados.
- **Interacciones**:
  - Consulta y actualiza detalles de órdenes en **BaseDeDatos**.
  - Obtiene información de platos de **PlatoService**.
  - Es utilizado por **OrdenService** para agregar detalles a las órdenes.

### 4. **UsuarioService**
- **Función**: Administra la información de los usuarios del sistema, como clientes y empleados.
- **Interacciones**:
  - Consulta y actualiza usuarios en **BaseDeDatos**.
  - Informa a **OrdenService** cuando un usuario realiza una orden.

### 5. **FacturaService**
- **Función**: Genera y maneja las facturas asociadas a las órdenes realizadas.
- **Interacciones**:
  - Consulta y actualiza facturas en **BaseDeDatos**.
  - Recibe solicitudes de generación de facturas desde **OrdenService**.

### 6. **BaseDeDatos**
- **Función**: Almacena toda la información relevante del sistema, incluyendo platos, órdenes, detalles de órdenes, usuarios y facturas.
- **Interacciones**:
  - Es accedida por todos los servicios para realizar consultas y actualizaciones.

## Relaciones

- **PlatoService** consulta y actualiza platos en **BaseDeDatos**.
- **OrdenService** consulta y actualiza órdenes en **BaseDeDatos**.
- **DetalleOrdenService** consulta y actualiza detalles de órdenes en **BaseDeDatos**.
- **UsuarioService** consulta y actualiza usuarios en **BaseDeDatos**.
- **FacturaService** consulta y actualiza facturas en **BaseDeDatos**.
- **PlatoService** proporciona información del plato a **DetalleOrdenService**.
- **OrdenService** agrega detalles a la orden a través de **DetalleOrdenService**.
- **OrdenService** genera facturas usando **FacturaService**.
- **UsuarioService** se comunica con **OrdenService** para registrar órdenes realizadas por los usuarios.

Este diagrama ilustra la interconexión y el flujo de información entre los diferentes componentes del sistema de restaurante, facilitando la comprensión de su arquitectura y funcionamiento.