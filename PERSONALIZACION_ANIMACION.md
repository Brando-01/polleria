# ⚙️ CÓMO PERSONALIZAR LA ANIMACIÓN

## 🎯 Cambios Rápidos y Fáciles

### 1️⃣ DESACTIVAR LA ANIMACIÓN

Si por algún motivo quieres desactivarla, busca en `index.html` esta sección:

```javascript
// Inicializar animación de apertura cuando el DOM esté listo
if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', initOpeningAnimation);
} else {
    initOpeningAnimation();
}
```

Y reemplaza por:

```javascript
// ANIMACIÓN DESACTIVADA
// Simplemente comentamos la inicialización
// if (document.readyState === 'loading') {
//     document.addEventListener('DOMContentLoaded', initOpeningAnimation);
// } else {
//     initOpeningAnimation();
// }
```

---

### 2️⃣ CAMBIAR LA DURACIÓN DE LA ANIMACIÓN

Busca en el CSS estas líneas y cambia el tiempo:

**Para las cortinas (actualmente 1.5s):**
```css
.curtain-left {
    animation: openCurtainLeft 1.5s cubic-bezier(...) forwards;
    /* Cambiar 1.5s a lo que desees: 1s, 2s, 0.8s, etc. */
}

.curtain-right {
    animation: openCurtainRight 1.5s cubic-bezier(...) forwards;
    /* Cambiar 1.5s a lo que desees */
}
```

**Para el logo (actualmente 1.5s):**
```css
.logo-reveal {
    animation: scaleUpLogo 1.5s cubic-bezier(...) forwards;
    /* Cambiar 1.5s a lo que desees */
}
```

**Para el contenido (actualmente 1s):**
```css
.page-content {
    animation: fadeInContent 1s ease-in 0.7s forwards;
    /* Cambiar 1s a lo que desees */
}
```

**Para el contenedor (actualmente 0.8s):**
```css
.page-content .container {
    animation: slideInUp 0.8s ease-out 0.8s forwards;
    /* Cambiar 0.8s a lo que desees */
}
```

---

### 3️⃣ CAMBIAR LOS COLORES DE LAS CORTINAS

Busca estas líneas:

```css
.curtain-left {
    background: linear-gradient(to right, var(--primary), #FF8C42);
    /* var(--primary) = #FF6B35 */
    /* Cambia estos colores a los que desees */
}

.curtain-right {
    background: linear-gradient(to left, var(--primary), #FF8C42);
    /* Cambia estos colores a los que desees */
}
```

**Ejemplos de otros colores:**
- Azul: `#0066FF` y `#0080FF`
- Verde: `#00AA44` y `#00CC55`
- Púrpura: `#8B5CF6` y `#A78BFA`
- Rojo: `#DC2626` y `#EF4444`

---

### 4️⃣ CAMBIAR EL TAMAÑO DEL LOGO

Busca esta sección:

```css
.logo-reveal img {
    width: 180px;   /* CAMBIAR AQUÍ */
    height: 180px;  /* Y AQUÍ */
    object-fit: contain;
    filter: drop-shadow(...);
    background: white;
    border-radius: 20px;
    padding: 20px;
    box-shadow: ...;
}
```

**Ejemplos:**
- Logo pequeño: `width: 120px; height: 120px;`
- Logo mediano: `width: 150px; height: 150px;`
- Logo grande: `width: 200px; height: 200px;`
- Logo muy grande: `width: 250px; height: 250px;`

---

### 5️⃣ CAMBIAR LA SOMBRA DEL LOGO

Busca esta línea:

```css
.logo-reveal img {
    filter: drop-shadow(0 15px 40px rgba(255, 107, 53, 0.4));
    /* ↑ Cambia estos valores */
}
```

**Valores de sombra:**
- `(0 15px 40px rgba(255, 107, 53, 0.4))` - Actual (suave)
- `(0 10px 20px rgba(255, 107, 53, 0.3))` - Más suave
- `(0 20px 50px rgba(255, 107, 53, 0.6))` - Más pronunciada
- `(0 25px 60px rgba(0, 0, 0, 0.3))` - Sombra negra

---

### 6️⃣ CAMBIAR EL EFECTO DE ROTACIÓN DEL LOGO

Busca la animación `scaleUpLogo`:

```css
@keyframes scaleUpLogo {
    0% {
        transform: scale(0.3) rotate(-10deg);  /* Cambiar -10deg */
        opacity: 0;
    }
    40% {
        opacity: 1;
        transform: scale(1.1) rotate(0deg);
    }
    100% {
        transform: scale(1) rotate(0deg);
        opacity: 1;
    }
}
```

**Ejemplos:**
- Sin rotación: `rotate(-0deg)` → `rotate(0deg)`
- Rotación mayor: `rotate(-20deg)` → `rotate(0deg)`
- Girar al revés: `rotate(10deg)` → `rotate(0deg)`

---

### 7️⃣ CAMBIAR LA ESCALA DEL LOGO (Efecto zoom)

En la misma animación `scaleUpLogo`:

```css
@keyframes scaleUpLogo {
    0% {
        transform: scale(0.3) rotate(-10deg);  /* Comenzar en 0.3 */
        opacity: 0;
    }
    40% {
        opacity: 1;
        transform: scale(1.1) rotate(0deg);   /* Pico en 1.1 (rebote) */
    }
    100% {
        transform: scale(1) rotate(0deg);     /* Final en 1 (normal) */
        opacity: 1;
    }
}
```

