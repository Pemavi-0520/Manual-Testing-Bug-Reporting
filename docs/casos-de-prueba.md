# Casos de Prueba

Datos válidos conocidos del sitio (Form Authentication):
- Usuario válido: `tomsmith`
- Contraseña válida: `SuperSecretPassword!`

---

## Módulo: Form Authentication (`/login`)
**Técnica: Clases de Equivalencia**

Clases identificadas:
- Usuario válido / inválido / vacío
- Contraseña válida / inválida / vacía

| ID | Clase de equivalencia | Precondición | Pasos | Resultado esperado | Resultado obtenido | No. de Bug | Prioridad |
|---|---|---|---|---|---|---|---|
| TC-001 | Usuario válido + contraseña válida (clase válida) | Estar en `/login` | 1. Ingresar `tomsmith` en usuario<br>2. Ingresar `SuperSecretPassword!` en contraseña<br>3. Clic en Login | Acceso concedido, redirección a `/secure` con mensaje de éxito | Acceso concedido, redirección a `/secure` con mensaje de éxito | N/A | Alta
| TC-002 | Usuario inválido + contraseña válida (clase inválida) | Estar en `/login` | 1. Ingresar `usuarioFalso`<br>2. Ingresar `SuperSecretPassword!`<br>3. Clic en Login | Acceso denegado, mensaje de error visible | Acceso denegado, mensaje de error visible | N/A | Alta |
| TC-003 | Usuario válido + contraseña inválida (clase inválida) | Estar en `/login` | 1. Ingresar `tomsmith`<br>2. Ingresar `contraseñaIncorrecta`<br>3. Clic en Login | Acceso denegado, mensaje de error visible | Acceso denegado, mensaje de error visible | N/A | Alta |
| TC-004 | Usuario y contraseña vacíos (clase vacía) | Estar en `/login` | 1. Dejar ambos campos vacíos<br>2. Clic en Login | Mensaje de validación indicando campos requeridos | Acceso denegado, mensaje de error visible | BUG-001 | Alta |
| TC-005 | Usuario vacío + contraseña válida | Estar en `/login` | 1. Dejar usuario vacío<br>2. Ingresar `SuperSecretPassword!`<br>3. Clic en Login | Acceso denegado, mensaje de error específico | Acceso denegado, mensaje de error específico | N/A | Media |
| TC-006 | Sensibilidad a mayúsculas/minúsculas | Estar en `/login` | 1. Ingresar `TomSmith` (mayúsculas alteradas)<br>2. Ingresar contraseña válida<br>3. Clic en Login | Comportamiento consistente y documentado (aceptar o rechazar según diseño) | Sensible a mayúsculas/minúsculas | N/A | Media
| TC-007 | Inyección básica en campo usuario (caso negativo) | Estar en `/login` | 1. Ingresar `' OR '1'='1` en usuario<br>2. Ingresar cualquier contraseña<br>3. Clic en Login | Acceso denegado, sin comportamiento anómalo | Acceso denegado, sin comportamiento anómalo | N/A | Alta |


---

## Módulo: Inputs (`/inputs`)
**Técnica: Análisis de Valores Límite**

Campo bajo prueba: input numérico (`type="number"`)

| ID | Valor límite probado | Precondición | Pasos | Resultado esperado | Resultado obtenido | No. de Bug | Prioridad |
|---|---|---|---|---|---|---|---|
| TC-008 | Valor mínimo típico (0) | Estar en `/inputs` | 1. Ingresar `0` en el campo | El campo acepta el valor sin error | El campo acepta el valor sin error | N/A | Media |
| TC-009 | Valor negativo | Estar en `/inputs` | 1. Ingresar `-1` | El campo acepta el valor | El campo acepta el valor | N/A | Media |
| TC-010 | Valor positivo grande (límite superior razonable) | Estar en `/inputs` | 1. Ingresar `999999999` | El campo acepta o trunca según comportamiento del navegador | El campo acepta y permite seguir aumentando el número | BUG-002 | Media |
| TC-011 | Valor decimal | Estar en `/inputs` | 1. Ingresar `3.14` | El campo acepta el decimal correctamente | El campo acepta el decimal correctamente | N/A | Media |
| TC-012 | Entrada no numérica | Estar en `/inputs` | 1. Intentar ingresar `abc` | El campo rechaza o no permite la entrada de letras | El campo rechaza o no permite la entrada de letras | N/A | Alta |
| TC-013 | Campo vacío al enviar/perder foco | Estar en `/inputs` | 1. Dejar el campo vacío<br>2. Hacer clic fuera del campo | No hay error inesperado; comportamiento consistente con un campo opcional/requerido | No hay error inesperado; comportamiento consistente con un campo opcional/requerido | N/A | Baja |
| TC-014 | Notación científica | Estar en `/inputs` | 1. Ingresar `1e5` | Documentar si el campo lo interpreta como 100000 o lo rechaza | Aumentar o reducir el numero cambia a 100001 o 99999 | N/A | Baja |
| TC-015 | Incremento con flechas del input | Estar en `/inputs` | 1. Ingresar `5`<br>2. Usar la flecha ↑ del campo | El valor incrementa en 1 (a 6) | El valor incrementa en 1 (a 6) | N/A | Media |

---

## Módulo: JavaScript Alerts (`/javascript_alerts`)
**Técnica: Pruebas funcionales / transición de estados (cubriendo aceptar y cancelar en cada tipo de diálogo)**
 
