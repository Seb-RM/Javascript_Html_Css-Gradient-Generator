# 🌈 Gradient Generator

¡Bienvenido al **Gradient Generator**! 🎨  
Esta aplicación te permite crear gradientes de colores personalizados con dos colores y diferentes direcciones. Además, genera automáticamente el código CSS necesario para que puedas utilizarlo en tus proyectos. ¡Perfecto para diseñadores y desarrolladores que buscan inspiración o una herramienta rápida para generar fondos atractivos!

---

## 🚀 Características

- **Selección de colores**: Elige dos colores para crear tu gradiente.
- **Direcciones personalizables**: Cambia la dirección del gradiente con botones intuitivos.
- **Código CSS generado automáticamente**: Obtén el código CSS listo para copiar y pegar.
- **Interfaz amigable**: Diseño simple y fácil de usar.
- **Animaciones suaves**: Transiciones y efectos visuales agradables.

---

## 🛠️ Funcionamiento

### 1. Selección de colores 🎨
La aplicación utiliza dos inputs de tipo `color` para que elijas los colores que formarán el gradiente. Estos inputs están representados por los elementos:

```html
<input type="color" id="color-a" value="#ff69b4">
<input type="color" id="color-b" value="#4a6ee0">
```

### 2. Dirección del gradiente 🧭
Puedes seleccionar la dirección del gradiente utilizando los botones con íconos de flechas. Cada botón llama a la función setDirection para actualizar la dirección y resaltar el botón activo.

```javascript
function setDirection(value, _this) {
    let directions = document.querySelectorAll(".buttons button");
    for (let i of directions) {
        i.classList.remove("active");
    }
    _this.classList.add("active");
    currentDirection = value;
}
```

- value: Define la dirección del gradiente (por ejemplo, to top, to right, etc.).

- _this: Hace referencia al botón clickeado, permitiendo agregar la clase active para resaltarlo.

### 3. Generación del gradiente 🌈
Al hacer clic en el botón "Generate Gradient", se ejecuta la función generateGradient. Esta función actualiza el fondo de la página y genera el código CSS correspondiente.

```javascript
function generateGradient() {
    outputCode.value = `background: linear-gradient(${currentDirection}, ${colorOne.value}, ${colorTwo.value});`;
    document.getElementsByTagName("BODY")[0].style.background = `linear-gradient(${currentDirection}, ${colorOne.value}, ${colorTwo.value})`;
}
```

- outputCode.value: Muestra el código CSS en el área de texto.

- document.getElementsByTagName('BODY')[0].style.background: Aplica el gradiente al fondo de la página.

### 4. Copiar el código CSS 📋
El botón "Copy" permite copiar el código CSS generado al portapapeles usando la API navigator.clipboard.

```javascript
function copyCode() {
    navigator.clipboard.writeText(outputCode.value).then(() => {
        alert("Gradient copied to clipboard");
    });
}
```

---

## 🖥️ Tecnologías utilizadas
- HTML: Estructura de la aplicación.

- CSS: Estilos y animaciones.

- JavaScript: Funcionalidad dinámica y manipulación del DOM.

- Font Awesome: Íconos para los botones de dirección.

---

## 🎨 Estilos y Animaciones
La aplicación cuenta con un diseño moderno y animaciones suaves para mejorar la experiencia del usuario:

- @keyframes slide-in: Animación de entrada del contenedor principal.

- Hover effects: Cambios de color en los botones al pasar el mouse.

- Rotación de íconos: Los íconos de las direcciones diagonales están rotados 45 grados.

```css
.rotate-icon i {
    transform: rotate(45deg);
}
```

---

## 🚀 Cómo usar
1. Selecciona dos colores utilizando los inputs de tipo color.

2. Elige la dirección del gradiente haciendo clic en los botones de flechas.

3. Haz clic en "Generate Gradient" para ver el resultado y generar el código CSS.

4. Copia el código CSS con el botón "Copy" y úsalo en tus proyectos.

---
## 📂 Estructura del proyecto

```
gradient-generator/
├── index.html          # Archivo principal HTML
├── style.css           # Estilos CSS
├── script.js           # Lógica de JavaScript
```