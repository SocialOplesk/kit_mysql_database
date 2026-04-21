# SOCIAL OPLESK
### 
<br/>

# Crear base de datos con MySQL 
**hack: (crear db & tablas)**

<br/>

**El proceso a realizar se hace con scripts SQL**

**Requisitos previos**

- Conocer de relaciones de base de datos
- https://onecompiler.com/mysql
- Cuenta en github.com
<br/>


### 🟢 Paso 1
- crear modelo 1 a 1
```
CREATE DATABASE ejemplo;
USE ejemplo;

CREATE TABLE persona (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    dni VARCHAR(10) NOT NULL UNIQUE
);

CREATE TABLE contacto (
    id INT AUTO_INCREMENT PRIMARY KEY,
    telefono VARCHAR(15),
    persona_id INT NOT NULL UNIQUE,
    FOREIGN KEY (persona_id) REFERENCES persona(id) ON DELETE CASCADE
);
```
⚡insertar data 1 a 1
```
1. Insert en tabla 'persona':

INSERT INTO persona (nombre, dni)
VALUES ('Juan Carlos', '12345678A');

----------------------------------------------------

2. Insert en tabla 'contacto' usando el id generado:

INSERT INTO contacto (telefono, persona_id)
VALUES ('611223344', 1);
```

### 🟢 Paso 2
- crear modelo 1 a n
```
CREATE DATABASE ejemplo;
USE ejemplo;

CREATE TABLE cliente (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    email VARCHAR(50) NOT NULL
);

CREATE TABLE orden (
    id INT AUTO_INCREMENT PRIMARY KEY,
    fecha DATE NOT NULL,
    cliente_id INT NOT NULL,
    FOREIGN KEY (cliente_id) REFERENCES cliente(id) ON DELETE CASCADE
);
```

### 🟢 Paso 3
- crear modelo n a n
```
CREATE DATABASE ejemplo;
USE ejemplo;

CREATE TABLE estudiante (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL,
    dni VARCHAR(10) NOT NULL
);

CREATE TABLE curso (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nombre VARCHAR(50) NOT NULL
);

CREATE TABLE estudiante_curso (
    id INT AUTO_INCREMENT PRIMARY KEY,
    estudiante_id INT NOT NULL,
    curso_id INT NOT NULL,
    FOREIGN KEY (estudiante_id) REFERENCES estudiante(id) ON DELETE CASCADE,
    FOREIGN KEY (curso_id) REFERENCES curso(id) ON DELETE CASCADE,
    UNIQUE (estudiante_id, curso_id)  -- No repetir misma matrícula
);
```

---
<h3 align="center">SOCIAL OPLESK</h3>
