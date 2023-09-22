# BD VENTAS DE EMPRESA
## PROBLEMA A RESOLVER 

Se quiere diseñar una BD que permita registrar las ventas de una empresa. 
Específicamente, esta empresa necesita llevar un control de proveedores, clientes,
productos y ventas.
Un proveedor se modela con CUIT, nombre, dirección, teléfono y página web. Un cliente
también se modela con CUIT, nombre y dirección, pero puede tener varios teléfonos de
contacto. De cada dirección,nos interesa su calle, número, comuna y ciudad. Tanto para
los proveedores como los clientes, el CUIT esun valor único (equivalente al DNI).
De los productos, sabemos que tienen un identificador único, nombre, precio actual, stock 
y nombre del proveedor que los comercializa. Además se organizan en categorías, y cada 
producto se clasifica solamente en una de ellas, pero sin embargo una categoría clasifica
varios productos. De ellas nos interesa saber suid, nombre y descripción.
Sabemos que un producto es comercializado por varios proveedores, pero que un
proveedor provee unsolo producto.
Por razones de contabilidad, se debe registrar la información de cada venta , las cuales
tienen un númerode factura (que es único), fecha, cliente, descuento y monto final. A 
su vez, sabemos que una venta se compone de varios productos, y por eso nos interesa 
el precio al momento de la venta del producto, la cantidad vendida y el monto total por
él. Tenga en cuenta que un producto puede estar en varias ventas,pero que podemos 
tener un producto que no haya sido vendido. Adicionalmente, sabemos que cada clien- te
puede realizar varias ventas, y en una venta solamente participa un cliente. 


Para diseñar una base de datos que permita registrar las ventas de la empresa , debemos tener en cuenta las tabals y relaciones a relizar , en este caso se realizaran las siguientes tablas y relaciones :

1. ***Tabla "Proveedores":***

    CUIT (clave primaria)
    Nombre
    Dirección
    Teléfono
    Página web

2. ***Tabla "Clientes":***

    CUIT (clave primaria, equivalente al DNI)
    Nombre
    Dirección (calle, número, comuna, ciudad)
    Teléfonos de contacto (puede ser una tabla aparte relacionada por CUIT del cliente)

3. ***Tabla "Productos":***

   Identificador único
   Nombre
   Precio actual
   Stock
   Proveedor (clave externa que referencia a la tabla de Proveedores)
   Categoría (clave externa que referencia a la tabla de Categorías de Productos)

4. ***Tabla "Categorías de Productos":***

   ID (clave primaria)
   Nombre
   Descripción

5. ***Tabla "Ventas":***

   Número de factura (clave primaria)
   Fecha
   Cliente (clave externa que referencia a la tabla de Clientes)
   Descuento
   Monto final

6. ***Tabla "Detalles de Venta":***

   ID (clave primaria)
   Venta (clave externa que referencia a la tabla de Ventas)
   Producto (clave externa que referencia a la tabla de Productos)
   Precio al momento de la venta
   Cantidad vendida
   Monto total por producto

Con estas tablas y relaciones, podemos registrar información detallada sobre proveedores, clientes, productos, categorías de productos, ventas y los detalles de cada venta, incluyendo los productos vendidos. Además, nos aseguramos de establecer las restricciones de integridad referencial necesarias para mantener la consistencia de la base de datos.

## DAGRAMA DE FLUJO RELACION DE TABLAS

![image](https://github.com/Diegogonzalezdr/mbasededatos/assets/133602952/ab1a11cb-70a9-415a-a301-1b852c988bc9)

## CASO DE USO 


***Nombre del caso de uso:*** Registrar una nueva venta

***Actores involucrados:*** Empleado de la empresa (usuario)

***Objetivo:*** Registrar una nueva venta en el sistema, incluyendo los productos vendidos y la información del cliente.

***Flujo principal de eventos:***

- El empleado inicia sesión en el sistema de gestión de ventas.

- El empleado selecciona la opción "Registrar Nueva Venta" en el menú principal.

- El sistema muestra un formulario vacío para ingresar los detalles de la venta.

- El empleado completa los siguientes campos del formulario:

   1. Fecha de la venta.
   2. Cliente (seleccionando de una lista de clientes existentes o ingresando nuevos detalles si es un cliente nuevo).
   3. Descuento (si corresponde).
   4. El empleado agrega los productos vendidos a la venta:

- Para cada producto, ingresa el nombre del producto o lo selecciona de una lista.
- Ingresa la cantidad vendida.
- El sistema calcula automáticamente el precio al momento de la venta y el monto total por producto.
- El empleado confirma la venta.

- El sistema valida la información ingresada y verifica que los productos estén disponibles en el stock.
(Si la información es válida, el sistema registra la venta en la base de datos, actualiza el stock de productos y genera un número de factura único.)

- El empleado recibe una confirmación de que la venta se ha registrado con éxito y se le proporciona el número de factura.

***Flujo alternativo:*** Si la información ingresada es inválida (por ejemplo, cantidad de productos no disponible en el stock), el sistema mostrará un mensaje de error y permitirá al empleado corregir la información.

Este caso de uso ilustra cómo un empleado de la empresa utiliza la base de datos para registrar una nueva venta, incluyendo la selección de productos, la asignación de un cliente y el cálculo de los montos totales.
