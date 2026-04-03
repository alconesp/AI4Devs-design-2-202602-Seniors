# Listado de prompts para la generación de las user stories

Para la realización de la práctica he utilizado Google Gemini en modo Fast.

## Prompt inicial para generación del product roadmap

Actúa como un Product Owner senior con experiencia en metodologías ágiles, productos SAAS B2B y B2C.
Analiza la descripción del producto en el fichero adjunto y propón un product roadmap de alto nivel, llegando ahora mismo a la definición de las épicas únicamente.

### Respuesta

Hola. Entiendo perfectamente el desafío. Como **Product Owner**, mi enfoque con este ATS (al que llamaremos provisionalmente **ACE**) es transformar esa sólida base técnica y funcional que ya tienes en un producto que no solo gestione procesos, sino que se convierta en una ventaja estratégica real para las empresas en la guerra por el talento.

El roadmap que propongo se divide en **cuatro horizontes estratégicos (H1-H4)**. He diseñado las épicas para asegurar que el sistema sea funcional desde el primer día (MVP), pero escalando rápidamente hacia la inteligencia de datos y la automatización.

Aquí tienes la propuesta de **Product Roadmap: Proyecto ACE**.

---

#### 🗺️ Product Roadmap: Épicas de Alto Nivel

##### H1: El Cimiento (MVP - Core Efficiency)
*Objetivo: Eliminar el uso de Excels y centralizar la operación básica.*

* **Épica 1: Motor de Gestión de Talento (Unified Talent Pool):** Implementación de la base de datos centralizada de candidatos, sistema de búsqueda avanzada y etiquetado dinámico para crear una fuente de verdad única.
* **Épica 2: Visual Pipeline & Kanban Workflow:** Desarrollo del tablero visual para la gestión de vacantes, permitiendo a los reclutadores mover candidatos entre etapas y configurar flujos personalizados por cada puesto.
* **Épica 3: Ingesta Inteligente (NLP CV Parsing):** Implementación del servicio de microservicios para la extracción automática de datos de archivos PDF/Word, reduciendo el trabajo manual de entrada de datos.

---

##### H2: Expansión de Alcance (Reach & Engagement)
*Objetivo: Atraer más talento con menos esfuerzo y mejorar la marca empleadora.*

* **Épica 4: Publicación Omnicanal (Multiposting):** Integración con APIs de terceros (LinkedIn, Indeed, portales locales) para la difusión masiva de vacantes con un solo clic.
* **Épica 5: Experiencia del Candidato (Career Site Builder):** Herramienta para que las empresas generen sus propios portales de empleo corporativos, optimizados para SEO y dispositivos móviles.
* **Épica 6: Colaboración Activa (Hiring Manager Portal):** Creación de interfaces simplificadas para que los jefes de equipo puedan puntuar candidatos (scorecards), dejar notas internas y ver sus calendarios de entrevistas.

---

##### H3: Optimización y Cierre (Velocity & Conversion)
*Objetivo: Reducir el Time-to-Hire y asegurar el cumplimiento legal.*

* **Épica 7: Automatización de Comunicaciones:** Motor de reglas que dispara correos electrónicos basados en cambios de etapa y plantillas dinámicas, eliminando el "silencio administrativo".
* **Épica 8: Gestión de Ofertas y Firma Digital:** Flujo de aprobación financiera integrado y conexión con proveedores de firma electrónica (DocuSign/Eversign) para el cierre formal de contratos.
* **Épica 9: Centro de Cumplimiento (GDPR Shield):** Automatización de la gestión de consentimientos, borrado de datos por inactividad y trazabilidad total para auditorías de privacidad.

---

##### H4: Inteligencia y Escala (Intelligence & Analytics)
*Objetivo: Tomar decisiones basadas en datos y automatizar decisiones de bajo valor.*

* **Épica 10: Advanced Analytics & ROI:** Cuadros de mando integrales sobre coste por contratación, efectividad de fuentes y cuellos de botella en el pipeline.
* **Épica 11: IA de Matching y Ranking:** Algoritmos que comparan la descripción del puesto con el perfil extraído del CV para priorizar automáticamente a los candidatos más aptos.
* **Épica 12: Arquitectura Multi-Tenant SaaS:** Refactorización final para el aislamiento de datos por cliente y escalado elástico en la nube para soportar miles de organizaciones simultáneas.

