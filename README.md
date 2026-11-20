SUSTENTANTE: EDWARD ALBERTO MOREL RAMIREZ (2025-1672)

Cafetería El Buen Sabor

Aplicación de Windows Forms en C# para registrar productos de una cafetería y calcular el total de un pedido.

## Controles principales

- `txtCliente`: escribe el nombre del cliente.
- `dtpFecha`: selecciona la fecha del pedido.
- `chkFrecuente`: indica si el cliente recibe un descuento del 10 %.
- `txtProducto`: escribe el producto.
- `txtPrecio`: escribe el precio base del producto.
- `nudCantidad`: selecciona la cantidad, de 1 a 20.
- `rbtNormal` y `rbtGrande`: seleccionan el tamaño del producto.
- `chkPorcionExtra`: agrega una porción extra.
- `rbtLocal` y `rbtLlevar`: seleccionan el tipo de servicio.
- `lstPedido`: muestra los productos agregados.

## Regla para el precio unitario

El programa comienza con el precio escrito en `txtPrecio`.

- Si el tamaño es grande, suma RD$ 25.00.
- Si tiene porción extra, suma RD$ 30.00.

Después multiplica el precio unitario por la cantidad para obtener el total de la línea.

## Botón Agregar al pedido

El evento `btnAgregar_Click` valida que el producto no esté vacío y que el precio sea válido. Luego:

1. Calcula el precio unitario.
2. Calcula el total de esa línea.
3. Acumula el importe en la variable `subtotal`.
4. Agrega una línea con cantidad, producto, precio y total en `lstPedido`.
5. Limpia los controles del producto para agregar otro.

## Botón Calcular total

El evento `btnCalcular_Click` usa el subtotal de todos los productos:

1. Aplica un descuento del 10 % si `chkFrecuente` está marcado.
2. Agrega RD$ 20.00 de empaque si el servicio es `rbtLlevar`.
3. Calcula la base imponible: `subtotal - descuento + empaque`.
4. Calcula ITBIS: 18 % de la base imponible.
5. Calcula el total final: `base imponible + ITBIS`.

Los resultados se muestran en `lblSubtotal`, `lblDescuento`, `lblEmpaque`, `lblItbis` y `lblTotal`.

## Botón Nuevo pedido

El evento `btnLimpiar_Click` llama al método `ReiniciarPedido()`. Este método borra la lista, los datos escritos y los resultados, y vuelve a dejar la cantidad en 1, tamaño normal y servicio local.

## Botón Salir

El evento `btnSalir_Click` muestra un mensaje de confirmación. El formulario se cierra solamente si se selecciona **Sí**.

## Prueba sugerida

Escribe estos datos y presiona **Agregar al pedido**:

- Cliente: María Pérez
- Cliente frecuente: marcado
- Producto: Sándwich
- Precio: 180
- Cantidad: 2
- Tamaño: Grande
- Servicio: Para llevar
