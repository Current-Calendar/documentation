# ISPP – Grupo 11 - Current
## 29/04/2026
## Preparing Project Launch (#PPL)
## INFORME DE IMPLEMENTACIÓN Y USO DE LA INTELIGENCIA ARTIFICIAL

| Versión | Fecha | Descripción |
| :--- | :--- | :--- |
| 1.0 | 18/05/2026 | Versión inicial del documento. |

---

### 1. Introducción

El presente documento describe cómo el equipo de **Current Calendar** ha utilizado herramientas de **Inteligencia Artificial generativa** durante el proyecto, con especial foco en la preparación de la entrega final. Current Calendar es una aplicación full-stack de calendario social y colaborativo, con backend en **Django 5.2 + Django REST Framework**, frontend en **React Native / Expo**, base de datos **PostgreSQL + PostGIS**, caché y pub/sub con **Redis**, integración de **Google Calendar / ICS**, notificaciones, radar geolocalizado, recomendaciones, suscripciones, analíticas, reportes y documentación de despliegue.

La IA se ha usado como un **asistente de apoyo** para acelerar tareas de desarrollo, depuración, revisión, testing, documentación y coordinación. En ningún caso se ha considerado como sustituto del criterio del equipo: las propuestas generadas por IA han sido revisadas, adaptadas al contexto real del repositorio, validadas con pruebas y finalmente aceptadas o descartadas por las personas responsables de cada tarea.

Este informe proporciona una descripción detallada de:

- Herramientas y modelos utilizados.
- Evidencias encontradas en el repositorio y en el tablero de GitHub Projects.
- Prompts representativos usados para distintas tareas.
- Resultados obtenidos y forma de validación.
- Limitaciones, riesgos y aprendizajes para próximos sprints.

---

### 2. Alcance y evidencias analizadas

Para elaborar este informe se ha revisado el repositorio `Current-Calendar/app`, la documentación del proyecto y el tablero público de GitHub Projects. Las evidencias principales son:

- **Repositorio local y remoto:** `https://github.com/Current-Calendar/app`.
- **GitHub Project:** `https://github.com/orgs/Current-Calendar/projects/1/views/1`.
- **Workflow de resumen automático de PRs:** `.github/workflows/PR_summarizer.yml`.
- **Workflow de CI y calidad:** `.github/workflows/CI_test.yml`.
- **CSV de mejora de cobertura:** `cobertura_mejoras.csv`.
- **Documentación funcional y técnica:** `README.md`, `docs/`, `e2e/README.md`.
- **Configuración local de Claude Code:** `.claude/settings.local.json`.

#### 2.1 Métricas del proyecto observadas

| Métrica | Valor observado | Fuente / comentario |
| :--- | :--- | :--- |
| Commits en `main` | 972 | `git rev-list --count HEAD`. |
| Pull requests públicas | 179 | Cabecera `Link` de GitHub API para `/pulls?state=all&per_page=1`. |
| Elementos en GitHub Project | 271 | Datos embebidos en el Project público. |
| Elementos en `Done` | 234 | GitHub Project. |
| Elementos en `Todo` | 25 | GitHub Project. |
| Elementos en `In Progress` | 5 | GitHub Project. |
| Elementos en `Quality Assurance` | 1 | GitHub Project. |
| Tests backend detectados | 593 funciones `test_` | Conteo de tests en `backend/main`. |
| Tests E2E detectados | 18 funciones `test_` | Conteo de tests en `e2e/tests`. |
| Cobertura global | 85% → 91% | `cobertura_mejoras.csv`. |
| Tests nuevos asociados a mejora de cobertura | 79 | `cobertura_mejoras.csv`. |

Estas métricas no pretenden atribuir todo el trabajo a la IA. Al contrario, muestran que la IA se ha integrado dentro de un proceso amplio de ingeniería, revisión humana, CI, pruebas y control de versiones.

---

### 3. Herramientas y modelos utilizados

