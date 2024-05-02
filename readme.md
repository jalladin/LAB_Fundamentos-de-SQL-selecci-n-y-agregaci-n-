![logo_ironhack_blue 7](https://user-images.githubusercontent.com/23629340/40541063-a07a0a8a-601a-11e8-91b5-2f13e4e6b441.png)

# Lab | Fundamentos de SQL (selección y agregación)

## Introducción

En este laboratorio, utilizarás la base de datos `files_for_lab/mysql_dump.sql`. Cárgala en MySQL Workbench, y allí encontrarás una base de datos llamada `bank` que usaremos para el siguiente ejercicio.

Una forma posible de cargarla a través de MySQL Workbench sería: `Server > Data import > Import from self-contained file > selecciona la ruta a tu archivo haciendo clic en el punto > Start import`.

Aquí, practicarás seleccionar y proyectar datos. Puedes responder todas las preguntas usando solo estas cláusulas:

- `SELECT`
- `SELECT DISTINCT`
- `FROM`
- `WHERE`
- `ORDER BY`
- `LIMIT`

Puedes guardar tus soluciones en un archivo `solutions.sql`.

## Instrucciones

Asume que cualquier columna `_id` es incremental, lo que significa que los ids más altos siempre ocurren después de los ids más bajos. Por ejemplo, un cliente con un `client_id` más alto se unió al banco después de un cliente con un `client_id` más bajo.

### Consulta 1

Obtén los valores de `id` de los primeros 5 clientes del `district_id` con un valor igual a 1.

Resultado esperado:

```shell
2
3
22
23
28
```

### Consulta 2

En la tabla `client`, obtén el valor de `id` del último cliente donde el `district_id` sea igual a 72.

Resultado esperado:


```shell
13576
```

### Consulta 3

Obtén las 3 cantidades más bajas en la tabla `loan`.

Resultado esperado:


```shell
4980
5148
7656
```

### Consulta 4

¿Cuáles son los valores posibles para `status`, ordenados alfabéticamente en orden ascendente en la tabla `loan`?

Resultado esperado:


```shell
A
B
C
D
```

### Consulta 5

¿Cuál es el `loan_id` del pago más alto recibido en la tabla `loan`?

Resultado esperado:


```shell
6415
```

### Consulta 6

¿Cuál es el monto del préstamo de los 5 `account_id` más bajos en la tabla `loan`? Muestra el `account_id` y el monto correspondiente.

Resultado esperado:


```shell
#id     amount
2	    80952
19	    30276
25	    30276
37	    318480
38	    110736
```

### Consulta 7

¿Cuáles son los `account_id` con el monto de préstamo más bajo que tienen una `duration` de préstamo de 60 en la tabla `loan`?

Resultado esperado:


```shell
10954
938
10711
1766
10799
```

### Consulta 8

¿Cuáles son los valores únicos de `k_symbol` en la tabla `order`?

Nota: No debería haber un nombre de tabla `order`, ya que `order` está reservado para la cláusula `ORDER BY`. Tienes que usar comillas invertidas para escapar el nombre de la tabla `order`.

Resultado esperado:


```shell
LEASING
POJISTNE
SIPO
UVER
```

### Consulta 9

En la tabla `order`, ¿cuáles son los `order_id` del cliente con el `account_id` 34?

Resultado esperado:


```shell
29445
29446
29447
```

### Consulta 10

En la tabla `order`, ¿qué `account_id` fueron responsables de las órdenes entre `order_id` 29540 y `order_id` 29560 (inclusive)?

Resultado esperado:


```shell
88
90
96
97
```

### Consulta 11

En la tabla `order`, ¿cuáles son los montos individuales que fueron enviados a (`account_to`) id 30067122?

Resultado esperado:


```shell
5123
```

### Consulta 12

En la tabla `trans`, muestra el `trans_id`, `date`, `type` y `amount` de las 10 primeras transacciones del `account_id` 793 en orden cronológico, de las más recientes a las más antiguas.

Resultado esperado:


```shell
3556468	981231	PRIJEM	78.6
233254	981216	VYDAJ	600
233104	981212	VYDAJ	1212
233248	981211	VYDAJ	851
233176	981207	VYDAJ	204
3556467	981130	PRIJEM	75.1
233395	981130	VYDAJ	14.6
233103	981112	VYDAJ	1212
233247	981111	VYDAJ	851
233175	981107	VYDAJ	204
```

### Consulta 13

En la tabla `client`, de todos los distritos con un `district_id` menor que 10, ¿cuántos clientes hay de cada `district_id`? Muestra los resultados ordenados por `district_id` en orden ascendente.

Resultado esperado:


```shell
1	663
2	46
3	63
4	50
5	71
6	53
7	45
8	69
9	60
```

### Consulta 14

En la tabla `card`, ¿cuántas tarjetas existen para cada `type`? Ordena el resultado comenzando con el `type` más frecuente.

Resultado esperado:


```shell
classic	659
junior	145
gold	88
```

### Query 15

Using the `loan` table, print the top 10 `account_id`s based on the sum of all of their loan amounts.

Expected result:

```shell
7542	590820
8926	566640
2335	541200
817	    538500
2936	504000
7049	495180
10451	482940
6950	475680
7966	473280
339	    468060
```

### Query 16

In the `loan` table, retrieve the number of loans issued for each day, before (excl) 930907, ordered by date in descending order.

Expected result:

```
930906	1
930803	1
930728	1
930711	1
930705	1
```

### Query 17

In the `loan` table, for each day in December 1997, count the number of loans issued for each unique loan duration, ordered by date and duration, both in ascending order. You can ignore days without any loans in your output.

Expected result:

```shell
971206	24	1
971206	36	1
971208	12	3
971209	12	1
971209	24	1
971210	12	1
971211	24	1
971211	48	1
971213	24	1
971220	36	1
971221	36	1
971224	60	1
971225	24	1
971225	60	1
```

### Query 18

In the `trans` table, for `account_id` 396, sum the amount of transactions for each type (`VYDAJ` = Outgoing, `PRIJEM` = Incoming). Your output should have the `account_id`, the `type` and the sum of amount, named as `total_amount`. Sort alphabetically by type.

Expected result:

```shell
396	PRIJEM	1028138.6999740601
396	VYDAJ	1485814.400024414
```
