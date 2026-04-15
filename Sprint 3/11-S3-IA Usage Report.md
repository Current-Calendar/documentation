# ISPP – Grupo 11 - Current
## 15/04/2026
## PREPARACIÓN DEL PROYECTO FINAL (#PPL)
## INFORME DE IMPLEMENTACIÓN Y USO DE LA INTELIGENCIA ARTIFICIAL

| Versión | Fecha | Descripción |
| :--- | :--- | :--- |
| 1.0 | 15/04/2026 | Versión inicial del documento |

---

### 1. Introducción
El presente documento describe la utilización de herramientas de **Inteligencia Artificial generativa** como soporte al trabajo realizado a lo largo del desarrollo del proyecto **Current Calendar**, una aplicación de calendario colaborativo con backend en Django y frontend en React Native / Expo. Su empleo ha estado orientado a reforzar el desarrollo técnico, facilitar la resolución de incidencias y mejorar la calidad del software implementado, manteniendo siempre al equipo como responsable de la validación, adaptación y decisión final.

La IA se ha utilizado principalmente como asistente de apoyo en tareas de programación, revisión de código, testing, búsqueda de información técnica y análisis de posibles problemas de consistencia o seguridad. En todo momento, la IA se ha concebido como una herramienta complementaria que potencia la productividad sin sustituir el criterio profesional del equipo.

---

### 2. Metodología de uso

Durante el desarrollo del proyecto se ha mantenido un **modelo colaborativo humano-IA**, en el que las herramientas empleadas (Claude de Anthropic, a través de Claude Code) han servido como apoyo técnico para agilizar tareas de desarrollo y revisión. La dinámica de trabajo seguida se ha basado en un proceso iterativo de tres fases:

1. **Planteamiento del contexto:** Se proporciona a la IA el fragmento de código, la funcionalidad o el problema concreto sobre el que se quiere trabajar.  
2. **Generación de apoyo técnico:** La IA propone código, revisiones, explicaciones, análisis de consistencia o posibles mejoras.  
3. **Evaluación e integración:** El equipo revisa críticamente las respuestas, adapta las propuestas al contexto real del proyecto y valida manualmente la solución definitiva.

Este enfoque ha permitido aprovechar la IA tanto para acelerar la implementación como para reforzar tareas de comprobación y análisis técnico, manteniendo en todo momento el control humano sobre el resultado final. Ningún fragmento de código sugerido por la IA se ha incorporado sin que el desarrollador responsable comprendiera completamente su funcionamiento y sus implicaciones.

---

### 3. Áreas de aplicación y casos de uso

#### 3.1 Desarrollo técnico y optimización del código
La IA se ha utilizado como apoyo en la construcción de nuevas funcionalidades y en la resolución de dudas surgidas durante la implementación.

* **Aplicación:** Generación de fragmentos de código, propuesta de estructuras de implementación, refactorización y optimización de endpoints y consultas a base de datos, y apoyo en el desarrollo de funcionalidades como etiquetas, analíticas de negocio, notificaciones, suscripciones, anuncios y gestión de privacidad/cookies.
* **Resultado:** Se ha conseguido agilizar el desarrollo, reducir el tiempo de bloqueo ante problemas concretos y disponer de propuestas iniciales que posteriormente fueron revisadas y ajustadas por el equipo.

#### 3.2 Testing y calidad del software
La IA se ha empleado como apoyo significativo en la mejora de la cobertura y calidad de los tests del proyecto.

* **Aplicación:** Generación y mejora de tests unitarios para los distintos módulos del backend (calendarios, eventos, etiquetas, invitaciones, notificaciones, reportes, etc.), apoyo en la configuración de tests end-to-end con Selenium y Docker, y análisis de cobertura de código.
* **Resultado:** Se logró aumentar la cobertura de tests del proyecto del 85% al 91%, reforzando la fiabilidad del software y facilitando la detección temprana de errores.

#### 3.3 Búsqueda de información y soporte técnico
Otra de las utilidades principales ha sido el uso de la IA como herramienta de consulta para obtener información relevante durante el desarrollo.

* **Aplicación:** Búsqueda de información técnica, aclaración de conceptos, consulta de buenas prácticas, diagnóstico y corrección de problemas de compatibilidad Android/iOS (AsyncStorage vs localStorage, estilos, modales) y resolución de conflictos de migraciones en Django.
* **Resultado:** Se ha facilitado la toma de decisiones técnicas y se ha reducido el tiempo invertido en localizar información de apoyo, especialmente en problemas de compatibilidad entre plataformas.