Durante el proyecto se han utilizado varias herramientas de IA con objetivos diferentes. Algunas están explícitamente versionadas en el repositorio; otras han sido usadas por integrantes del equipo en sus entornos locales.

| Herramienta / entorno | Modelo identificado | Uso principal | Evidencia | Observaciones |
| :--- | :--- | :--- | :--- | :--- |
| **Claude Code** | Claude de Anthropic, mediante Claude Code. El repositorio no versiona el modelo exacto de cada sesión local. | Agente de código para navegar el repositorio, proponer cambios, depurar errores, generar tests y ejecutar comandos controlados. | Carpeta `.claude/` y comentarios del equipo sobre uso de Claude Code. | Muy útil para tareas con mucho contexto de repositorio. Se recomienda registrar en futuras PRs el modelo exacto usado por cada desarrollador. |
| **Groq API compatible con OpenAI** | `llama-3.3-70b-versatile` | Resumen automático de pull requests. | `.github/workflows/PR_summarizer.yml`. | Temperatura `0.3`, orientado a análisis directo y baja creatividad. |
| **Asistentes tipo ChatGPT / OpenAI** | Modelos GPT usados de forma individual por miembros del equipo. El modelo exacto no siempre quedó registrado. | Consulta técnica, explicación de errores, apoyo a documentación, generación de prompts y revisión conceptual. | Uso declarado de IA en issues de informe; no hay trazabilidad completa por prompt. | Adecuado para consultas puntuales y redacción, pero requiere validación. |
| **OpenAI Codex / agente de análisis del repositorio** | Modelo de OpenAI usado para revisar el repositorio y preparar esta ampliación del informe. | Análisis de estructura, extracción de evidencias, redacción y organización del documento. | Esta actualización del informe. | Se ha usado con revisión humana posterior antes de entregar. |

#### 3.1 Consideración importante sobre trazabilidad

No todos los usos de IA han quedado registrados con el mismo nivel de detalle. En particular, las sesiones locales de Claude Code o ChatGPT no guardan por defecto en el repositorio el **modelo exacto**, el prompt completo ni el razonamiento seguido. Por ello, este informe distingue entre:

- **Evidencia directa:** por ejemplo, `llama-3.3-70b-versatile` en el workflow de PRs.
- **Evidencia de uso local:** por ejemplo, Claude Code en `.claude/` y en la forma de trabajo del equipo.
- **Uso declarado o inferido:** uso de asistentes conversacionales para apoyo técnico y redacción.

Como mejora de proceso, proponemos que en próximas entregas se añada a cada PR o issue una breve sección opcional:

```markdown
### Uso de IA
- Herramienta/modelo:
- Prompt resumido:
- Resultado aprovechado:
- Validación realizada:
- Cambios descartados:
```

---

### 4. Metodología de uso humano-IA

La metodología seguida ha sido un ciclo iterativo de trabajo colaborativo:

1. **Contextualización del problema.**  
   El desarrollador aporta a la IA el objetivo de la tarea, fragmentos de código, errores de consola, tests fallidos, diff de una PR o restricciones funcionales.

2. **Generación de propuesta.**  
   La IA propone un enfoque, explica el problema, sugiere código, tests, refactorizaciones o documentación.

3. **Revisión crítica.**  
   El equipo comprueba si la propuesta encaja con la arquitectura real del proyecto: modelos de Django, serializadores, permisos, servicios frontend, rutas Expo, configuración Docker y convenciones del repositorio.

4. **Adaptación manual.**  
   Las respuestas de IA se ajustan a la base de código existente. Es habitual que una propuesta inicial requiera cambios en nombres de campos, endpoints, imports, fixtures, mocks o validaciones.

5. **Validación.**  
   Se ejecutan tests unitarios, pruebas manuales, pruebas E2E cuando aplica, revisión de PR y CI con PostgreSQL/PostGIS, Redis, coverage y SonarCloud.

6. **Integración y seguimiento.**  
   Los cambios se integran mediante ramas, commits y pull requests. En tareas críticas, el equipo revisa impactos en seguridad, permisos, privacidad y experiencia de usuario.