| ID | Escenario | Precondición | Pasos | Resultado esperado | Resultado obtenido | No. de Bug | Prioridad |
|---|---|---|---|---|---|---|---|
| TC-016 | JS Alert - aceptar | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Alert"<br>2. Clic en OK del diálogo | El diálogo se cierra y el texto de resultado muestra "You successfully clicked an alert" | El diálogo se cierra y el texto de resultado muestra "You successfully clicked an alert" | N/A | Alta |
| TC-017 | JS Confirm - aceptar | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Confirm"<br>2. Clic en OK | El texto de resultado muestra "You clicked: Ok" | El texto de resultado muestra "You clicked: Ok" | N/A | Alta |
| TC-018 | JS Confirm - cancelar | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Confirm"<br>2. Clic en Cancelar | El texto de resultado muestra "You clicked: Cancel" | El texto de resultado muestra "You clicked: Cancel" | N/A | Alta |
| TC-019 | JS Prompt - aceptar con texto | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Prompt"<br>2. Escribir `Test` en el campo<br>3. Clic en OK | El texto de resultado muestra "You entered: Test" | El texto de resultado muestra "You entered: Test" | N/A | Alta |
| TC-020 | JS Prompt - aceptar con campo vacío | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Prompt"<br>2. Dejar el campo vacío<br>3. Clic en OK | El texto de resultado muestra "You entered:" ` ` | El texto de resultado muestra "You entered:" ` ` | N/A | Media |
| TC-021 | JS Prompt - cancelar | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Prompt"<br>2. Clic en Cancelar (sin escribir nada) | El texto de resultado muestra "You entered: null" | El texto de resultado muestra "You entered: null" | N/A | Alta |
| TC-022 | JS Prompt - caracteres especiales | Estar en `/javascript_alerts` | 1. Clic en "Click for JS Prompt"<br>2. Escribir `<script>alert(1)</script>`<br>3. Clic en OK | El texto se muestra literal como string, sin ejecutarse ni romper la página | No se muestra ningun texto aparte del mensaje "You entered:", además que se crea una nueva etiqueta en código HTML | BUG-003 |Media |
| TC-023 | Bloqueo de interacción con la página | Estar en `/javascript_alerts` | 1. Clic en cualquiera de los 3 botones<br>2. Intentar interactuar con otro elemento de la página sin cerrar el diálogo | No es posible interactuar con el resto de la página hasta cerrar el diálogo (comportamiento nativo del navegador) | No es posible interactuar con el resto de la página hasta cerrar el diálogo (comportamiento nativo del navegador) | N/A | Baja |
 
---
 
## Módulo: Dynamic Loading (`/dynamic_loading`)
**Técnica: Pruebas de sincronización / basadas en estado**
 
### Example 1 (elemento oculto, ya existe en el DOM)
| ID | Escenario | Precondición | Pasos | Resultado esperado | Resultado obtenido | No. de Bug | Prioridad |
|---|---|---|---|---|---|---|---|
| TC-024 | Elemento oculto antes de cargar | Estar en `/dynamic_loading/1` | 1. Inspeccionar la página antes de hacer clic en Start | El texto "Hello World!" no es visible en pantalla | El texto "Hello World!" no es visible en pantalla | N/A | Media |
| TC-025 | Carga exitosa | Estar en `/dynamic_loading/1` | 1. Clic en "Start"<br>2. Esperar a que la barra de progreso termine | El texto "Hello World!" se vuelve visible al terminar la carga | El texto "Hello World!" se vuelve visible al terminar la carga | N/A | Alta |
| TC-026 | Múltiples clics en Start durante la carga | Estar en `/dynamic_loading/1` | 1. Clic en "Start"<br>2. Clic en "Start" nuevamente antes de que termine la barra | No se generan barras de progreso duplicadas ni estados inconsistentes | No se generan barras de progreso duplicadas ni estados inconsistentes | N/A | Baja |
 
### Example 2 (elemento no existe hasta que termina la carga)
| ID | Escenario | Precondición | Pasos | Resultado esperado | Resultado obtenido | No. de Bug | Prioridad |
|---|---|---|---|---|---|---|---|
| TC-027 | Elemento ausente del DOM antes de cargar | Estar en `/dynamic_loading/2` | 1. Inspeccionar el HTML antes de hacer clic en Start | El elemento con el texto "Hello World!" no existe todavía en el DOM (no solo oculto) | El elemento con el texto "Hello World!" no existe todavía en el DOM (no solo oculto) | N/A | Alta |
| TC-028 | Carga exitosa | Estar en `/dynamic_loading/2` | 1. Clic en "Start"<br>2. Esperar a que la barra de progreso termine | El elemento "Hello World!" se agrega al DOM y se muestra correctamente | El elemento "Hello World!" se agrega al DOM y se muestra correctamente | N/A | Alta |
| TC-029 | Comparación de comportamiento vs Example 1 | Haber ejecutado TC-024 y TC-027 | 1. Documentar la diferencia observada entre ambos ejemplos | Queda documentado que Example 1 = elemento oculto (CSS), Example 2 = elemento inexistente (DOM) — relevante para diseño de esperas en automatización | Queda confirmado que Example = 1 tiene un elemento oculto, mientras que Example = 2 crea un elemento nuevo | N/A | Baja |
 
