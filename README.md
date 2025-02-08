# Practica avanzada de SQL

Descricpcion de la actividad [Practica SQL y DW](https://drive.google.com/file/d/1M6gLWsdVLbMGbEDw1aZ7Qm4MtcoS-GyA/view?usp=sharing)

# 📌 Diagrama Entidad-Relación (E/R)

## 1️⃣ Introducción

Para diseñar el diagrama E/R, seguí un enfoque sistemático que me permitió identificar entidades y sus relaciones de manera estructurada. A continuación, describo los pasos que seguí:

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
## 📌 Índice de Actividades 🔗

| #  | Actividad | Enlace |
|----|----------|--------|
| 1️⃣ | **Diagrama Entidad-Relación** | [Ir a actividad](#1-diagrama-entidad-relacion) |
| 2️⃣ | **Creación de Base de Datos** | [Ir a actividad](#2-creacion-de-base-de-datos) |
| 3️⃣ | **Crear Tabla `ivr_detail`** | [Ir a actividad](#3-crear-tabla-ivr_detail) |
| 4️⃣ | **Generar campo `vdn_aggregation`** | [Ir a actividad](#4-generar-el-campo-vdn_aggregation) |
| 5️⃣ | **Generar `document_type` y `document_identification`** | [Ir a actividad](#5-generar-los-campos-document_type-y-document_identification) |
| 6️⃣ | **Generar el campo `customer_phone`** | [Ir a actividad](#6-generar-el-campo-customer_phone) |
| 7️⃣ | **Generar el campo `billing_account_id`** | [Ir a actividad](#7-generar-el-campo-billing_account_id) |
| 8️⃣ | **Generar el campo `masiva_lg`** | [Ir a actividad](#8-generar-el-campo-masiva_lg) |
| 9️⃣ | **Generar el campo `info_by_phone_lg`** | [Ir a actividad](#9-generar-el-campo-info_by_phone_lg) |
| 🔟 | **Generar el campo `info_by_dni_lg`** | [Ir a actividad](#10-generar-el-campo-info_by_dni_lg) |
| 1️⃣1️⃣ | **Generar `repeated_phone_24H` y `cause_recall_phone_24H`** | [Ir a actividad](#11-generar-los-campos-repeated_phone_24h-y-cause_recall_phone_24h) |
| 1️⃣2️⃣ | **Crear Tabla `ivr_summary`** | [Ir a actividad](#12-crear-tabla-ivr_summary) |
| 1️⃣3️⃣ | **Crear función `clean_integer`** | [Ir a actividad](#13-crear-funcion-clean_integer) |

---
