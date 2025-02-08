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

## 5️⃣ Entidades y Atributos 📊

🏫 Alumno
```sql
alumno_id INTEGER PRIMARY KEY, -- Identificador único
nombre VARCHAR(50), 
apellido VARCHAR(50),
email VARCHAR(100), 
telefono VARCHAR(20),
direccion VARCHAR(100)

📜 Inscripción

inscripcion_id INTEGER PRIMARY KEY, 
alumno_id INTEGER REFERENCES Alumno(alumno_id),
bootcamp_id INTEGER REFERENCES Bootcamp(bootcamp_id),
fechaInscripcion DATE,
estadoInscripcion VARCHAR(20)

💳 Pago

pago_id INTEGER PRIMARY KEY, 
inscripcion_id INTEGER REFERENCES Inscripcion(inscripcion_id),
fechaPago DATE,
montoPago DECIMAL(10,2)

🚀 Bootcamp

bootcamp_id INTEGER PRIMARY KEY, 
nombre VARCHAR(50),
descripcion VARCHAR(200),
fechaInicio DATE,
fechaFin DATE

📚 Módulo

modulo_id INTEGER PRIMARY KEY, 
nombre VARCHAR(50),
descripcion VARCHAR(200),
fechaInicio DATE,
bootcamp_id INTEGER REFERENCES Bootcamp(bootcamp_id)

👨‍🏫 Profesor

profesor_id INTEGER PRIMARY KEY, 
nombre VARCHAR(50),
apellido VARCHAR(50),
email VARCHAR(100),
telefono VARCHAR(20),
direccion VARCHAR(100),
modulo_id INTEGER REFERENCES Modulo(modulo_id)

🔗 Diagrama Entidad-Relación

📌 Ver el diseño en línea:
[📊 Ver el Diagrama E/R en dbdiagram.io](https://dbdiagram.io/d/E/R-inicial-679e65b9263d6cf9a0b914a8)