---

##### 💡 Nota del Product Owner:
Para el **H1**, priorizaremos la **Épica 3 (Parsing)** sobre la **Épica 4 (Multiposting)**. ¿Por qué? Porque de nada sirve atraer a cientos de candidatos si el equipo de reclutamiento colapsa procesando los datos manualmente. Primero preparamos la "casa" para recibir el volumen.

¿Te gustaría que profundizáramos en el **Backlog de Usuario** de alguna de estas épicas en particular para empezar a definir los *User Stories*?

## Prompt 2 - Generación de las user stories de la primera épica
Sí, vamos a empezar a definir las User Stories de la primera épica.

Actúa como un Product Owner senior con experiencia en metodologías ágiles.

A partir de la descripción de la primera épica, genera las User Stories necesarias para desarrollar esa funcionalidad, que cumplan los criterios INVEST. Para cada una incluye:
- Título descriptivo
- Historia en formato "Como [rol], quiero [acción], para [beneficio]"
- 3 criterios de aceptación en formato BDD (Dado que/Cuando/Entonces)
- Estimación de complejidad (S/M/L)
- Evaluación breve contra INVEST

Después de generar las historias, sugiere un orden de priorización y justifica tu decisión.

### Respuesta

Como **Product Owner**, vamos a desglosar la **Épica 1: Motor de Gestión de Talento (Unified Talent Pool)**. El objetivo aquí es construir el cimiento sobre el cual reposará toda la inteligencia del ATS.

Para que estas historias de usuario (US) sean efectivas, nos enfocaremos en la **trazabilidad y la >integridad de los datos**, asegurando que el reclutador tenga una "fuente de verdad" fiable.

---

#### 📋 User Stories: Épica 1 - Motor de Gestión de Talento

##### US 1.1: Creación manual de perfil de candidato
* **Historia:** Como **Reclutador**, quiero **poder dar de alta a un candidato manualmente** introduciendo sus datos básicos, para **añadir talento que contacto por canales no integrados** (ej. ferias de empleo o referidos directos).
* **Criterios de Aceptación (BDD):**
    * **Dado que** estoy en el panel de "Candidatos", **cuando** pulso en "Añadir Candidato" e introduzco un email que ya existe, **entonces** el sistema debe mostrar un error de duplicado y no permitir el registro.
    * **Dado que** relleno los campos obligatorios (nombre, apellido, email), **cuando** guardo el perfil, **entonces** el sistema debe generar un UUID único para ese candidato.
    * **Dado que** el candidato ha sido creado, **cuando** consulto su ficha, **entonces** debo ver la fuente ("Source") marcada como "Manual" por defecto.
* **Estimación:** **S** (Small). Es un CRUD básico sobre la entidad Candidate.
* **Evaluación INVEST:** **Cumple.** Es **Independiente** de otras fuentes de ingesta y su valor es **Estimable** y **Pequeño**.

##### US 1.2: Buscador global por criterios técnicos
* **Historia:** Como **Reclutador**, quiero **buscar candidatos por nombre, correo o habilidades**, para **localizar perfiles específicos en mi base de datos de forma inmediata**.
* **Criterios de Aceptación (BDD):**
    * **Dado que** tengo 1.000 candidatos en la base de datos, **cuando** escribo una tecnología en el campo de búsqueda (ej: "Java"), **entonces** el sistema debe devolver solo los perfiles que tengan ese tag o palabra clave.
    * **Dado que** realizo una búsqueda por email exacto, **cuando** el candidato existe, **entonces** el sistema debe redirigirme directamente a su ficha de perfil.
    * **Dado que** el buscador está activo, **cuando** no hay coincidencias, **entonces** el sistema debe mostrar un mensaje de "No se han encontrado candidatos" con una opción para limpiar filtros.
* **Estimación:** **M** (Medium). Requiere indexación eficiente de campos en la base de datos.
* **Evaluación INVEST:** **Cumple.** Es **Valiosa** (evita la pérdida de talento) y **Testeable** mediante pruebas de regresión de búsqueda.