---

### 5. Casos de uso de IA por área

#### 5.1 Desarrollo backend

La IA se ha utilizado para acelerar la implementación y revisión de lógica de backend en Django/DRF.

#### Tareas representativas

- Calendarios públicos, privados, co-owned y viewers.
- Exportación e importación ICS / Google Calendar.
- Eventos de varios días y validación de fechas.
- Likes de calendarios y eventos.
- Reportes de abuso.
- Analíticas de negocio.
- Ads y recomendaciones.
- Permisos y protección de rutas.
- Categorías, etiquetas y migraciones.

#### Prompt representativo

```text
Contexto: backend Django/DRF de Current Calendar.
Revisa esta vista y estos serializers de calendarios. Tenemos calendarios privados con viewers y co-owners.
Necesito comprobar si un usuario con permiso de lectura puede exportar el calendario a ICS sin permitirle editarlo.
Devuélveme:
1. Posibles fallos de permisos.
2. Cambios mínimos en la vista.
3. Tests unitarios que cubran owner, co-owner, viewer y usuario sin permisos.
```

#### Resultado obtenido

La IA ayudó a razonar sobre combinaciones de permisos y a plantear matrices de casos de prueba. El equipo ajustó las propuestas a las clases reales del proyecto, validó los endpoints y añadió o corrigió tests. Un ejemplo de este tipo de trabajo aparece en la línea de commits de S3 con la corrección de exportación de calendarios privados con permiso de visualización.

#### Validación

- Tests unitarios de calendarios, permisos y eventos.
- Revisión manual de los endpoints protegidos.
- CI con base de datos PostgreSQL/PostGIS y Redis.

---

#### 5.2 Desarrollo frontend en React Native / Expo

La IA se ha utilizado para resolver problemas de interfaz, navegación, modales, compatibilidad móvil/web y conexión con el backend.

#### Tareas representativas

- Pantallas de login, registro y recuperación de contraseña.
- Pantallas de creación/edición de calendarios y eventos.
- Modales de invitación, confirmación, éxito y reportes.
- Pantallas de privacidad, cookies, términos y condiciones.
- Integración de likes persistentes.
- Ajustes visuales para Android y web.
- Suscripciones, pasarela de pago y tarjetas de plan.
- Feedback en ajustes.
- SEO y enlaces enriquecidos.

#### Prompt representativo

```text
Estoy en una app Expo/React Native que funciona en web y Android.
Este hook usa localStorage y en Android falla. Queremos mantener la misma interfaz pública del hook,
pero usar AsyncStorage cuando estemos en native.
Propón una solución compatible con Expo, indica imports necesarios y riesgos de sincronización.
```

#### Resultado obtenido

Se obtuvieron propuestas para separar almacenamiento web y móvil, evitando dependencias directas de `localStorage` en entornos nativos. El equipo adaptó la solución a los servicios y hooks del frontend, revisando que no rompiera la experiencia de usuario ni las pantallas ya integradas.

#### Validación

- Pruebas manuales en web y Android.
- Revisión de navegación con Expo Router.
- Tests E2E para flujos principales cuando aplica.

---

#### 5.3 Testing, cobertura y calidad

Uno de los usos más valiosos de la IA ha sido la generación y mejora de tests. La IA se ha utilizado para proponer casos límite, fixtures, mocks y pruebas de regresión.

#### Evidencias cuantitativas

El fichero `cobertura_mejoras.csv` registra una mejora de cobertura global del **85% al 91%**, con **79 tests nuevos** distribuidos en módulos relevantes:

| Módulo | Cobertura previa | Cobertura obtenida | Tests nuevos |
| :--- | ---: | ---: | ---: |
| `main/analytics/views.py` | 24% | 100% | 11 |
| `main/views.py` | 45% | 100% | 13 |
| `main/permissions.py` | 72% | 96% | 34 |
| `main/rs/calendars.py` | 68% | 95% | 5 |
| `main/rs/events.py` | 69% | 98% | 5 |
| `current/schema/types.py` | 73% | 100% | 11 |
| **Total proyecto** | **85%** | **91%** | **79** |

