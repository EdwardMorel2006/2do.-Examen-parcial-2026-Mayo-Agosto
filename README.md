**SUSTENTANTE: EDWARD ALBERTO MOREL RAMIREZ (2025-1672)**

Cafetería El Buen Sabor

## Descripción del programa

Aplicación de escritorio desarrollada con Windows Forms y C#. Permite registrar los productos solicitados por un cliente en la cafetería **El Buen Sabor**, calcular los importes del pedido y mostrar el total a pagar.

## Datos de entrada

El usuario ingresa o selecciona los siguientes datos:

- Nombre del cliente.
- Fecha del pedido.
- Si el cliente es frecuente.
- Nombre del producto.
- Precio base del producto.
- Cantidad, de 1 a 20.
- Tamaño: normal o grande.
- Si lleva porción extra.
- Tipo de servicio: consumir en local o para llevar.

## Procesos

1. Parte del precio base digitado.
2. Suma RD$ 25.00 si el tamaño es grande.
3. Suma RD$ 30.00 si lleva porción extra.
4. Multiplica el precio unitario por la cantidad para calcular el total de cada producto.
5. Acumula las líneas en el subtotal.
6. Aplica un descuento del 10 % si el cliente es frecuente.
7. Suma RD$ 20.00 de empaque si el pedido es para llevar.
8. Calcula el ITBIS, equivalente al 18 % de la base imponible.
9. Calcula el total final del pedido.

## Datos de salida

El programa muestra:

- Lista de productos agregados, con cantidad, producto, precio unitario y total por línea.
- Subtotal.
- Descuento aplicado.
- Costo de empaque.
- ITBIS.
- Total a pagar.