##### US 1.3: Sistema de Etiquetado Dinámico (Tags)
* **Historia:** Como **Reclutador**, quiero **asignar etiquetas personalizadas a los candidatos**, para **categorizar el talento según criterios propios de la empresa** (ej: "Senior", "Inglés C1", "Hard-to-fill").
* **Criterios de Aceptación (BDD):**
    * **Dado que** estoy en la ficha de un candidato, **cuando** escribo una nueva etiqueta, **entonces** el sistema debe guardarla en el array/JSONB del perfil y estar disponible para futuros candidatos.
    * **Dado que** un candidato tiene varias etiquetas, **cuando** elimino una de ellas, **entonces** el cambio debe persistir sin afectar al resto de los datos del perfil.
    * **Dado que** quiero organizar mi pool, **cuando** hago clic en una etiqueta desde la ficha, **entonces** el sistema debe mostrarme todos los candidatos que comparten esa misma etiqueta.
* **Estimación:** **S** (Small). Implementación de un componente de gestión de tags en el frontend y guardado en JSONB.
* **Evaluación INVEST:** **Cumple.** Es **Negociable** (podemos decidir si los tags son predefinidos o libres) y **Valiosa**.

##### US 1.4: Repositorio de Documentos Centralizado
* **Historia:** Como **Reclutador**, quiero **subir y visualizar múltiples archivos (CV, Portfolio) en el perfil del candidato**, para **tener toda su documentación técnica organizada en un solo lugar**.
* **Criterios de Aceptación (BDD):**
    * **Dado que** intento subir un archivo, **cuando** el formato es PDF o DOCX y pesa menos de 10MB, **entonces** el sistema debe almacenarlo en S3 y vincular la URL al perfil.
    * **Dado que** el candidato ya tiene un CV, **cuando** subo una nueva versión, **entonces** el sistema debe permitirme elegir cuál es el documento "Principal".
    * **Dado que** visualizo el perfil, **cuando** hago clic en el documento, **entonces** el sistema debe abrir una previsualización o descargar el archivo de forma segura.
* **Estimación:** **M** (Medium). Requiere integración con almacenamiento externo (S3) y manejo de tipos de archivo.
* **Evaluación INVEST:** **Cumple.** Es **Independiente** y fundamental para la posterior US de Parsing.

---

#### ⚖️ Priorización Sugerida (Orden de Ejecución)

Propongo el siguiente orden de desarrollo para el primer Sprint:

1.  **US 1.1 (Alta Manual):** Es el bloque mínimo para que la base de datos empiece a poblarse. Sin datos, no hay nada que buscar ni etiquetar.
2.  **US 1.4 (Documentos):** El valor de un ATS reside en el CV físico. Necesitamos la capacidad de almacenamiento antes de añadir capas de organización.
3.  **US 1.3 (Tags):** Permite empezar a organizar el talento de forma rudimentaria pero efectiva mientras se desarrolla el buscador complejo.
4.  **US 1.2 (Buscador):** Se deja para el final de la épica porque su utilidad real aparece cuando ya existe un volumen crítico de datos cargados mediante las historias anteriores.

##### Justificación:
Este orden sigue una lógica de **"Disponibilidad de Datos"**. Primero habilitamos la entrada de información (1.1 y 1.4), luego su categorización (1.3) y finalmente su recuperación avanzada (1.2). Esto permite entregar un incremento de producto funcional al final de cada semana de desarrollo.

¿Te parece bien este enfoque para comenzar el Sprint Planning, o preferirías priorizar el buscador por encima de los documentos?

## Prompt 3 - Creación de los tickets de trabajo para la primera user story

Sí, el orden aportado me parece correcto. Por lo que vamos a iniciar la generación de tickets de trabajo para la primera User Story.
Teniendo en cuenta que partimos desde cero, no hay nada implementado, necesitamos primero definir los requisitos técnicos necesarios para poder implementar esa user story. Crea los tickets de trabajo que sean necesarios para implementar la user story. Cada ticket de trajo debe tener lo siguiente:
- Título claro y conciso
- Descripción detallada. Debe incluir el propósito del ticket y los detalles específicos del mismo.
- Criterios de aceptación. Utiliza la metodología Gherkin para especificarlos.

### Respuesta

Como **Product Owner**, para abordar la **US 1.1: Creación manual de perfil de candidato** desde un estado de "cero absoluto", debemos descomponer la historia en tickets técnicos que preparen la infraestructura, el backend y el frontend.

Siguiendo el diseño de **arquitectura desacoplada** y el **modelo de datos** propuestos, aquí tienes los tickets de trabajo iniciales:

