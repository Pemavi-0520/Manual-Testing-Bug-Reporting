# Plan de Pruebas — the-internet.herokuapp.com

## 1. Introducción

Este documento define el alcance, estrategia y criterios para las pruebas funcionales manuales realizadas sobre el sitio `the-internet.herokuapp.com`, como parte de un proyecto de portafolio QA.

## 2. Alcance

### Módulos incluidos
| Módulo | URL | Técnica principal |
|---|---|---|
| Form Authentication | `/login` | Clases de equivalencia |
| Inputs | `/inputs` | Valores límite |
| JavaScript Alerts | `/javascript_alerts` | Pruebas funcionales exploratorias |
| Dynamic Loading | `/dynamic_loading` | Pruebas funcionales / sincronización |

### Fuera de alcance
- Pruebas de carga o rendimiento
- Pruebas de seguridad exhaustivas (aunque se incluyen casos negativos básicos)
- Módulos del sitio no listados arriba

## 3. Estrategia de pruebas

- **Tipo:** Pruebas funcionales manuales, caja negra
- **Técnicas de diseño:**
  - Clases de equivalencia (partición de datos válidos/inválidos)
  - Análisis de valores límite (límites superior/inferior de campos numéricos)
- **Nivel de prueba:** Sistema (UI end-to-end)
- **Enfoque:** Cada caso de prueba documenta precondición, pasos, resultado esperado y prioridad. Los defectos encontrados se documentan con plantilla estandarizada (ver `bugs/template-bug-report.md`).

## 4. Criterios de entrada

- Sitio bajo prueba accesible públicamente
- Casos de prueba diseñados y revisados (este documento + `casos-de-prueba.md`)
- Ambiente de prueba definido (sección 6)

## 5. Criterios de salida

- 100% de los casos de prueba diseñados han sido ejecutados
- Todos los defectos encontrados están documentados con severidad y prioridad asignadas
- No quedan defectos críticos sin reportar

## 6. Ambiente de pruebas

| Elemento | Detalle |
|---|---|
| URL base | https://the-internet.herokuapp.com |
| Navegador | Chrome (última versión estable) |
| Sistema operativo | Windows / según ejecución |
| Herramienta de evidencia | Capturas de pantalla nativas |

## 7. Riesgos

| Riesgo | Impacto | Mitigación |
|---|---|---|
| El sitio es de terceros y puede cambiar sin aviso | Casos de prueba podrían quedar desactualizados | Revisar y actualizar casos si el sitio cambia |
| No hay lógica de negocio real (datos ficticios) | Limita pruebas de reglas de negocio complejas | Enfocar el ejercicio en técnica de diseño, no en profundidad de negocio |

## 8. Entregables

- Este plan de pruebas
- Casos de prueba documentados (`docs/casos-de-prueba.md`)
- Reportes de bugs individuales (`bugs/`)
