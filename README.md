# Resolución ejercicio calculo rompe cabeza

Para empezare se necesita una función que tiene como parámetro (N), dentro de esta función existen 4 variables A,B,C y D, cada una de ellas se le asigna un valor de 1.

```tsx
function solucionarRompecabezas(N) {
		let A = 1n;
    let B = 1n;
    let C = 1n;
    let D = 1n;

```

Para este ejercicio que lo he resulto con javascript, es necesario utilizar BigInt para poder utilizar números grandes (La sintaxis para bigInt es adjuntar la letra “n” a la derecha del valor numérico o utilizando BigInt()).

Luego dentro de la función se realiza un ciclo for que itera desde 1 hasta (N) dependiendo del valor que se ingreso como argumento.

```tsx
for (let i = 1; i <= N; i++)
```

Dentro del ciclo for, primero se crea una variable llamada resultado que multiplica

```tsx
3n * D + 1n * C + 4n * B + 1n * A;
```

Para la primera iteración reemplazando sus valores quedaría de la siguiente manera

```tsx
3n * 1n + 1n * 1n + 4n * 1n + 1n * 1n

= 3n + 1n + 4n + 1n

= 9n
```

Luego asignamos el valor de B a A

```tsx
A = B = 1n;
B = C = 1n;
C = D = 1n;
D = resultado = 9n;
```

de esta manera cambiamos el valor de D para la siguiente iteración.

Calculemos la segunda iteración

```tsx
3n * 9n + 1n * 1n + 4n * 1n + 1n + 1n

= 27n + 1n + 4n + 1n

= 33n
```

En este momento es cuando cambia otra variable si asignamos sus valores actuales

```tsx
A = B = 1n;
B = C = 1n;
C = D = 9n; // aqui ya cambia el valor de C
D = 33n; // que es el nuevo resultado del calculo anterior
```

Esto ira aumentando cada vez dependiendo del valor de iteración que se dio como argumento.

Por ultimo dentro de la función se pide que del resultado de la ultima iteración se le calcule el resto de 10000000000, para así obtener los últimos dies números del valor obtenido.

```tsx
return Number(D % 10000000000n);

}
```

Resultados:

```tsx
solucionarRompecabezas(10); //902441 , correcto segun la guia
solucionarRompecabezas(100); //8042318513, correcto segun la guia
solucionarRompecabezas(Math.pow(2023, 100)); // no es capaz de calcularlo
```

\*Quizás con alguna maquina mas poderosa u otro algoritmo sea posible el calculo

\*En javaScript dado que después de sobre pasar el numero máximo seguro (Number.MAX_SAFE_INTEGER) , la precisión de los cálculos baja, es necesario utilizar BigInt.

```tsx
function solucionarRompecabezas(N) {
	let A = 1n;
	let B = 1n;
	let C = 1n;
	let D = 1n;

	for (let i = 1; i <= N; i++) {
		let resultado = 3n * D + 1n * C + 4n * B + 1n * A;
		A = B;
		B = C;
		C = D;
		D = resultado;
	}

	return Number(D % 10000000000n); // Últimos 10 dígitos de var_D
}

solucionarRompecabezas(10);
solucionarRompecabezas(100);
solucionarRompecabezas(BigInt(Math.pow(2023, 100)));
```
