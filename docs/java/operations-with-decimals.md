---
sidebar_position: 1
---

# Operaciones con decimales

Al trabajar con decimales hay que tener especial cuidado al querer redondear cantidades por la precisión de Java. 
Por ejemplo, al ejecutar la siguiente operación:

```
(int) (Double.valueOf(36776.52) * 100)
```

El resultado es:

```
3677651
```

Aunque matemáticamente:

```
36776.52 * 100 = 3677652
```

con double realmente puedes obtener internamente algo parecido a:

```
3677651.9999999995
```

Y al hacer el cast:

```
(int) 3677651.9999999995
```

Java trunca los decimales, por lo que queda:

```
3677651
```

Si quieres obtener correctamente 3677652, mejor:

```
(int) Math.round(Double.valueOf(36776.52) * 100)
```

Resultado:

```
3677652
```

Para importes monetarios, además, es preferible usar BigDecimal para evitar este tipo de errores de precisión.