---

#### Ticket 1: Configuración de Entorno y Modelo de Datos "Candidate"
**Título:** Implementación del esquema de base de datos y entidad Candidate.

**Descripción:**
El propósito de este ticket es establecer la base técnica del sistema. Se debe configurar la base de datos relacional (PostgreSQL) y definir la tabla `candidates` según el modelo de datos especificado. Es fundamental asegurar que el campo `id` sea un **UUID** para garantizar la escalabilidad y que el `email` sea único.

**Detalles específicos:**
* Configurar conexión a PostgreSQL.
* Crear migración para la tabla `candidates` con los campos: `id` (PK, UUID), `first_name` (String), `last_name` (String), `email` (String, Unique), `phone` (String), `linkedin_url` (String) y `source` (Enum: Manual, LinkedIn, etc.).
* Implementar el modelo en el Core Service.

**Criterios de Aceptación (Gherkin):**
* **Dado que** no existe la base de datos, **cuando** ejecuto las migraciones del sistema, **entonces** la tabla `candidates` debe crearse con todas las restricciones de integridad definidas.
* **Dado que** intento insertar un registro, **cuando** el `email` ya existe en la tabla, **entonces** la base de datos debe devolver un error de violación de unicidad.
* **Dado que** se crea un nuevo registro, **cuando** no se especifica un ID, **entonces** el sistema debe generar automáticamente un UUID v4.

---

#### Ticket 2: Desarrollo del Endpoint de Creación (API REST)
**Título:** API de creación de candidatos (POST /candidates).

**Descripción:**
Desarrollar el endpoint en el **Application Service** (o Core Service) que reciba los datos del formulario de alta manual y los persista en la base de datos. El servicio debe validar que los datos cumplen con el formato esperado antes de intentar la persistencia.

**Detalles específicos:**
* Crear ruta `POST /api/v1/candidates`.
* Validar formato de email y campos obligatorios (nombre, apellido, email).
* Manejar errores de servidor y de validación (400 Bad Request, 409 Conflict para duplicados, 500 Internal Error).

**Criterios de Aceptación (Gherkin):**
* **Dado que** envío una petición válida con `first_name`, `last_name` y `email`, **cuando** la API procesa la solicitud, **entonces** debe retornar un código 201 Created y el objeto del candidato creado incluyendo su UUID.
* **Dado que** envío una petición sin el campo obligatorio `email`, **cuando** la API valida la entrada, **entonces** debe retornar un código 400 y un mensaje indicando el campo faltante.
* **Dado que** el email ya está registrado, **cuando** la API intenta procesar la creación, **entonces** debe retornar un código 409 Conflict.

---

#### Ticket 3: Interfaz de Formulario "Nuevo Candidato" (Frontend)
**Título:** Implementación del formulario de alta manual en el Dashboard.

**Descripción:**
Crear la interfaz de usuario en la **SPA (React/Vue)** que permita al reclutador introducir los datos del candidato. El formulario debe conectarse con la API desarrollada en el Ticket 2 y proporcionar feedback visual al usuario sobre el éxito o error de la operación.

**Detalles específicos:**
* Crear vista/modal de "Añadir Candidato".
* Implementar validaciones de cliente (campos vacíos, formato de email).
* Consumir el endpoint `POST /candidates`.
* Añadir notificaciones (Toasts) para confirmar la creación o mostrar errores.

**Criterios de Aceptación (Gherkin):**
* **Dado que** el reclutador está en la sección de candidatos, **cuando** pulsa el botón "Nuevo" y completa el formulario correctamente, **entonces** el sistema debe limpiar el formulario y mostrar un mensaje de éxito.
* **Dado que** el usuario introduce un formato de email inválido (ej: "usuario@com"), **cuando** intenta enviar el formulario, **entonces** el sistema debe mostrar un aviso de error visual antes de realizar la llamada a la API.
* **Dado que** el backend responde con un error de duplicado (409), **cuando** el frontend recibe la respuesta, **entonces** debe mostrar un mensaje informando que el candidato ya existe con ese correo.

---

#### Ticket 4: Configuración de Auth & Gateway (Infraestructura)
**Título:** Configuración de seguridad y enrutamiento inicial en API Gateway.

