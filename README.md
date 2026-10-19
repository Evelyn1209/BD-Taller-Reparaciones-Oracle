# Base de datos para taller de reparación de equipos

Base de datos relacional en Oracle (PL/SQL) para gestionar un taller de reparación de equipos: clientes, empleados, equipos, servicios, repuestos y órdenes de trabajo. Desarrollada como proyecto del curso de Bases de Datos, Universidad Castro Carazo. [Proyecto en equipo: describa en una línea qué parte desarrolló usted.]

## Contenido

| Objeto | Cantidad |
|--------|----------|
| Tablas | 16 |
| Índices | 12 |
| Vistas | 5 |
| Funciones | 5 |
| Procedimientos almacenados | 47 |
| Triggers | 10 |

## Funcionalidades

- CRUD de clientes, empleados, equipos, categorías de equipo, servicios y repuestos mediante procedimientos almacenados
- Órdenes de trabajo con estados: Recibido, Diagnóstico, En reparación, Esperando repuestos, Listo para entrega, Entregado y Cancelado
- Creación de una orden con varios ítems (servicios y repuestos) en una sola transacción
- Búsqueda de órdenes y equipos por filtros
- Borrado lógico: al cancelar una orden se cambia su estado, no se elimina
- Control automático de stock de repuestos al agregar ítems a una orden
- Recálculo automático del total de la orden
- Validación de los cambios de estado de una orden
- Auditoría de cambios en personas, equipos, servicios, repuestos y órdenes (tabla `TBL_AUDIT_LOG`)
- Registro de errores (tabla `TBL_ERROR_LOG`)
- Usuarios del sistema con contraseña cifrada (SHA-256) mediante trigger
- Particionamiento por hash en los ítems de las órdenes de trabajo

## Modelo de datos

Tablas principales:

- `TBL_PERSON`, `TBL_IDENTIFICATION_TYPE`, `TBL_CONTACT`, `TBL_CONTACT_METHOD`
- `TBL_CUSTOMERS`, `TBL_EMPLOYEES`, `TBL_SYS_USERS`
- `TBL_EQUIPMENT_CATEGORY`, `TBL_EQUIPMENT`
- `TBL_SERVICES`, `TBL_PARTS`
- `TBL_WORKORDER_STATUS`, `TBL_WORKORDERS_P`, `TBL_WORKORDER_ITEMS_P`
- `TBL_AUDIT_LOG`, `TBL_ERROR_LOG`

[Si tiene el diagrama entidad-relación, súbalo como `diagrama-er.png` y agregue aquí:]
![Diagrama entidad-relación](diagrama-er.png)

## Cómo ejecutarlo

1. Tener Oracle [indique la versión que usó, por ejemplo 19c o XE 21c]. Se requiere 12c o superior por el uso de columnas `IDENTITY`.
2. Abrir Oracle SQL Developer y conectarse a un esquema de prueba.
3. Ejecutar el script `taller_reparaciones.sql` completo, de arriba a abajo.
4. Al final del script hay datos de prueba (personas, clientes, empleados y usuarios de ejemplo). Todos son ficticios.

El script también incluye bloques de prueba, comentados con `-- EXECUTE THE FOLLOWING BLOCK TO TEST ...`, para probar procedimientos como `SP_CREATE_EMPLOYEE`, `SP_GET_EMPLOYEES` y `SP_DELETE_EMPLOYEE`.

## Herramientas

Oracle Database · PL/SQL · Oracle SQL Developer

## Autora

Evelyn Castro Vega
