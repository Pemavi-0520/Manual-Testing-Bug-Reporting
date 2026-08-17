# Manual Testing & Bug Reporting — Portafolio QA

## Objetivo

Proyecto de práctica de QA manual sobre [the-internet.herokuapp.com](https://the-internet.herokuapp.com), un sitio diseñado específicamente para pruebas funcionales, con el fin de demostrar diseño de casos de prueba estructurado y documentación profesional de defectos.

Este es el **primer proyecto de una serie progresiva** de portafolio QA:

1. **Manual Testing + Bug Reporting** ← este repo
2. API Testing (Postman)
3. Validación de datos con SQL
4. Automatización Web (Selenium)
5. Testing Mobile

## Técnicas aplicadas

- **Clases de equivalencia (Equivalence Partitioning)** — módulo Form Authentication
- **Análisis de valores límite (Boundary Value Analysis)** — módulo Inputs
- Pruebas exploratorias complementarias

## Estructura del repositorio

```
manual-testing-qa-portfolio/
├── README.md
├── docs/
│   ├── plan-de-pruebas.md      # Alcance, estrategia, criterios de entrada/salida
│   └── casos-de-prueba.md      # Casos de prueba diseñados con técnicas formales
├── bugs/
│   └── template-bug-report.md  # Plantilla estilo Jira para reportes de defectos
└── evidencias/                 # Capturas de pantalla como evidencia (a agregar)
```

## Cómo usar este repo

1. Revisa `docs/plan-de-pruebas.md` para entender el alcance y estrategia
2. Ejecuta los casos listados en `docs/casos-de-prueba.md` contra el sitio en vivo
3. Por cada defecto encontrado, copia `bugs/template-bug-report.md` y llénalo (ej. `bugs/BUG-001.md`)
4. Guarda capturas de pantalla en `evidencias/` y referencia el archivo en el reporte

## Herramientas

- Sitio bajo prueba: the-internet.herokuapp.com
- Documentación: Markdown / GitHub
- (Próximo proyecto) Gestión de defectos: Jira

## Contacto

Mario Victorio — QA / Systems Engineer Jr. / mae.vic@outlook.com