**Descripción:**
Como el sistema parte de cero, necesitamos configurar el **API Gateway** y el **Auth Service** para asegurar que solo usuarios autenticados (Reclutadores) puedan crear candidatos.

**Detalles específicos:**
* Configurar el Gateway para enrutar las peticiones al servicio de candidatos.
* Implementar middleware de autenticación (JWT/OAuth) para proteger el endpoint de creación.

**Criterios de Aceptación (Gherkin):**
* **Dado que** un usuario no autenticado intenta acceder al endpoint `POST /candidates`, **cuando** realiza la petición, **entonces** el API Gateway debe denegar el acceso con un código 401 Unauthorized.
* **Dado que** un reclutador tiene un token válido, **cuando** envía la petición a través del Gateway, **entonces** la solicitud debe llegar correctamente al servicio de aplicación.

---

Con estos 4 tickets, el equipo de desarrollo tiene una hoja de ruta clara para implementar la primera funcionalidad del sistema desde los cimientos. ¿Te gustaría que estimemos los puntos de historia para estos tickets técnicos?

## Prompt 4 - Petición adicional de tickets

Antes de estimarlos, echo en falta algunos tickets adicionales. El ticket 4 habla de la configuración de API Gateway y el Auth Service para asegurar que los usuarios autenticados puedan crear candidatos. Sin embargo, ya que el proyecto está en blanco, todavía no tenemos los tickets de trabajo para poder dar de alta nuevos reclutadores.
Créame los tickets de trabajo necesarios para poder crear los reclutadores en el sistema. Esto supone que al iniciar el proyecto, por primera vez, el sistema debería tener ya creada una cuenta de administrador. Necesitamos poder actualizar la contraseña de esa cuenta "administrador" para que sea la que inicie todo el proceso de alta de reclutadores. También necesitaremos los tickets para que los reclutadores puedan iniciar sesión y accedan a la sección de candidatos

### Respuesta

Tienes toda la razón. Como **Product Owner**, mi enfoque estaba demasiado centrado en la funcionalidad de negocio (*Candidates*) y he pasado por alto el **"Bootstrap"** del sistema. Para que un reclutador pueda crear un candidato, primero debe existir el reclutador y una forma de entrar al sistema.

A continuación, presento los tickets técnicos para establecer la gestión de usuarios, la seguridad y el acceso inicial.

---

#### Ticket 5: Script de Bootstrap y Cuenta Administradora
**Título:** Seed de Base de Datos: Usuario Administrador Inicial.

**Descripción:**
Dado que el sistema empieza de cero, necesitamos un "Super Usuario" inicial que nos permita gestionar al resto del equipo. El propósito de este ticket es crear un script de migración o *seeding* que inserte un registro en la tabla `users` con el rol de `ADMIN`.

**Detalles específicos:**
* Crear tabla `users` con campos: `id` (UUID), `name`, `email` (Unique), `password_hash`, `role` (Enum: ADMIN, RECRUITER).
* Crear un script que inserte un usuario con email `admin@ace-ats.com`.
* La contraseña debe estar cifrada (ej. BCrypt).

**Criterios de Aceptación (Gherkin):**
* **Dado que** la base de datos está recién migrada, **cuando** ejecuto el script de *seed*, **entonces** se debe crear un registro en la tabla `users` con el rol `ADMIN`.
* **Dado que** el usuario admin ya existe, **cuando** consulto su contraseña en la DB, **entonces** el valor debe ser un hash ilegible y no texto plano.

---

#### Ticket 6: Endpoint de Cambio de Contraseña (Primer Inicio)
**Título:** Funcionalidad de actualización de contraseña para Administrador.

**Descripción:**
Por seguridad, la contraseña del administrador del script de *seed* debe ser cambiada inmediatamente. Este ticket habilita la lógica para que el administrador actualice su credencial de acceso.

**Detalles específicos:**
* Endpoint `PATCH /api/v1/users/me/password`.
* Validar que la nueva contraseña cumple con criterios de complejidad (mínimo 8 caracteres, números, símbolos).

**Criterios de Aceptación (Gherkin):**
* **Dado que** el administrador está autenticado, **cuando** envía su contraseña actual y una nueva válida, **entonces** el sistema debe actualizar el `password_hash` en la base de datos.
* **Dado que** el administrador envía una contraseña nueva que no cumple los requisitos mínimos, **cuando** la API la procesa, **entonces** debe retornar un código 400 y no actualizar los datos.