#### Prompt representativo

```text
Actúa como QA backend para un proyecto Django.
Este módulo tiene baja cobertura. Te paso la vista, los serializers implicados y los modelos.
Genera una lista de tests unitarios que cubran:
- respuesta correcta,
- usuario no autenticado,
- permisos insuficientes,
- parámetros inválidos,
- ramas de error,
- y regresiones sobre bugs recientes.
No inventes campos: si no están en el código, pregúntame o márcalo como supuesto.
```

#### Resultado obtenido

La IA facilitó la identificación de ramas sin cubrir y la creación de esqueletos de tests. El equipo completó fixtures, usuarios, calendarios, eventos, permisos y datos necesarios. Esto permitió subir cobertura, detectar errores de permisos y reducir regresiones en endpoints críticos.

#### Validación

- `coverage run manage.py test`.
- Reportes de coverage en CI.
- SonarCloud en la rama `main`.
- Revisión humana de tests para evitar tests triviales o acoplados a la implementación.

---

#### 5.4 Pruebas end-to-end

La IA se ha utilizado para diseñar y ampliar pruebas E2E con Selenium, especialmente para convertir flujos funcionales reales en escenarios reproducibles.

#### Flujos cubiertos

Según `e2e/README.md`, las pruebas cubren:

- Validación de login con campos vacíos.
- Navegación login → registro.
- Registro exitoso.
- Login exitoso con credenciales válidas.
- Validación de registro con contraseñas distintas.
- Creación de calendario.
- Validación de creación de calendario sin nombre.
- Creación de evento.
- Validación de evento sin título.
- Carga de calendarios en vistas principales.
- Restricción de acciones protegidas sin sesión.
- Búsqueda por usuarios, calendarios y eventos.
- RSVP completo.
- Notificaciones vacías y notificación real de nuevo seguidor.

#### Prompt representativo

```text
Necesito ampliar tests E2E con Selenium para Current Calendar.
Con base en estos flujos de usuario, propón tests robustos que no dependan de sleeps fijos:
login, registro, crear calendario, crear evento, búsqueda, RSVP y notificaciones.
Incluye helpers reutilizables para esperar elementos y limpiar datos entre tests.
```

#### Resultado obtenido

La IA ayudó a estructurar escenarios E2E y helpers. El equipo ajustó selectores, tiempos de espera, datos de prueba y configuración Docker. El resultado es una suite documentada en `e2e/README.md`, con ejecución recomendada mediante Docker para evitar problemas de entorno.

---

#### 5.5 Revisión automática de pull requests

El repositorio contiene un workflow específico de IA para resumir PRs:

**Archivo:** `.github/workflows/PR_summarizer.yml`  
**Modelo:** `llama-3.3-70b-versatile`  
**Proveedor:** Groq, mediante API compatible con OpenAI  
**Temperatura:** `0.3`  
**Disparador:** `pull_request` en eventos `opened` y `synchronize`

#### Funcionamiento

1. El workflow obtiene el diff de la PR con `gh pr diff`.
2. Si el diff supera 20.000 caracteres, lo recorta para evitar sobrepasar el contexto.
3. Envía el diff a Groq con un prompt de revisión técnica.
4. Publica un comentario en la PR con:
   - Resumen general.
   - Archivos clave modificados.
   - Posibles riesgos.

#### Prompt del workflow, resumido

```text
Eres un Tech Lead experto revisando código.
Analiza el diff de una Pull Request y devuelve un resumen en español con:
1. Resumen general.
2. Archivos clave modificados.
3. Posibles riesgos de rendimiento, seguridad o deuda técnica.
Sé directo, sin saludos ni despedidas.
```

#### Resultado obtenido

