# 🧪 Guía de Pruebas - Sistema de Pollos a la Brasa

## Prueba 1: Verificar que las Estadísticas se Guardan por Fecha

### Paso 1: Crear un Pedido Hoy
1. Abre index.html en el navegador
2. Ve a la pestaña **"Pedidos"**
3. Selecciona tipo de pedido: **"Para Mesa"**
4. Selecciona una mesa (ej: Mesa 2, Mesa 3, Mesa 5)
5. Agrega algunos productos (Pollos, bebidas, extras)
6. Ingresa el nombre del cliente
7. Haz clic en **"Guardar Pedido"**
8. Verifica que:
   - ✅ Aparezca un mensaje: "Pedido registrado exitosamente"
   - ✅ La mesa esté bloqueada (no puedas seleccionarla)
   - ✅ El pedido aparezca en la pestaña "Pedidos Actuales" con la fecha de hoy

### Paso 2: Verificar la Fecha Guardada
1. Ve a la pestaña **"Historial"**
2. Busca el pedido que acabas de crear
3. Verifica que:
   - ✅ La fecha sea la de HOY (con la hora correcta)
   - ✅ Aparezca tu nombre del cliente
   - ✅ Aparezca el número de mesa correcto

### Paso 3: Pagar el Pedido
1. Ve a la pestaña **"Pedidos Actuales"**
2. Haz clic en **"Marcar como Pagado"** del pedido que creaste
3. Selecciona un método de pago (Efectivo, Yape o Tarjeta)
4. Verifica que:
   - ✅ Aparezca un mensaje: "Pedido #X pagado con [Método]"
   - ✅ Aparezca: "Mesa X ahora está disponible"
   - ✅ La mesa vuelva a estar disponible en el dropdown de mesas

### Paso 4: Verificar Estadísticas
1. Ve a la pestaña **"Estadísticas"**
2. Verifica que:
   - ✅ El total de ingresos actualizado (S/ XXX.XX)
   - ✅ Total de pedidos actualizado
   - ✅ Gráficos mostrando datos de hoy
   - ✅ Solo aparezcan los pedidos de HOY (no de otros días)

---

## Prueba 2: Verificar Bloqueo de Mesas para TODAS las Mesas

### Prueba 2A: Mesa 2
1. Ve a **"Pedidos"**
2. Selecciona **"Para Mesa"**
3. En el dropdown de mesas, selecciona **"Mesa 2"**
4. Agrega un producto
5. Ingresa nombre del cliente
6. Haz clic en **"Guardar Pedido"**
7. Verifica que:
   - ✅ La Mesa 2 ahora esté marcada como 🔒 BLOQUEADA en el dropdown
   - ✅ No puedas seleccionar la Mesa 2 de nuevo
   - ✅ Las otras mesas (1, 3, 4, 5, 6, 7, 8) sigan disponibles

### Prueba 2B: Mesa 5
1. Selecciona **"Mesa 5"** en el dropdown
2. Agrega un producto
3. Ingresa nombre del cliente
4. Haz clic en **"Guardar Pedido"**
5. Verifica que:
   - ✅ La Mesa 5 ahora esté marcada como 🔒 BLOQUEADA
   - ✅ La Mesa 2 siga bloqueada (del pedido anterior)
   - ✅ Las otras mesas sigan disponibles

### Prueba 2C: Desbloquear Mesas
1. Ve a **"Pedidos Actuales"**
2. Haz clic en **"Marcar como Pagado"** del pedido en Mesa 2
3. Selecciona método de pago
4. Verifica que:
   - ✅ Aparezca: "Mesa 2 ahora está disponible"
   - ✅ En el dropdown, Mesa 2 ya no esté bloqueada
   - ✅ Mesa 5 siga bloqueada (tiene pedido pendiente)
5. Haz lo mismo con el pedido de Mesa 5
6. Verifica que:
   - ✅ Todas las mesas vuelvan a estar disponibles

---

## Prueba 3: Agregar Nueva Mesa (Escalabilidad)

