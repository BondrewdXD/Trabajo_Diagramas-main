# Diagrama UML de Despliegue para Sistema de Restaurante

Este documento describe el diagrama de despliegue que representa la arquitectura de implementación del sistema de gestión para un restaurante.

## Estructura del Despliegue

### 1. **Nodos del Sistema**

#### a. Servidor de Aplicación
Este nodo contiene los servicios que gestionan la lógica de negocio del sistema:
- **PlatoService**: Se encarga de las operaciones relacionadas con los platos.
- **OrdenService**: Maneja las órdenes realizadas en el restaurante.
- **DetalleOrdenService**: Gestiona los detalles específicos de cada orden.
- **UsuarioService**: Administra la información de los usuarios.
- **FacturaService**: Genera y maneja las facturas asociadas a las órdenes.

#### b. Base de Datos
Este nodo representa el almacenamiento persistente de datos:
- **BaseDeDatos**: Contiene las siguientes tablas:
  - **Plato**: Información sobre los platos disponibles.
  - **Detalle_Orden**: Detalles de los platos en cada orden.
  - **Orden**: Información sobre las órdenes realizadas.
  - **Mesa**: Información sobre las mesas disponibles en el restaurante.
  - **Usuario**: Datos de los usuarios del sistema.
  - **Factura**: Información sobre las facturas generadas.

#### c. Cliente
Este nodo representa la interfaz con la que interactúan los usuarios del sistema:
- **Interfaz de Usuario**: Proporciona la experiencia visual y de interacción para los usuarios.

## Relaciones y Flujo de Datos

- **Interfaz de Usuario** se comunica con **PlatoService** para realizar peticiones relacionadas con los platos.
- **PlatoService** consulta y actualiza la información de los platos en **BaseDeDatos**.
- **OrdenService** consulta y actualiza órdenes en **BaseDeDatos**.
- **DetalleOrdenService** consulta y actualiza detalles de órdenes en **BaseDeDatos**.
- **UsuarioService** consulta y actualiza la información de los usuarios en **BaseDeDatos**.
- **FacturaService** consulta y actualiza la información de las facturas en **BaseDeDatos**.

## Conclusión

Este diagrama de despliegue ilustra cómo los componentes del sistema se distribuyen en diferentes nodos, mostrando la interacción entre el cliente, los servicios de aplicación y la base de datos. Facilita la comprensión de la arquitectura del sistema y el flujo de datos entre los distintos componentes involucrados en el funcionamiento del sistema de gestión de restaurante.