#### 3.4 Revisión de código, validaciones y seguridad
La IA también se ha empleado para realizar una revisión del código desde una perspectiva analítica, con el objetivo de detectar inconsistencias, vulnerabilidades o aspectos mejorables.

* **Aplicación:** Análisis de seguridad en autenticación y permisos de calendario, protección de acciones sin login, eliminación de búsqueda por email, y validación del cumplimiento de buenas prácticas en la estructura del proyecto.
* **Resultado:** Se ha reforzado la robustez de la implementación al disponer de una segunda capa de revisión enfocada a la calidad y seguridad del código, detectando puntos de mejora antes de la integración.

#### 3.5 Documentación
La IA se ha utilizado como apoyo para la generación y revisión de documentación técnica del proyecto.

* **Aplicación:** Apoyo en la redacción de documentación técnica (README, documentación de APIs), generación de informes de cobertura y análisis de calidad, y configuración de entornos de desarrollo y despliegue (Docker, CI/CD).
* **Resultado:** Se ha mejorado la calidad y exhaustividad de la documentación del proyecto, facilitando la comprensión y mantenibilidad del sistema.

---

### 4. Análisis de impacto
El uso de IA durante el desarrollo del proyecto ha tenido un impacto positivo en varios aspectos:

* **Mayor eficiencia en la implementación:** La posibilidad de obtener propuestas de código y explicaciones técnicas ha permitido avanzar con mayor rapidez en determinadas tareas.  
* **Mejora de la calidad del software:** El análisis de consistencia, la revisión de validaciones y el aumento de la cobertura de tests han ayudado a detectar y prevenir problemas potenciales.  
* **Reducción del tiempo de consulta:** La IA ha servido como apoyo inmediato para resolver dudas técnicas y localizar información útil de forma más ágil, especialmente en temas de compatibilidad multiplataforma.  
* **Refuerzo del criterio técnico del equipo:** Las respuestas generadas por la IA han servido como punto de partida o contraste, pero siempre han sido sometidas a revisión y ajuste por parte del grupo.

En conjunto, la IA ha contribuido a mejorar la productividad y a reforzar la calidad de las soluciones implementadas, permitiendo al equipo centrarse en los aspectos más creativos y de mayor valor añadido del desarrollo.

---

### 5. Supervisión y validación
A pesar del apoyo proporcionado por la Inteligencia Artificial, todas las aportaciones generadas han sido revisadas y validadas por el equipo antes de su incorporación al proyecto.

* **Validación técnica:** Se comprobaron manualmente las propuestas de implementación, asegurando su coherencia con la arquitectura y con los requisitos del proyecto.  
* **Revisión de seguridad y robustez:** Las observaciones sobre validaciones o vulnerabilidades potenciales fueron analizadas críticamente antes de aplicar cualquier cambio.  
* **Adaptación al contexto real:** Las soluciones generadas se ajustaron al estado actual del código y a las necesidades específicas del proyecto.  
* **Control humano del resultado final:** La decisión de aceptar, modificar o descartar cualquier propuesta correspondió siempre al equipo.
* **Control de versiones:** Todo el trabajo se ha gestionado a través de Git con ramas de feature, revisiones de código y pull requests (+410 PRs revisadas y mergeadas), garantizando la trazabilidad completa del desarrollo.

Este proceso de supervisión ha sido esencial para garantizar que la IA funcionara como herramienta de apoyo útil, sin comprometer la calidad ni la adecuación de los entregables.

---

### 6. Conclusiones
A lo largo del desarrollo del proyecto Current Calendar, la Inteligencia Artificial se ha consolidado como un recurso de apoyo valioso para el equipo, especialmente en tareas de desarrollo, testing, revisión técnica y consulta de información. Su uso ha permitido acelerar ciertas actividades, detectar posibles inconsistencias, aumentar la cobertura de tests y reforzar la calidad general del trabajo realizado.

El grueso del trabajo ha sido realizado directamente por el equipo de desarrollo, con más de 960 commits y 410 pull requests, incluyendo el diseño completo de la arquitectura, la implementación de funcionalidades complejas (calendarios compartidos, eventos, invitaciones, suscripciones con pasarela de pago, notificaciones en tiempo real, analíticas de negocio, entre otras) y la configuración de la infraestructura de despliegue.

No obstante, el valor real de esta herramienta ha dependido del uso crítico y supervisado por parte del equipo, que ha actuado en todo momento como responsable de interpretar, validar y adaptar las propuestas generadas. De este modo, la IA ha contribuido de forma efectiva al avance del proyecto, manteniendo siempre el control y la responsabilidad en manos del grupo.
