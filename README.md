# Practica avanzada de SQL

Descripcion de la actividad [Practica SQL y DW](https://drive.google.com/file/d/1M6gLWsdVLbMGbEDw1aZ7Qm4MtcoS-GyA/view?usp=sharing)

En Big query el proyecto se identifica como:

Número de proyecto: 52153624215 
ID del proyecto: sql-dwulises 
[vinculo](https://console.cloud.google.com/bigquery?ws=!1m4!1m3!3m2!1ssql-dwulises!2skeepcoding)

# **Configuración Utilizada en la Práctica**

## **🖥️ Configuración del Entorno**
Esta práctica se realizó utilizando **Visual Studio Code**, **TablePlus** y otras herramientas para el desarrollo y análisis de bases de datos. En macOS Sequoia 15.3

### **🛠️ Versión de Visual Studio Code**
Para verificar la versión instalada:

```sh
code  1.97.0 33fc5a94a3f99ebe7087e8fe79fbe1d37a251016 arm64
```

### **📦 Extensiones Instaladas**
Se utilizaron las siguientes extensiones en VS Code:

```sh
code --list-extensions --show-versions
```

| Extensión | Identificador | Versión |
|-----------|--------------|---------|
| Markdown Lint | `davidanson.vscode-markdownlint` | 0.58.2 |
| GitLens | `eamodio.gitlens` | 16.2.2 |
| HTML & CSS Support | `ecmel.vscode-html-css` | 2.0.13 |
| EditorConfig | `editorconfig.editorconfig` | 0.16.7 |
| Prettier | `esbenp.prettier-vscode` | 11.0.0 |
| Google Translate | `funkyremi.vscode-google-translate` | 1.4.13 |
| GitHub Codespaces | `github.codespaces` | 1.17.3 |
| GitHub Copilot | `github.copilot` | 1.266.0 |
| GitHub Copilot Chat | `github.copilot-chat` | 0.24.0 |
| GitHub PRs & Issues | `github.vscode-pull-request-github` | 0.104.0 |
| TablePlus Integration | `tableplus.tableplus` | 6.2.1 |
| Tembo PostgreSQL | `tembo.postgresql` | https://tembo.io/ |

---

## **🛠️ Tecnologías Utilizadas**
En esta práctica se emplearon las siguientes herramientas y tecnologías:

- **Control de Versiones:** GitHub desktop + GitHub
- **Bases de Datos:** PostgreSQL (administrado con **TablePlus** y **Tembo**) para los ejercicios 2 al 5
- **Desarrollo SQL:** Google BigQuery (el proyecto completo)
- **Editor de Código:** Visual Studio Code
- **Gestión de Configuración:** EditorConfig, Prettier
- **Automatización & AI:** GitHub Copilot, GitHub Copilot Chat
- **Diagramación de Bases de Datos:** [dbdiagram.io](https://dbdiagram.io/)

---

## **🤖 Uso de Inteligencia Artificial**
Durante la práctica, se usaron herramientas de IA para asistir en la codificación y la generación de código SQL:

- **GitHub Copilot** → Sugerencias de código en tiempo real dentro de Visual Studio Code.
- **GitHub Copilot Chat** → Generación de explicaciones y asistencia en SQL, Python y otras tecnologías.
- **Google Translate** → Traducción de documentación técnica.

---

### **📊 Herramientas para la Diagramación**
Se utilizó [dbdiagram.io](https://dbdiagram.io/) para la creación y documentación del modelo relacional de la base de datos.

---



## 📌 Índice de Actividades 🔗

| #  | Actividad | Enlace |
|----|----------|--------|
| 1️⃣ | **Diagrama Entidad-Relación v3.0** | [Ir a actividad](https://dbdiagram.io/d/PRACTICA-SQL-Y-DW-679d9f4b263d6cf9a0b10be5) |
| 2️⃣ | **Creación de Base de Datos** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad2) |
| 3️⃣ | **Crear Tabla `ivr_detail`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad3) |
| 4️⃣ | **Generar campo `vdn_aggregation`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad4) |
| 5️⃣ | **Generar `document_type` y `document_identification`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad5) |
| 6️⃣ | **Generar el campo `customer_phone`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad6) |
| 7️⃣ | **Generar el campo `billing_account_id`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad7) |
| 8️⃣ | **Generar el campo `masiva_lg`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad8) |
| 9️⃣ | **Generar el campo `info_by_phone_lg`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad9) |
| 🔟 | **Generar el campo `info_by_dni_lg`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad10) |
| 1️⃣1️⃣ | **Generar `repeated_phone_24H` y `cause_recall_phone_24H`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad11) |
| 1️⃣2️⃣ | **Crear Tabla `ivr_summary`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad12) |
| 1️⃣3️⃣ | **Crear función `clean_integer`** | [Ir a actividad](https://github.com/gonzalezulises/practicaSQLKC/blob/main/Actividad13) |

---


# 📌 Diagrama Entidad-Relación (E/R)

## 1️⃣ Introducción

Para diseñar el diagrama E/R, seguí un enfoque sistemático que me permitió identificar entidades y sus relaciones de manera estructurada. Le hice varias actualizaciones cuando fui revisando el resto de las preguntas. A continuación, describo los pasos que seguí inicialmente hasta llegar a la version 3.0 que es la que esta en el indice:

### 🔍 **Pasos del diseño**
1. **Identificación de actores y roles:** Determinar quiénes interactúan con el sistema (alumnos, profesores, administradores, etc.).
2. **Definición de casos de uso:** Establecer las principales acciones que los actores pueden realizar (inscripción, creación de módulos, gestión de pagos).
3. **Identificación de entidades y atributos:** Listar la información clave que se debe almacenar (alumnos, módulos, pagos).
4. **Definición de relaciones:** Determinar cómo se conectan las entidades (uno a muchos, muchos a muchos).
5. **Identificación de claves primarias y foráneas:** Especificar qué campos vinculan las entidades entre sí.

---

## 2️⃣ Actores del Sistema

- **👨‍🎓 Alumno:** Persona que se inscribe en un bootcamp y participa en el aprendizaje.
- **👨‍🏫 Profesor:** Persona que imparte clases y guía a los alumnos.
- **🛠 Administrador:** Responsable de la gestión del sistema (bootcamps, módulos, usuarios).
- **📋 Coordinador:** Encargado de la coordinación de los bootcamps y módulos.
- **🎓 Tutor:** Brinda apoyo y orientación a los alumnos.
- **💰 Sistema de pago:** Proveedor externo que procesa los pagos de los alumnos.
- **🔐 Sistema de autenticación:** Sistema externo para la gestión de usuarios.

---

## 3️⃣ Casos de Uso

| # | Caso de Uso | Actor | Objetivo | Secuencia |
|---|------------|-------|----------|-----------|
| 1️⃣ | **Inscribirse en un bootcamp** | Alumno | Registrarse en un bootcamp | 1. Selecciona bootcamp → 2. Proporciona pago → 3. Se procesa pago → 4. Se autentica |
| 2️⃣ | **Crear un módulo** | Profesor | Crear un nuevo módulo | 1. Crea módulo → 2. Agrega contenido → 3. Guarda módulo |
| 3️⃣ | **Asignar un profesor a un módulo** | Administrador | Asignar profesor a un módulo | 1. Selecciona módulo → 2. Selecciona profesor → 3. Asigna profesor |
| 4️⃣ | **Acceder a materiales de aprendizaje** | Alumno | Consultar contenido del módulo | 1. Selecciona módulo → 2. Se muestran materiales → 3. Alumno accede |
| 5️⃣ | **Interactuar con un profesor** | Alumno | Comunicación con profesor | 1. Selecciona módulo → 2. Ve contacto profesor → 3. Interactúa |
| 6️⃣ | **Crear un nuevo bootcamp** | Administrador | Agregar bootcamp al sistema | 1. Crea bootcamp → 2. Agrega módulos → 3. Guarda bootcamp |
| 7️⃣ | **Gestionar pagos** | Administrador | Administrar pagos de alumnos | 1. Selecciona pago → 2. Se muestra información → 3. Gestiona pago |

---

## 4️⃣ Requisitos del Sistema 📋

A partir de los casos de uso, el sistema debe cumplir con los siguientes requisitos:
✔️ Permitir a los alumnos inscribirse en bootcamps.  
✔️ Permitir a los profesores crear y gestionar módulos.  
✔️ Permitir a los administradores gestionar bootcamps y módulos.  
✔️ Permitir a los alumnos acceder a materiales de aprendizaje.  
✔️ Permitir a los alumnos interactuar con profesores.  

---

# 5️⃣ Entidades y Atributos 📊

Link al 🔗 [Diagrama Entidad-Relación](https://dbdiagram.io/d/E/R-inicial-679e65b9263d6cf9a0b914a8)

```sql

// Utilizando DBML to define your database structure y generar la diagramacion, de manera que la pueda reutilizar

Table Alumno {
  alumno_id integer [primary key]
  nombre varchar
  apellido varchar
  email varchar
  telefono varchar
  direccion varchar
  document_type varchar
  document_identification varchar
  canal_id integer [ref: > Canal_Inscripcion.canal_id]  
}

Table Bootcamp {
  bootcamp_id integer [primary key]
  nombre varchar
  descripcion varchar
  fechaInicio date
  fechaFin date
  costo decimal(10,2)
  profesor_id integer [ref: > Profesor.profesor_id]  
}

Table Modulo {
  modulo_id integer [primary key]
  nombre varchar
  descripcion varchar
  fechaInicio date
  fechaFin date
  bootcamp_id integer [ref: > Bootcamp.bootcamp_id]
}

Table Profesor {
  profesor_id integer [primary key]
  nombre varchar
  apellido varchar
  email varchar
  telefono varchar
  direccion varchar
}

Table Profesor_Modulo {
  profesor_id integer [ref: > Profesor.profesor_id]
  modulo_id integer [ref: > Modulo.modulo_id]
  fecha_asignacion date
  carga_horaria integer
  rol varchar
  PRIMARY KEY (profesor_id, modulo_id)
}

Table Bootcamp_Profesor {
  bootcamp_id integer [ref: > Bootcamp.bootcamp_id]
  profesor_id integer [ref: > Profesor.profesor_id]
  rol varchar
  PRIMARY KEY (bootcamp_id, profesor_id)
}

Table Inscripcion {
  inscripcion_id integer [primary key]
  fechaInscripcion date
  alumno_id integer [ref: > Alumno.alumno_id]
  bootcamp_id integer [ref: > Bootcamp.bootcamp_id]
  canal_id integer [ref: > Canal_Inscripcion.canal_id]
  estadoInscripcion enum('pendiente', 'confirmada', 'cancelada', 'completada')
}

Table Canal_Inscripcion {
  canal_id integer [primary key]
  nombre varchar
}

Table Pago {
  pago_id integer [primary key]
  inscripcion_id integer [ref: > Inscripcion.inscripcion_id]
  fechaPago date
  montoPago decimal
  billing_account_id varchar
}

Table IVR_Call {
  ivr_call_id integer [primary key]
  phone_number varchar
  ivr_result varchar
  vdn_label varchar
  start_date date
  start_date_id integer
  end_date date
  end_date_id integer
  total_duration decimal(6,2)
  customer_segment varchar
  ivr_language varchar
  inscripcion_id integer [ref: > Inscripcion.inscripcion_id]
  canal_id integer [ref: > Canal_Inscripcion.canal_id]
  alumno_id integer [ref: > Alumno.alumno_id]  
}

Table IVR_Module {
  ivr_module_id integer [primary key]
  ivr_call_id integer [ref: > IVR_Call.ivr_call_id]
  module_sequence integer
  module_name varchar
  module_duration decimal(6,2)
  module_result varchar
}

Table IVR_Step {
  ivr_step_id integer [primary key]
  ivr_module_id integer [ref: > IVR_Module.ivr_module_id]
  ivr_call_id integer [ref: > IVR_Call.ivr_call_id]  
  step_id integer
  step_sequence integer
  step_name varchar
  step_result varchar
  step_description_error varchar
}

```
# **Integración del Sistema IVR en el Modelo de Datos**

## **3. Creación de la Tabla `ivr_detail`**

Con la solicitud de integración de un sistema IVR para la atención al cliente, fue necesario extender el modelo de datos para incluir nuevos procesos y entidades. A continuación, se detallan los cambios implementados.

---

### **3.1 Nuevas Entidades Agregadas**
Se incorporaron las siguientes entidades al modelo de datos:

- **`Canal_Inscripcion`**: Registra la fuente a través de la cual los alumnos se inscriben (Ejemplo: WhatsApp, Email, Llamada Telefónica).
- **`Bootcamp_Profesor`**: Relaciona a los profesores con los bootcamps, permitiendo asignar roles específicos dentro del programa.
- **`Profesor_Modulo`**: Relaciona profesores con los módulos que imparten, almacenando información sobre carga horaria y fecha de asignación.
- **`IVR_Call`**: Almacena información sobre cada llamada del usuario, incluyendo su resultado, duración y segmento de cliente.
- **`IVR_Module`**: Representa los módulos por los que pasa una llamada durante el flujo IVR.
- **`IVR_Step`**: Registra los pasos específicos seguidos dentro de cada módulo IVR.
- **`IVR_Detail` (Vista Consolidada)**: Integra información de `IVR_Call`, `IVR_Module` y `IVR_Step` para generar reportes detallados sobre la interacción de los clientes.

---

### **3.2 Definición de Nuevas Relaciones**
Las siguientes relaciones fueron definidas para conectar los nuevos elementos con el modelo de datos existente:

- **`IVR_Call` → `Inscripcion`** a través de `inscripcion_id`: Permite vincular llamadas con usuarios registrados.
- **`IVR_Module` → `IVR_Call`** mediante `ivr_call_id`: Relaciona las llamadas con los módulos del IVR.
- **`IVR_Step` → `IVR_Module`** a través de `ivr_module_id`: Conecta los pasos con los módulos IVR.
- **`IVR_Call` → `Canal_Inscripcion`** mediante `canal_id`: Identifica el origen de la llamada (Ejemplo: WhatsApp, Email, Llamada Telefónica).

---

### **3.3 Ajustes en Datos y Cálculos**
Se realizaron los siguientes ajustes en la estructura de datos:

- Se agregaron los campos `document_type` y `document_identification` en `Alumno` para identificar al usuario en interacciones con el IVR.
- Se incluyó `billing_account_id` en `Pago` para vincular la información de facturación con el sistema IVR.
- Se creó un código SQL consolidado que recopila información de las llamadas IVR, incluyendo detalles del alumno, módulos y pasos dentro del sistema.
- La consulta utiliza `LEFT JOIN` para relacionar las tablas `IVR_Call`, `IVR_Module`, `IVR_Step`, `Inscripcion`, `Alumno` y `Pago`, asegurando que cada llamada contenga información completa sobre su duración, resultado, módulos utilizados y pasos seguidos.
- Se transforman las fechas de inicio y fin en el formato `YYYYMMDD` para facilitar su análisis.
- La consulta también incorpora datos del alumno como tipo de documento, identificación y número de teléfono, junto con el identificador de su cuenta de facturación.
- Se emplea `GROUP BY` para garantizar que cada combinación de llamada, módulo y paso aparezca en una sola fila, permitiendo generar reportes detallados sobre las interacciones en el IVR.

🔗 **Consulta SQL**: [Ejecutar en RunSQL](https://runsql.com/r/64948899d420ab15)

```sql
SELECT
   c.ivr_call_id,
   c.phone_number,
   c.ivr_result,
   c.vdn_label,
   c.start_date,
   EXTRACT(YEAR FROM c.start_date) * 10000 + EXTRACT(MONTH FROM c.start_date) * 100 + EXTRACT(DAY FROM c.start_date) AS calls_start_date_id,
   c.end_date,
   EXTRACT(YEAR FROM c.end_date) * 10000 + EXTRACT(MONTH FROM c.end_date) * 100 + EXTRACT(DAY FROM c.end_date) AS calls_end_date_id,
   c.total_duration,
   c.customer_segment,
   c.ivr_language,
   steps_data.calls_steps_module,
   m.module_sequence,
   m.module_name,
   m.module_duration,
   m.module_result,
   s.step_sequence,
   s.step_name,
   s.step_result,
   s.step_description_error,
   a.document_type,
   a.document_identification,
   a.telefono AS customer_phone,
   p.billing_account_id 
FROM IVR_Call c
LEFT JOIN Inscripcion i ON c.inscripcion_id = i.inscripcion_id
LEFT JOIN Alumno a ON i.alumno_id = a.alumno_id 
LEFT JOIN Pago p ON i.inscripcion_id = p.inscripcion_id 
LEFT JOIN IVR_Module m ON c.ivr_call_id = m.ivr_call_id
LEFT JOIN IVR_Step s ON m.ivr_module_id = s.ivr_module_id
LEFT JOIN (
   SELECT ivr_module_id, COUNT(ivr_step_id) AS calls_steps_module
   FROM IVR_Step
   GROUP BY ivr_module_id
) AS steps_data ON s.ivr_module_id = steps_data.ivr_module_id

### **3.4 Impacto en los Casos de Uso**

La incorporación del sistema IVR modificó algunos procesos existentes y agregó nuevos casos de uso, tales como:

- 📞 **Consultar estado de inscripción vía IVR** → El alumno consulta su inscripción llamando al IVR.
- 💳 **Consultar pagos realizados vía IVR** → El alumno ingresa su identificación y el IVR consulta su historial de pagos.
- 🤖 **Recibir asistencia automatizada** → El alumno recibe información de soporte mediante IVR sin intervención humana.
- 📅 **Recibir notificaciones de eventos y clases** → El IVR notifica fechas importantes a alumnos registrados.
- 📡 **Escalar una consulta a un asesor humano** → Si el IVR no resuelve la duda, redirige la llamada a un agente.
- 📊 **Monitoreo de calidad del IVR** → El administrador revisa reportes sobre interacciones y tiempos de resolución en IVR.
- 🔍 **Registrar intenciones de usuarios** → El IVR almacena patrones de preguntas para mejorar la experiencia del usuario en futuras interacciones.