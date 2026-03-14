# Carrito de Compras (Java)

Este proyecto es un ejemplo de cómo modelar un carrito de compras con buenas prácticas de diseño en Java: separación de responsabilidades, encapsulación, validación de datos y manejo de excepciones.

## 📦 Estructura del proyecto

- `CarritoDeCompras.java` — Lógica del carrito, cálculo de totales, impresión y gestión de cantidades.
- `Item.java` — Representa un artículo con validación de precios y formato de impresión.
- `CarritoApp.java` — Programa principal que usa el carrito.

## ✅ Mejoras aplicadas

### Separación de responsabilidades
- `CarritoDeCompras` es una entidad independiente y no contiene el método `main`.
- `CarritoApp` es el punto de entrada del programa.

### Encapsulación y validación
- `Item` ya no expone atributos públicos.
- Se agregaron getters y setters con validación de precios.
- El constructor de `Item` también valida los datos.

### Manejo de errores
- Si se trata de eliminar un artículo que no existe en el carrito, se lanza una excepción (`IllegalStateException`).
- Se valida que las cantidades sean positivas.

### Impresión y `toString`
- `Item#toString()` devuelve un texto formateado.
- `CarritoDeCompras#imprimirDetalle()` usa el método de `Item` para evitar duplicar lógica de impresión.

### Escalabilidad
- El carrito usa un `Map<Item,Integer>` para permitir rápido acceso y gestión de cantidades.
- Para volúmenes mayores, sería apropiado considerar:
  - Persistencia en base de datos.
  - Estructuras de datos con paginación / streams.
  - Algoritmos de procesamiento en lotes.

## 🧪 Cómo ejecutar

Desde la carpeta del proyecto:

```sh
javac *.java
java CarritoApp
```

## ⚠️ Notas

- Los límites de precio (`MIN_PRICE`, `MAX_PRICE`) están definidos en `Item.java`. Ajusta según el modelo de negocio.
- El símbolo de moneda (`CURRENCY_SYMBOL`) está definido en `CarritoDeCompras`.