El workflow reduce el tiempo necesario para entender una PR, especialmente en un equipo numeroso. Por ejemplo, en la PR #76 el bot generó un resumen automático explicando que se añadía el propio flujo de resumen de PRs, identificó `.github/workflows/PR_summarizer.yml` como archivo clave y avisó sobre la importancia de proteger la API key de Groq.

#### Limitaciones

- El resumen no sustituye una revisión real de código.
- Si el diff se trunca, puede omitir partes relevantes.
- Puede no detectar problemas de negocio o de arquitectura que no sean evidentes en el diff.
- Requiere mantener seguro `GROQ_API_KEY`.

---

#### 5.6 Debugging y resolución de incidencias

La IA ha sido útil en incidencias con múltiples capas: frontend, backend, base de datos, migraciones, permisos y datos de prueba.

#### Ejemplos de tareas donde la IA aporta valor

- Conflictos de migraciones en Django.
- Validaciones de fechas pasadas y eventos multiday.
- Persistencia de likes en frontend.
- Recuperación de contraseña y enlaces de email.
- Acciones protegidas sin login.
- Fallos de estilos en Android.
- Duplicidad de fetches y optimización de endpoints.
- Problemas de permisos en calendarios privados.

#### Prompt representativo

```text
Tengo este error al ejecutar tests tras resolver migraciones de Django.
Te paso:
- traceback,
- modelos afectados,
- migraciones recientes,
- y tests que fallan.
Explícame la causa probable y dame un plan de corrección seguro sin borrar datos.
Prioriza una solución compatible con CI y con la base de datos ya migrada.
```

#### Resultado obtenido

La IA ayuda a reducir el espacio de búsqueda y a ordenar hipótesis. El equipo mantiene la decisión final, especialmente en migraciones, porque un cambio incorrecto puede afectar datos persistentes. En estos casos, las propuestas se aplican de forma conservadora y se validan con tests.

---

#### 5.7 Seguridad, privacidad y cumplimiento

La IA se ha utilizado como segunda capa de revisión en tareas sensibles, pero no como autoridad final.

#### Tareas representativas

- Protección de rutas.
- Eliminación de búsqueda por email.
- Revisión de permisos de calendarios privados.
- Cookies, política de privacidad y términos legales.
- Tester destructivo y ciberdefensa.
- Revisión de acciones no autenticadas.

#### Prompt representativo

```text
Actúa como revisor de seguridad para una API Django REST.
Revisa estos endpoints de calendarios y usuarios.
Busca:
- endpoints que permitan acciones sin autenticación,
- exposición innecesaria de emails,
- permisos inconsistentes entre owner, co-owner, viewer y usuario anónimo,
- y riesgos de enumeración.
Devuelve hallazgos priorizados y tests de regresión recomendados.
```

#### Resultado obtenido

La IA ayudó a identificar preguntas de seguridad que el equipo debía responder. El resultado no fue aplicar ciegamente sus sugerencias, sino convertirlas en revisiones concretas: permisos, validaciones, cambios de búsqueda, pruebas y QA.

---

#### 5.8 Documentación y comunicación

La IA también se ha utilizado para mejorar la documentación, generar borradores y revisar claridad.

#### Documentos y áreas apoyadas

- `README.md` del proyecto.
- Contrato de APIs.
- Guía de uso para usuarios piloto.
- Restricciones y planes de pago.
- Documentación de Redis y GraphQL.
- E2E con Selenium.
- Informes de cobertura.
- Informes de uso de IA.
- Presentaciones y tareas no-code relacionadas con PPL.

#### Prompt representativo

```text
Redacta una sección de documentación para usuarios piloto sobre recuperación de contraseña.
Debe ser clara, en español, no demasiado técnica, y coherente con el flujo real:
1. solicitar email,
2. abrir enlace,
3. introducir nueva contraseña,
4. volver a iniciar sesión.
Indica también limitaciones conocidas.
```

#### Resultado obtenido

La IA aceleró la redacción inicial y ayudó a mantener estructura homogénea. Posteriormente el equipo corrigió contenido para que reflejara exactamente el comportamiento real de la aplicación.

---

### 6. Ejemplos de prompts por tarea, modelo y resultado

