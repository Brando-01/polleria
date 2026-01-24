# 🔍 Instrucciones para Debugging de Mesa 2

## Paso 1: Abre la consola de navegador
1. Abre `index.html` en tu navegador
2. Presiona **F12** para abrir Developer Tools
3. Ve a la pestaña **"Console"**

## Paso 2: Crea un pedido en Mesa 2

1. Ve a la pestaña de "Pedidos"
2. **MUY IMPORTANTE**: Abre la consola (F12) ANTES de hacer nada
3. Selecciona: **Para Mesa**
4. En el dropdown de mesas, selecciona **Mesa 2**
5. Agrega un producto (cualquiera)
6. Ingresa un nombre de cliente
7. Haz clic en **"Guardar Pedido"**

## Paso 3: Revisa los logs en la consola

Deberías ver mensajes como estos (mira especialmente los que dicen `[DEBUG]`):

### BUENOS LOGS (si funciona):
```
✓ tableSelect encontrado, tiene 8 mesas en total
Órdenes en sistema: 1
Órdenes pendientes: (1) [{id: 1, tableNumber: "2", status: "pendiente"}]
[DEBUG MESA 2] Order#1: "2" (int: 2) vs Mesa "2" (int: 2) = true
✓ Mesa 2 BLOQUEADA
✓✓✓ Mesa 2 ahora está ocupada
```

### MALOS LOGS (si no funciona):
```
✓ tableSelect encontrado, tiene 8 mesas en total
Órdenes en sistema: 1
Órdenes pendientes: (1) [{id: 1, tableNumber: "2", status: "pendiente"}]
[DEBUG MESA 2] Order#1: "2" (int: 2) vs Mesa "2" (int: 2) = false  ← PROBLEMA: false!
```

## Paso 4: Si ves FALSE en la comparación

Si ves `= false` cuando debería ser `= true`, copia estos logs completos en la consola:

```javascript
// Pega esto en la consola y ejecuta:
console.log('Tables:', tables);
console.log('Orders:', orders);
console.log('Mesa 2:', tables.find(t => t.number === '2'));
console.log('Order en mesa 2:', orders.find(o => o.type === 'table' && o.tableNumber === '2'));
```

Copia el resultado completo.

## Paso 5: Verifica en el dropdown de mesas

Después de crear el pedido en mesa 2:
1. Haz clic nuevamente en el dropdown de mesas
2. **Mesa 2 debería decir "Mesa 2 - 🔒 BLOQUEADA"**
3. Si no dice eso, entonces el problema está en `loadTables()`

## Paso 6: Prueba otros pasos

1. Crea un pedido en **Mesa 1** - ¿Se bloquea?
2. Crea un pedido en **Mesa 3** - ¿Se bloquea?
3. Crea un pedido en **Mesa 2 de nuevo** - ¿Se bloquea esta vez?

---

## Archivos de ayuda

- **TEST_MESA_2.html** - Abre este archivo y prueba los botones para hacer debugging local
- **index.html** - El sistema principal (con debugging agregado)

---

## Qué buscar

Si Mesa 2 no se bloquea:

1. ¿Aparecen los logs de `[DEBUG MESA 2]` en la consola?
   - Si NO → El código no está siendo ejecutado
   - Si SÍ → El código se ejecuta pero da false

2. ¿Dice `parseInt = 2` en ambos lados?
   - Si NO → Hay un problema con cómo se guarda/lee el número

3. ¿Dice `match = true` o `match = false`?
   - Si false → Los números NO coinciden por alguna razón
   - Si true → Debería estar bloqueada, pero no lo está

---

## Envía estos datos:

Si el problema persiste, copia en el chat:

1. Los logs completos de la consola (F12 → Console)
2. El resultado de ejecutar en la consola:
   ```javascript
   JSON.stringify({tables, orders})
   ```
3. Cuál mesa SE bloquea y cuál NO se bloquea

Así podré identificar exactamente qué está pasando.