### Paso 1: Agregar una Mesa Nueva
1. Ve a la pestaña **"Administración"**
2. En la sección "Gestión de Mesas", haz clic en **"Agregar Mesa"**
3. Ingresa el número: **9** (o cualquier número mayor a 8)
4. Haz clic en **"Guardar"**
5. Verifica que:
   - ✅ Aparezca el mensaje: "Mesa guardada exitosamente"
   - ✅ La Mesa 9 aparezca en la tabla de mesas

### Paso 2: Usar la Nueva Mesa
1. Ve a **"Pedidos"**
2. En el dropdown de mesas, scrollea hacia abajo
3. Verifica que:
   - ✅ La Mesa 9 aparezca en el dropdown
4. Selecciona **"Mesa 9"**
5. Agrega un producto
6. Ingresa nombre del cliente
7. Haz clic en **"Guardar Pedido"**
8. Verifica que:
   - ✅ La Mesa 9 se bloquee correctamente
   - ✅ El pedido se registre con la Mesa 9
   - ✅ Puedas desbloquearla pagando

### Paso 3: Agregar Más Mesas
1. Repite los pasos para agregar Mesa 10, Mesa 11, etc.
2. Verifica que todas funcionen correctamente

---

## Prueba 4: Verificar Separación por Fechas

### Paso 1: Crear Pedidos Hoy (Sábado)
1. Crea 2-3 pedidos en mesas diferentes hoy
2. Paga todos los pedidos
3. Ve a **"Estadísticas"**
4. Anota el total de ingresos (ej: S/ 150.00)

### Paso 2: Simular Cambio de Día (Opcional)
*Nota: Para esta prueba necesitarías cambiar la hora del sistema o esperar a mañana*

1. Si esperas a mañana (domingo):
   - Abre el sistema nuevamente
   - Ve a "Pedidos Actuales"
   - Verifica que NO aparezcan los pedidos de sábado
   - Los pedidos de sábado estarán en "Historial" con la fecha correcta

---

## Checklist de Verificación ✅

### Estadísticas por Fecha
- [ ] Los pedidos se guardan con la fecha correcta de hoy
- [ ] Las estadísticas muestran solo los pedidos de hoy
- [ ] Los datos de días anteriores se mantienen en el historial
- [ ] Si cambias de día, las estadísticas se limpian (solo muestran el día actual)

### Bloqueo de Mesas
- [ ] Mesa 1 se bloquea cuando tiene pedido
- [ ] Mesa 2 se bloquea cuando tiene pedido
- [ ] Mesa 3 se bloquea cuando tiene pedido
- [ ] Mesa 4 se bloquea cuando tiene pedido
- [ ] Mesa 5 se bloquea cuando tiene pedido
- [ ] Mesa 6 se bloquea cuando tiene pedido
- [ ] Mesa 7 se bloquea cuando tiene pedido
- [ ] Mesa 8 se bloquea cuando tiene pedido
- [ ] Las mesas se desbloquean cuando se paga el pedido
- [ ] Múltiples mesas pueden estar bloqueadas al mismo tiempo

### Escalabilidad
- [ ] Puedes agregar nuevas mesas (9, 10, 11, etc.)
- [ ] Las nuevas mesas funcionan con bloqueo/desbloqueo
- [ ] Las nuevas mesas aparecen en el dropdown de pedidos
- [ ] Puedes eliminar mesas (si no tienen pedidos)

---

## 🆘 Si Algo No Funciona

### Los pedidos no aparecen en estadísticas:
- Verifica que la fecha del sistema sea correcta
- Abre el Developer Console (F12) y busca errores

### Las mesas no se bloquean:
- Abre el Developer Console (F12)
- Busca mensajes con ✓ o ✗ sobre mesas
- Si ves errores, toma una captura y reporta

### Los datos no se guardan:
- Abre el Developer Console (F12)
- Busca "Datos guardados correctamente en localStorage"
- Si ves errores, verifica el localStorage del navegador

### Limpiar datos (si necesitas empezar de cero):
1. Abre el navegador (Chrome, Firefox, Edge)
2. Presiona F12 para abrir Developer Tools
3. Ve a la pestaña "Application" o "Storage"
4. Selecciona "Local Storage"
5. Haz clic derecho y "Clear All"
6. Recarga la página

---

¡Felicidades! El sistema debería estar funcionando perfectamente ahora. 🎉