| Área | Herramienta / modelo | Prompt representativo | Resultado aprovechado | Validación |
| :--- | :--- | :--- | :--- | :--- |
| Resumen de PRs | Groq `llama-3.3-70b-versatile` | “Analiza este diff como Tech Lead y devuelve resumen, archivos clave y riesgos.” | Comentarios automáticos en PRs. | Revisión humana de la PR. |
| Tests backend | Claude Code / ChatGPT | “Genera tests para permisos owner/co-owner/viewer/anónimo sin inventar campos.” | Matriz de tests y esqueletos de casos. | `coverage run manage.py test`, CI y revisión. |
| E2E Selenium | Claude Code / ChatGPT | “Convierte estos flujos críticos en tests E2E robustos sin sleeps fijos.” | Helpers y escenarios E2E. | Ejecución con Docker/Selenium. |
| Migraciones Django | Claude Code | “Analiza este conflicto de migraciones y propón una solución segura.” | Hipótesis y plan de corrección. | Tests, revisión de migraciones y CI. |
| Frontend móvil/web | Claude Code / ChatGPT | “Sustituye localStorage por AsyncStorage manteniendo compatibilidad Expo web/native.” | Solución multiplataforma. | Prueba manual en web y Android. |
| Seguridad | ChatGPT / Claude | “Revisa endpoints buscando acciones sin login, exposición de email y permisos inconsistentes.” | Lista de riesgos y tests sugeridos. | QA, tests y revisión de código. |
| Documentación | ChatGPT / OpenAI / Claude | “Redacta esta guía para usuarios piloto con lenguaje claro y limitaciones.” | Borradores estructurados. | Revisión funcional por el equipo. |
| Informe actual | OpenAI Codex | “Analiza el repositorio y crea un informe detallado de uso de IA.” | Documento estructurado con evidencias. | Revisión del repositorio, project board y archivos. |

---

### 7. Resultados obtenidos

#### 7.1 Productividad

La IA ha reducido tiempos de bloqueo en tareas donde el problema estaba bien delimitado:

- Interpretar tracebacks.
- Localizar archivos relevantes.
- Proponer casos de prueba.
- Explicar APIs o patrones de Django/React Native.
- Generar borradores de documentación.
- Resumir diffs de PRs.

En un proyecto con muchas áreas funcionales y más de veinte integrantes, esto ha sido especialmente útil para que un desarrollador pudiera incorporarse rápidamente al contexto de una parte del sistema.

#### 7.2 Calidad y cobertura

El impacto más medible se observa en testing:

- Mejora de cobertura global del **85% al 91%**.
- **79 tests nuevos** en áreas de baja cobertura.
- Suite backend extensa con cientos de tests.
- Suite E2E con flujos críticos de usuario.
- CI con servicios reales de PostgreSQL/PostGIS y Redis.

La IA no “garantiza” calidad por sí misma, pero sí ha ayudado a pensar en ramas de error y casos límite que podrían haberse omitido.

#### 7.3 Revisión y mantenibilidad

El resumen automático de PRs ha ayudado a entender cambios con mayor rapidez. Además, los asistentes conversacionales han servido como una segunda lectura para detectar:

- Duplicidad de lógica.
- Posibles problemas de permisos.
- Inconsistencias entre backend y frontend.
- Validaciones insuficientes.
- Riesgos de deuda técnica.

#### 7.4 Documentación

La IA ha facilitado la redacción de documentos más completos y homogéneos. Esto es relevante porque el proyecto requiere no solo código, sino también:

- Guías de uso.
- Contratos de API.
- Documentación de despliegue.
- Informes de cobertura.
- Informes de calidad y proceso.
- Material de presentación.

---

### 8. Supervisión, validación y control humano

Para evitar un uso acrítico de la IA, el equipo ha aplicado varias barreras de control:

1. **Revisión de código por personas.**  
   Las sugerencias se integran mediante ramas y PRs, no directamente en `main`.

