
# 🍏 Localización de Elementos iOS en Appium

## Orden jerárquico recomendado para localizar elementos

1. **Accessibility ID**
2. **Predicate String**
3. **Class Chain**
4. **ID (name)**
5. **Class Name**
6. **XPath**

---

## Definición y Recomendaciones

### 1. **Accessibility ID**
- **Descripción**: Usa el atributo `accessibilityIdentifier` o `accessibilityLabel` de iOS.
- **Ventajas**:
  - Rápido, confiable y reutilizable entre Android/iOS.
  - Muy usado en apps bien diseñadas con accesibilidad en mente.
- **Recomendación**:
  - Primera opción siempre que esté disponible.

---

### 2. **Predicate String**
- **Descripción**: Usa una sintaxis similar a consultas SQL para filtrar elementos (por nombre, etiqueta, valor, etc.).
- **Ventajas**:
  - Potente para búsquedas con condiciones.
  - Mejor rendimiento que XPath.
- **Recomendación**:
  - Úsalo cuando no haya `accessibilityId`.


## iOS Predicate String (Ejemplos)

### 1. Buscar botón por nombre exacto
```
name == "Aceptar"
```
Localiza el botón con name “Aceptar”.

### 2. Buscar texto que comience con cierta palabra
```
label BEGINSWITH "Hola"
```
Muy útil para texto dinámico o encabezados.

### 3. Buscar campo visible con contenido específico
```
type == "XCUIElementTypeTextField" AND value CONTAINS "correo"
```
Busca un campo de texto que contenga la palabra "correo".

### 4. Buscar botón con accesibilidad y visibilidad
```
name == "Enviar" AND visible == 1
```
Evita errores cuando elementos están ocultos.

### 5. Buscar elementos con nombre parcial, sin importar mayúsculas
```
name CONTAINS[c] "usuario"
```
`[c]` ignora mayúsculas y minúsculas. Muy útil para validaciones flexibles.


---

### 3.  **Class Chain**
- **Descripción**: Cadena jerárquica de clases para buscar elementos. Una forma de navegar la jerarquía de elementos por su clase, como si fueran carpetas anidadas.
- **Ventajas**:
  - Más rápido que XPath.
  - Mejor estructura que usar clases sueltas.
- **Recomendación**:
  - Útil cuando necesitas navegar jerarquías sin usar XPath.


## Localizadores en iOS – Ejemplos comunes

### iOS Class Chain (Ejemplos)

### 1. Buscar un botón dentro de cualquier vista
```
**/XCUIElementTypeButton
```
Devuelve todos los botones en la pantalla.

### 2. Buscar el primer botón dentro de una celda
```
**/XCUIElementTypeCell/XCUIElementTypeButton[1]
```
Selecciona el primer botón dentro de cada celda.

### 3. Buscar un texto dentro de una tabla
```
**/XCUIElementTypeTable/XCUIElementTypeStaticText
```
Encuentra todos los textos visibles dentro de una tabla.

### 4. Buscar una celda específica por su nombre
```
**/XCUIElementTypeCell[`name == "Perfil"`]
```
Ubica la celda que tiene como nombre “Perfil”.

### 5. Buscar un campo de texto dentro de una alerta
```
**/XCUIElementTypeAlert/XCUIElementTypeTextField
```
Usado para interactuar con inputs dentro de diálogos.

---

### 4. **ID (name)**
- **Descripción**: Usa el nombre del elemento, que normalmente es el mismo que `accessibilityLabel`.
- **Desventajas**:
  - Puede no ser único o no estar configurado correctamente.
- **Recomendación**:
  - Solo si no hay `accessibilityId` ni predicados.

---

### 5.  **Class Name**
- **Descripción**: Busca por tipo de clase (`XCUIElementTypeButton`, `XCUIElementTypeTextField`, etc.).
- **Desventajas**:
  - Muy genérico y poco confiable solo.
- **Recomendación**:
  - Combinar con filtros adicionales si se usa.

---

### 6. ⚠️ **XPath**
- **Descripción**: Rutas similares a XML para buscar elementos.
- **Desventajas**:
  - Muy lento.
  - Frágil ante cambios de UI.
- **Recomendación**:
  - Evitarlo si es posible.

---

## 🏁 Resumen en Tabla

| Prioridad | Estrategia        | ¿Cuándo usarla?                                  |
|-----------|-------------------|--------------------------------------------------|
| 1         | `accessibilityId` | Siempre que esté disponible                      |
| 2         | `predicate`       | Cuando necesitas condiciones lógicas             |
| 3         | `class chain`     | Para navegación jerárquica sin XPath             |
| 4         | `name`            | Si no hay accessibilidad configurada             |
| 5         | `className`       | En combinación con otros filtros                 |
| 6         | `xpath`           | Último recurso                                   |
