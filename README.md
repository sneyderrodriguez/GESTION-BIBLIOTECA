# 📚 Sistema de Gestión de Biblioteca Universitaria

> Aplicación de consola desarrollada en **Java** para organizar un catálogo de libros y revistas, consultar su disponibilidad y administrar listas de espera de materiales bibliográficos.

![Java](https://img.shields.io/badge/Java-POO-orange?logo=openjdk)
![Estado](https://img.shields.io/badge/Estado-Proyecto%20académico-blue)

---

## 📌 Sobre el proyecto

Este proyecto implementa un sistema básico de gestión de biblioteca universitaria mediante **programación orientada a objetos (POO)**. Permite registrar materiales, buscarlos por código, mostrar el catálogo y gestionar solicitudes en listas de espera. La clase `Main` contiene un ejemplo de ejecución con datos de prueba.

---

## ✨ Características principales

- 📖 **Registro de materiales:** incorpora libros y revistas al catálogo mediante un código identificador.
- 🔎 **Búsqueda por código:** recupera un material registrado.
- 📋 **Consulta del catálogo:** muestra el tipo, título, año y estado de disponibilidad.
- 👥 **Listas de espera:** agrega nombres de usuarios y consulta la lista asociada a cada código.
- 📦 **Entrega de materiales:** retira al primer usuario de la lista de espera y marca el material como no disponible cuando existe.

> **Alcance actual:** el proyecto es una demostración por consola. Los datos se almacenan en memoria durante la ejecución; no incluye base de datos ni interfaz gráfica.

---

## 🧰 Tecnologías y conceptos

- **Java** y biblioteca estándar (`HashMap`, `ArrayList`, `Map`).
- **POO:** abstracción, herencia, encapsulamiento y polimorfismo.
- **Interfaces:** `Catalogable` define el acceso al código de cada material.
- **Colecciones:** almacenamiento del catálogo y de las listas de espera.

---

## 🏗️ Organización del sistema

| Clase / interfaz | Responsabilidad |
| --- | --- |
| `Catalogable` | Define el método `getCodigo()`. |
| `Material` | Clase abstracta con los datos comunes y el método `mostrarInfo()`. |
| `Libro` | Extiende `Material` e incorpora autor e ISBN. |
| `Revista` | Extiende `Material` e incorpora edición y temática. |
| `SistemaBiblioteca` | Administra el catálogo, las búsquedas y las listas de espera. |
| `Main` | Ejecuta una demostración del funcionamiento. |

---

## 📁 Estructura del proyecto

```text
GESTION-BIBLIOTECA/
├── src/
│   ├── Catalogable.java
│   ├── Libro.java
│   ├── Main.java
│   ├── Material.java
│   ├── Revista.java
│   └── SistemaBiblioteca.java
├── .gitignore
└── SistemaGestionBibliotecaUniversitaria.iml
```

> Se omiten los archivos internos de Git y la configuración local del IDE.

---

## 🖥️ Ejecutar el proyecto localmente

**Requisito:** tener instalado un JDK y disponibles los comandos `javac` y `java`.

### 1. Obtener el código

Descarga o clona el repositorio y entra a la carpeta `GESTION-BIBLIOTECA`.

### 2. Compilar

Desde la raíz del proyecto, ejecuta:

```bash
javac -d out src/*.java
```

Este comando compila las clases y guarda los archivos generados en `out`.

### 3. Ejecutar

```bash
java -cp out Main
```

La aplicación registra materiales de ejemplo, crea listas de espera, consulta materiales, muestra el catálogo y realiza una entrega. También puedes abrir el proyecto en IntelliJ IDEA y ejecutar `Main.java`.

---

## 🔍 Ejemplo de uso

La clase `Main` demuestra operaciones como las siguientes:

```java
SistemaBiblioteca biblioteca = new SistemaBiblioteca();

biblioteca.registrarMaterial(
    new Revista("R-050", "El papel dual de los insectos", 1999, true, 20, "Ciencia")
);

biblioteca.agregarAListaEspera("R-050", "Ana");
biblioteca.agregarAListaEspera("R-050", "Jessica");

Material material = biblioteca.buscarMaterial("R-050");
if (material != null) {
    material.mostrarInfo();
}

biblioteca.entregarMaterial("R-050");
```

El ejemplo registra una revista, agrega dos personas a su lista, consulta sus datos y entrega el material a la primera persona en espera.

---

## 🚧 Limitaciones y posibles mejoras

- Validar los códigos antes de agregar usuarios o entregar materiales: actualmente, `entregarMaterial()` puede producir un `NullPointerException` si existe una lista de espera para un código sin material registrado.
- Evitar que el registro de un código repetido sobrescriba un material existente.
- Añadir operaciones explícitas de préstamo y devolución, con reglas de disponibilidad.
- Incorporar persistencia de datos para conservar el catálogo al cerrar la aplicación.
- Agregar pruebas automatizadas y una interfaz de usuario.

---

## 📫 Contacto

- **GitHub:** [SneyderRodriguez](https://github.com/SneyderRodriguez)
- **LinkedIn:** [Sneyder Rodríguez](https://www.linkedin.com/in/sneyder-rodriguez-ingeniero-de-sistemas/)
- **Portafolio:** [sneyderrodriguez.netlify.app](https://sneyderrodriguez.netlify.app/)

---

## 📄 Licencia

Este proyecto está disponible bajo la licencia **MIT**.

Puedes utilizar, modificar y distribuir el código respetando los términos establecidos en dicha licencia.