---

#### Ticket 7: Gestión de Usuarios (Alta de Reclutadores)
**Título:** CRUD de Usuarios: Creación de Reclutadores por Administrador.

**Descripción:**
Este ticket permite al Administrador dar de alta a otros miembros del equipo (Reclutadores) para que puedan empezar a trabajar en el ATS.

**Detalles específicos:**
* Endpoint `POST /api/v1/users`.
* Restringir este endpoint: **Solo** usuarios con `role: ADMIN` pueden ejecutarlo.

**Criterios de Aceptación (Gherkin):**
* **Dado que** un usuario con rol `ADMIN` envía los datos de un nuevo reclutador, **cuando** la API procesa la petición, **entonces** se crea el nuevo usuario con rol `RECRUITER`.
* **Dado que** un usuario con rol `RECRUITER` intenta crear a otro usuario, **cuando** envía la petición, **entonces** el sistema debe denegar la acción con un código 403 Forbidden.

---

#### Ticket 8: Servicio de Autenticación (Login & JWT)
**Título:** Implementación de Login y generación de Tokens de Acceso.

**Descripción:**
Desarrollar la lógica de intercambio de credenciales por un token de acceso (JWT) para que los usuarios puedan mantener su sesión activa y acceder a las secciones protegidas.

**Detalles específicos:**
* Endpoint `POST /api/v1/auth/login`.
* Validación de credenciales contra la base de datos.
* Generación de JWT firmado con los datos del usuario (id, email, rol).

**Criterios de Aceptación (Gherkin):**
* **Dado que** un usuario introduce email y contraseña correctos, **cuando** envía el login, **entonces** el sistema debe retornar un JWT y los datos básicos del perfil.
* **Dado que** un usuario introduce credenciales erróneas, **cuando** intenta loguearse, **entonces** el sistema debe retornar un código 401 Unauthorized.

---

#### Ticket 9: Frontend - Login y Protección de Rutas
**Título:** Interfaz de Login y Redirección al Dashboard.

**Descripción:**
Crear la pantalla de acceso en la SPA y asegurar que solo los usuarios logueados puedan ver la sección de candidatos.

**Detalles específicos:**
* Formulario de Login (Email/Password).
* Guardado del JWT en LocalStorage o Cookies seguras.
* Implementación de "Guards" en las rutas de React/Vue para redirigir al login si no hay token.

**Criterios de Aceptación (Gherkin):**
* **Dado que** el usuario no ha iniciado sesión, **cuando** intenta entrar en `/candidates`, **entonces** el sistema debe redirigirlo automáticamente a `/login`.
* **Dado que** el login es exitoso, **cuando** el frontend recibe el token, **entonces** debe redirigir al usuario al Dashboard principal.

---

#### Resumen de Dependencias Técnicas:
Para implementar la **US 1.1** (Creación de candidatos), ahora el orden técnico lógico es:
1.  **Ticket 5** (User DB & Admin Seed).
2.  **Ticket 8** (Auth Service/Login).
3.  **Ticket 4** (API Gateway con seguridad activa).
4.  **Ticket 1, 2, 3** (Funcionalidad de Candidatos).

¿Deseas que procedamos ahora con la estimación de esfuerzo para este conjunto completo de tickets iniciales?

## Prompt 5 - Estimación de esfuerzo

Sí, por favor, estima todos los tickets que tenemos hasta ahora, los 9, usando story points y horas de trabajo. Ten en cuenta que el desarrollo lo haríamos usando IA, por lo que la estimación debe ser acorde esto.

### Respuesta

Como **Product Owner**, estimar un proyecto "greenfield" (desde cero) utilizando **IA Generativa** (como cursores de código, Copilot o agentes autónomos) cambia drásticamente las reglas del juego. La IA acelera la escritura de *boilerplate*, migraciones y tests unitarios, pero la **complejidad de arquitectura y seguridad** sigue requiriendo validación humana experta.

Para esta estimación, utilizaremos una escala de **Story Points (SP)** basada en la serie de Fibonacci y convertiremos a **horas hombre (HH)** asumiendo una reducción de tiempo del **40-50%** gracias al uso de IA en la generación de código y esquemas.

---

### 📊 Estimación de Tickets: Proyecto ACE (Desarrollo con IA)