**Ejemplos:**
- Sin rebote: `scale(0.3)` → `scale(1)` → `scale(1)`
- Rebote pequeño: `scale(0.3)` → `scale(1.05)` → `scale(1)`
- Rebote grande: `scale(0.3)` → `scale(1.2)` → `scale(1)`

---

### 8️⃣ CAMBIAR EL EASING (Suavidad de movimiento)

Busca los valores `cubic-bezier`:

```css
.curtain-left {
    animation: openCurtainLeft 1.5s cubic-bezier(0.25, 0.46, 0.45, 0.94) forwards;
    /* ↑ Cambiar este valor */
}
```

**Valores preestablecidos:**
- **Suave natural**: `cubic-bezier(0.25, 0.46, 0.45, 0.94)` ← Actual
- **Muy suave**: `cubic-bezier(0.1, 0.9, 0.2, 1)`
- **Rápido al inicio**: `cubic-bezier(0.42, 0, 1, 1)`
- **Lento al inicio**: `cubic-bezier(0, 0, 0.58, 1)`
- **Con rebote**: `cubic-bezier(0.34, 1.56, 0.64, 1)` ← Logo

O usa las palabras clave simples:
- `ease` - Suave por defecto
- `ease-in` - Acelera
- `ease-out` - Desacelera
- `ease-in-out` - Suave ambos lados
- `linear` - Velocidad constante

---

### 9️⃣ CAMBIAR EL TIEMPO DE DESAPARICIÓN

En la función JavaScript, busca:

```javascript
function initOpeningAnimation() {
    // ... código ...
    
    // Esperamos 1.8s y luego escondemos el overlay
    setTimeout(() => {
        openingOverlay.style.pointerEvents = 'auto';
        openingOverlay.style.opacity = '0';
        openingOverlay.style.transition = 'opacity 0.3s ease-out';
    }, 1800);  // ← CAMBIAR AQUÍ (en milisegundos)
    
    // Removemos del DOM después de 2.2s
    setTimeout(() => {
        if (openingOverlay.parentNode) {
            openingOverlay.parentNode.removeChild(openingOverlay);
        }
    }, 2200);  // ← O AQUÍ
}
```

**Ejemplos:**
- Desaparición rápida: `1200` y `1600`
- Desaparición lenta: `2500` y `3000`
- Desaparición media: `1800` y `2200` ← Actual

---

### 🔟 CAMBIAR PADDING Y BORDER DEL LOGO

Busca:

```css
.logo-reveal img {
    padding: 20px;          /* CAMBIAR AQUÍ */
    border-radius: 20px;    /* O AQUÍ (esquinas) */
}
```

**Ejemplos:**
- Sin padding: `padding: 0px;`
- Padding pequeño: `padding: 10px;`
- Padding grande: `padding: 30px;`
- Esquinas redondeadas muy suaves: `border-radius: 10px;`
- Esquinas más redondeadas: `border-radius: 30px;`
- Completamente redondeado: `border-radius: 50%;`

---

## 🎨 PALETA DE COLORES SUGERIDA

### Colores Cálidos (como actual)
```css
/* Naranja */
#FF6B35 → #FF8C42 ← ACTUAL

/* Rojo-Naranja */
#E63946 → #F77F00

/* Dorado */
#D4A373 → #FFC371
```

### Colores Fríos
```css
/* Azul */
#0066FF → #0080FF

/* Verde */
#00AA44 → #00CC55

/* Púrpura */
#8B5CF6 → #A78BFA
```

### Colores Profesionales
```css
/* Negro y Gris */
#1F2937 → #374151

/* Verde oscuro */
#1B4332 → #2D6A4F

/* Azul oscuro */
#0F3460 → #16213E
```

---

## 📊 PRESETS PARA COPIAR Y PEGAR

### Preset 1: Animación Muy Rápida
```css
.curtain-left, .curtain-right {
    animation: ... 0.8s ...
}
.logo-reveal {
    animation: ... 0.8s ...
}
.page-content {
    animation: ... 0.5s ease-in 0.3s ...
}
.page-content .container {
    animation: ... 0.5s ease-out 0.4s ...
}
```

### Preset 2: Animación Lenta y Elegante
```css
.curtain-left, .curtain-right {
    animation: ... 2s ...
}
.logo-reveal {
    animation: ... 2s ...
}
.page-content {
    animation: ... 1.2s ease-in 1s ...
}
.page-content .container {
    animation: ... 1s ease-out 1.1s ...
}
```

### Preset 3: Colores Azules
```css
.curtain-left {
    background: linear-gradient(to right, #0066FF, #0080FF);
}
.curtain-right {
    background: linear-gradient(to left, #0066FF, #0080FF);
}
.logo-reveal img {
    filter: drop-shadow(0 15px 40px rgba(0, 102, 255, 0.4));
}
```

---

## ✅ TIPS PROFESIONALES

1. **Menos es más** - Mantén los cambios sutiles
2. **Prueba en vivo** - Abre index.html después de cambiar
3. **Sé consistente** - Usa los mismos colores de tu marca
4. **Copia/pega cuidadoso** - Verifica la sintaxis
5. **Ten backup** - Copia el archivo antes de modificar

---

## 🔧 HERRAMIENTAS ÚTILES

- **ColorPicker**: Busca "Color Picker Online" para obtener códigos HEX
- **Cubic-bezier Generator**: Busca "Cubic Bezier Generator" para crear easing personalizado
- **DevTools del navegador**: F12 para inspeccionar y ver cambios en tiempo real

---

**¡Personaliza tu animación a tu gusto! 🎨✨**