2. **CI obligatorio.**  
   El workflow de tests levanta PostgreSQL/PostGIS y Redis, instala dependencias y ejecuta `coverage run manage.py test`.

3. **Coverage y SonarCloud.**  
   En `main`, se genera reporte de coverage, HTML coverage y análisis de SonarCloud.

4. **Pruebas manuales.**  
   Especialmente necesarias en frontend móvil/web, estilos, navegación y flujos con OAuth o email.

5. **E2E no integrado en CI por estabilidad.**  
   Las pruebas E2E existen y están documentadas, pero se ejecutan aparte para evitar inestabilidad de Selenium en pipeline.

6. **Protección de secretos.**  
   Las claves como `GROQ_API_KEY`, tokens, secretos de Django o credenciales de servicios no se incluyen en prompts ni documentación pública.

7. **Adaptación al contexto real.**  
   Se evita copiar código sin comprobar nombres reales de campos, serializers, rutas, servicios y convenciones del proyecto.

---

### 9. Limitaciones detectadas

#### 9.1 Falta de trazabilidad completa

No existe todavía un registro sistemático de:

- Prompt exacto utilizado.
- Modelo exacto usado en cada sesión.
- Fragmentos aceptados, modificados o descartados.
- Validación asociada a cada sugerencia.

Esto dificulta medir con precisión qué parte del resultado procede de IA y qué parte procede de implementación manual.

#### 9.2 Riesgo de alucinaciones

La IA puede inventar:

- Campos de modelos inexistentes.
- Endpoints incorrectos.
- Imports no instalados.
- APIs desactualizadas.
- Comportamientos no implementados.

Por eso los prompts más efectivos han sido aquellos que incluyen código real y piden explícitamente **no inventar supuestos**.

#### 9.3 Riesgo de sobreconfianza

Un resumen de PR o una revisión automática puede parecer convincente aunque omita problemas relevantes. La IA ayuda a priorizar, pero no sustituye:

- Revisión de arquitectura.
- Validación funcional.
- Criterio de producto.
- Pruebas reales.
- Responsabilidad del equipo.

#### 9.4 Coste de contexto

En tareas grandes, la IA necesita mucho contexto. Si se le proporciona un fragmento aislado, puede proponer soluciones que no encajan con:

- Permisos existentes.
- Convenciones del frontend.
- Fixtures de tests.
- Migraciones previas.
- Configuración Docker/CI.

Claude Code ha sido útil precisamente porque permite trabajar con más contexto de repositorio, aunque sigue requiriendo supervisión.

---

### 10. Buenas prácticas consolidadas

A partir del uso durante el proyecto, se han consolidado las siguientes prácticas:

1. **Dar contexto concreto.**  
   Incluir archivo, función, error, objetivo y restricciones.

2. **Pedir planes antes que código cuando la tarea es compleja.**  
   En migraciones, permisos o seguridad conviene validar primero el enfoque.

3. **Solicitar tests junto con la implementación.**  
   Las respuestas son más útiles si incluyen casos de regresión.

4. **Exigir que la IA declare supuestos.**  
   Reduce el riesgo de campos o endpoints inventados.

5. **Usar baja temperatura en automatizaciones.**  
   El workflow de PRs usa `temperature: 0.3`, adecuado para respuestas más analíticas.

6. **No compartir secretos.**  
   Los prompts no deben incluir `.env`, tokens, claves API ni datos sensibles.

7. **Validar en local y CI.**  
   Toda propuesta útil debe pasar por tests, revisión y ejecución real.

8. **No usar la IA como única revisión.**  
   Es una ayuda para detectar riesgos, no una garantía.

---

### 11. Reflexiones del equipo

#### 11.1 Dónde ha aportado más valor

La IA ha sido especialmente útil en:

- **Testing:** pensar casos límite y acelerar tests repetitivos.
- **Debugging:** interpretar errores y ordenar hipótesis.
- **Documentación:** generar estructuras iniciales y mejorar claridad.
- **Revisión de PRs:** resumir diffs y señalar riesgos.
- **Onboarding técnico:** explicar partes del repositorio a integrantes que no habían trabajado en ese módulo.