| Ticket | Título | SP | Horas (Con IA) | Justificación de Complejidad |
| :--- | :--- | :--- | :--- | :--- |
| **T5** | Script Bootstrap & Admin Seed | 1 | 2h | La IA genera el script SQL/Migración y el hash BCrypt instantáneamente. |
| **T8** | Servicio de Auth (Login/JWT) | 3 | 6h | Tarea estándar. La IA sobresale implementando lógica JWT, pero requiere revisión en la firma de tokens. |
| **T6** | Actualización de Contraseña | 1 | 2h | Lógica simple de backend. Implementación rápida de validaciones con ayuda de IA. |
| **T7** | CRUD Usuarios (Alta Reclutadores) | 2 | 4h | Basado en el patrón de la T5/T8. La IA replica el patrón de controlador y servicio rápidamente. |
| **T4** | API Gateway & Auth Guard | 3 | 5h | Configuración de infraestructura. Requiere ajuste fino de reglas de enrutamiento y middleware. |
| **T1** | Modelo de Datos Candidate | 1 | 2h | Definición de tabla y tipos UUID. La IA genera la migración y el modelo en segundos. |
| **T2** | API POST /candidates | 2 | 4h | Endpoint estándar. La IA ayuda con la validación de esquemas (Zod/Joi) y manejo de errores. |
| **T3** | Frontend: Formulario Alta | 3 | 6h | Creación de componentes UI. La IA genera el JSX/HTML rápido, pero el manejo de estados y feedback lleva tiempo. |
| **T9** | Frontend: Login & Auth Guards | 2 | 4h | Implementación de persistencia de token (Cookies/Local) y protección de rutas en el cliente. |
| **TOTAL** | | **18 SP** | **35h** | **Aprox. 1 Semana de desarrollo para un Fullstack Senior con IA.** |

---

### 📉 Análisis del Esfuerzo Total

* **Velocidad Impulsada por IA:** Sin IA, este conjunto de 9 tickets (que incluye seguridad, infraestructura inicial y modelos) podría estimarse en unas **60-70 horas**. La reducción a **35 horas** refleja la capacidad de la IA para generar el 80% del código repetitivo, dejando al desarrollador el 20% de configuración crítica y lógica de negocio.
* **Camino Crítico:** La configuración de la seguridad (**T8** y **T4**) y la interfaz de usuario (**T3**) son los puntos que consumen más tiempo, ya que requieren pruebas manuales para asegurar que la experiencia del usuario sea fluida y segura.

---

### 🚀 Sugerencia de Sprint (Sprint 1: "The Foundation")

Dado que el total son **35 horas**, este bloque encaja perfectamente en un **Sprint de 1 semana** para un desarrollador o un par de días para un equipo pequeño.

**Orden de ejecución recomendado para maximizar el uso de IA:**
1.  **Backbone (T5, T1, T8):** Define las estructuras de datos. La IA necesita esto para "entender" el contexto del resto del código.
2.  **Seguridad (T6, T7, T4):** Establece las reglas de acceso.
3.  **Funcionalidad (T2, T3, T9):** Construye la experiencia visible sobre la base segura.

¿Te gustaría que preparemos el **Sprint Backlog** oficial con estas estimaciones para dar por iniciada la fase de desarrollo?

## Conclusiones

Me ha sorprendido bastante que el modelo Fast de Gemini generase estas historias de la forma que lo ha hecho. Apenas he realizado cambios, de hecho creo que lo único adicional que le he pedido ha sido que tenga en cuenta que no teníamos nada hecho y que debía crear un usuario de administración inicial, el resto lo ha considerado y generado directamente.

Este proceso ha sido interesante de seguir y me da algunas ideas de cómo funcionar en mis próximos proyectos personales. Creo que es una forma muy buena de poder estructurar el trabajo a realizar.

El principal problema con el que me he encontrado al hacer esta práctica ha sido la falta real de dirección, de lo que hay que hacer, ya que no se trata de un proyecto real en el cual esté involucrado, por lo que la dirección que le voy dando al agente no sigue una hoja de ruta, simplemente veo que el resultado es aceptable y continúo. Entiendo que esto variará en el momento en el que me ponga a hacer el proyecto final ya que ahí sí tengo claro el objetivo, lo que quiero conseguir, las tecnologías a utilizar, etc.