#### 11.2 Dónde aporta menos valor

La IA es menos fiable cuando:

- La tarea depende de decisiones de producto no documentadas.
- La solución requiere conocer criterios específicos del profesorado, clientes o usuarios piloto.
- El problema está en una interacción visual difícil de reproducir solo con código.
- Falta contexto del repositorio.
- Se le pide “hacerlo todo” sin dividir en pasos verificables.

#### 11.3 Papel de Claude Code

Claude Code ha resultado especialmente útil para tareas de repositorio:

- Buscar archivos relacionados.
- Proponer cambios en varios módulos.
- Ejecutar comandos de diagnóstico.
- Generar y ajustar tests.
- Mantener un hilo de trabajo más cercano al código que un chat aislado.

Sin embargo, su uso debe seguir siendo controlado: revisar diffs, no aceptar cambios masivos sin entenderlos, y ejecutar tests después de cada bloque de cambios.

#### 11.4 Papel de los modelos conversacionales

Los asistentes tipo ChatGPT/OpenAI han sido útiles para:

- Resolver dudas conceptuales.
- Comparar alternativas.
- Redactar documentación.
- Explicar errores.
- Diseñar prompts para otras herramientas.

Su limitación principal es que, si no se les proporciona código real, pueden responder de forma genérica.

---

### 12. Recomendaciones para próximas entregas

1. **Crear un registro ligero de uso de IA por issue/PR.**  
   No hace falta guardar conversaciones completas, pero sí herramienta, modelo, tarea, resultado y validación.

2. **Añadir plantilla de PR con sección de IA.**  
   Permitiría saber si se usó Claude Code, ChatGPT, Groq u otra herramienta.

3. **Mantener prompts reutilizables.**  
   Por ejemplo: prompt de revisión de permisos, prompt de generación de tests, prompt de documentación de endpoint.

4. **Ampliar el workflow de PR summarizer.**  
   Posibles mejoras:
   - No duplicar comentarios si la PR se sincroniza muchas veces.
   - Incluir checklist de seguridad.
   - Indicar si el diff fue truncado.
   - Añadir enlaces a archivos clave.

5. **Auditar periódicamente código generado con IA.**  
   Especialmente en seguridad, permisos, pagos, privacidad y datos personales.

6. **Medir impacto real.**  
   Registrar métricas como tiempo ahorrado estimado, bugs detectados por IA, tests añadidos y propuestas descartadas.

---

### 13. Conclusiones

La Inteligencia Artificial se ha consolidado como una herramienta de apoyo relevante en Current Calendar. Ha contribuido a acelerar desarrollo, depuración, testing, documentación y revisión de PRs. El ejemplo más trazable a nivel de repositorio es el workflow de resumen automático con **Groq `llama-3.3-70b-versatile`**, mientras que a nivel de trabajo diario se ha usado **Claude Code** y asistentes conversacionales para resolver tareas de código y documentación.

El impacto más claro se observa en la mejora de calidad: incremento de cobertura del **85% al 91%**, ampliación de tests unitarios y E2E, mejor documentación y mayor agilidad para revisar cambios. También ha sido útil en tareas complejas como permisos, migraciones, compatibilidad móvil/web y validaciones.

No obstante, el valor de la IA ha dependido siempre de un uso crítico. Las respuestas se han tratado como propuestas, no como verdades. El equipo ha mantenido la responsabilidad sobre el diseño, la implementación, las pruebas y la decisión final. Esta forma de trabajo permite aprovechar la productividad de la IA sin comprometer la calidad, seguridad ni coherencia del proyecto.

En futuras entregas, la principal mejora no será usar más IA, sino **usarla con mayor trazabilidad**: registrar modelo, prompt resumido, resultado aceptado y validación realizada. Esto permitirá demostrar mejor el impacto real de la IA y convertirla en una herramienta de ingeniería más madura dentro del proceso del equipo.
