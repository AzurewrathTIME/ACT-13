🎓 Sistema de Gestión Escolar en C++
📌 Descripción

Este proyecto consiste en un sistema de gestión escolar desarrollado en C++, diseñado para administrar información básica de alumnos, materias, calificaciones, maestros y administradores.

El programa funciona mediante un menú interactivo en consola, permitiendo al usuario realizar diferentes operaciones de registro, consulta, modificación y eliminación de información.

El proyecto hace uso de conceptos fundamentales de Programación Orientada a Objetos (POO), incluyendo:

    Clases y objetos.

    Encapsulamiento.

    Herencia.

    Polimorfismo.

    Constructores.

    Métodos set y get.

    Arreglos de objetos.

    Arreglos de apuntadores.

    Memoria dinámica mediante new y delete.

    Funciones para modularizar el programa.

🚀 Funcionalidades

El sistema cuenta con las siguientes opciones:
Opción	Funcionalidad
1	Registrar alumno
2	Mostrar un alumno
3	Mostrar todos los alumnos
4	Calcular promedio de edades
5	Buscar alumno por nombre
6	Eliminar alumno
7	Modificar alumno
8	Agregar materia
9	Registrar calificación
10	Mostrar historial académico
11	Registrar maestro
12	Registrar administrador
13	Mostrar maestros y administradores
14	Salir del programa
🧩 Estructura del proyecto

El programa se encuentra organizado mediante diferentes clases que representan las principales entidades del sistema.
📚 Clase Materia

Representa una materia académica.

Contiene:

    nombre: nombre de la materia.

    clave: identificador de la materia.

Métodos principales:

setNombre()
getNombre()
setClave()
getClave()
mostrar()

📝 Clase Calificacion

Representa una calificación asociada a una materia.

Contiene:

    claveMateria: clave de la materia.

    nota: calificación obtenida.

El método setNota() valida que la calificación se encuentre dentro del rango permitido de 0 a 10.

setClaveMateria()
getClaveMateria()
setNota()
getNota()
mostrar()

👤 Clase Persona

Es la clase base del sistema para representar personas.

Contiene:

    nombre

    edad

Además, cuenta con el método virtual:

virtual void mostrarInformacion()

Esto permite implementar polimorfismo mediante las clases derivadas.
🎓 Clase Alumno

Hereda de la clase Persona.

Además de los atributos heredados, contiene:

    matricula

    Arreglo de materias.

    Arreglo de calificaciones.

    Número de materias registradas.

    Número de calificaciones registradas.

La clase permite:

    Agregar materias.

    Registrar calificaciones.

    Buscar materias mediante su clave.

    Consultar materias.

    Consultar calificaciones.

    Mostrar información del alumno.

La capacidad máxima definida para materias y calificaciones es de 10 registros por alumno.
👨‍🏫 Clase Maestro

Hereda de Persona.

Agrega el atributo:

string especialidad;

Permite almacenar la especialidad del maestro y mostrar su información mediante una implementación propia de:

mostrarInformacion()

🧑‍💼 Clase Administrador

También hereda de Persona.

Agrega el atributo:

string departamento;

Permite registrar y mostrar el departamento al que pertenece el administrador.
🏗️ Conceptos de Programación Orientada a Objetos

Uno de los objetivos principales del proyecto es aplicar diferentes conceptos de POO.
🔒 Encapsulamiento

Los atributos de las clases se encuentran declarados como private o protected, evitando el acceso directo desde cualquier parte del programa.

El acceso se realiza mediante métodos set y get.

Ejemplo:

class Materia {
private:
    string nombre;
    string clave;

public:
    void setNombre(string n) {
        nombre = n;
    }

    string getNombre() {
        return nombre;
    }
};

🧬 Herencia

Las clases Alumno, Maestro y Administrador heredan de Persona.

class Alumno : public Persona

class Maestro : public Persona

class Administrador : public Persona

Esto permite reutilizar atributos y funcionalidades comunes como el nombre y la edad.
🔄 Polimorfismo

La clase Persona define:

virtual void mostrarInformacion()

Las clases derivadas implementan su propia versión del método.

Esto permite utilizar un arreglo de apuntadores:

Persona* personas[100];

y almacenar diferentes tipos de objetos derivados de Persona.

Por ejemplo:

personas[numPersonas] = new Maestro(n, e, esp);

o:

personas[numPersonas] = new Administrador(n, e, d);

Posteriormente, al ejecutar:

personas[i]->mostrarInformacion();

se ejecuta la versión correspondiente al tipo de objeto almacenado.
💾 Manejo de memoria

Para almacenar maestros y administradores se utilizan objetos creados dinámicamente mediante new.

Ejemplo:

personas[numPersonas] = new Maestro(n, e, esp);

Al finalizar el programa, la memoria reservada se libera utilizando delete:

for (int i = 0; i < numPersonas; i++) {
    delete personas[i];
}

Además, la clase Persona cuenta con un destructor virtual:

virtual ~Persona() {
}

Esto permite una correcta destrucción de los objetos derivados cuando son eliminados mediante un apuntador de tipo Persona*.
📊 Almacenamiento de información

El programa utiliza arreglos de tamaño fijo.

La constante:

const int MAX = 10;

establece el número máximo de alumnos que pueden almacenarse.

Para maestros y administradores se utiliza:

Persona* personas[100];

por lo que se pueden almacenar hasta 100 personas en dicho arreglo.

Cada alumno puede almacenar como máximo:

    10 materias.

    10 calificaciones.

🔍 Búsqueda de alumnos

El sistema cuenta con una función para localizar alumnos mediante su nombre:

int buscarIndiceAlumno(string nombre)

La función recorre el arreglo de alumnos y compara el nombre proporcionado con los nombres registrados.

Si encuentra coincidencia, devuelve la posición del alumno.

Si no encuentra resultados, devuelve:

-1

Este mecanismo se utiliza en diferentes operaciones como:

    Búsqueda.

    Eliminación.

    Modificación.

    Registro de materias.

    Registro de calificaciones.

    Consulta del historial académico.

📖 Historial académico

El sistema permite consultar el historial académico de cada alumno.

Para esto, primero se recorren las materias registradas y posteriormente se buscan las calificaciones que correspondan a la clave de cada materia.

La relación entre materia y calificación se realiza mediante:

claveMateria

De esta manera, una calificación queda asociada a una materia específica.

Ejemplo conceptual:

Alumno: Carlos

Materia: Programacion
Clave: PROG01
Nota: 9.5

Materia: Matematicas
Clave: MAT01
Nota: 8.7

📋 Menú principal

Al iniciar el programa se muestra un menú interactivo:

===== MENU =====
1. Registrar Alumno.
2. Mostrar un Alumno.
3. Mostrar Todos los Alumnos.
4. Calcular Promedio.
5. Buscar Alumno por nombre.
6. Eliminar Alumno.
7. Modificar Alumno.
8. Agregar Materia.
9. Registrar Calificacion.
10. Mostrar Historial Academico.
11. Registrar Maestro.
12. Registrar Administrador.
13. Mostrar Maestros y Administradores.
14. Salir.

El usuario selecciona una opción y el programa ejecuta la función correspondiente.

El menú continúa ejecutándose hasta que el usuario selecciona la opción 14.
🛠️ Requisitos

Para compilar y ejecutar el programa se necesita:

    Un compilador compatible con C++.

    Soporte para C++ estándar.

    Una terminal o IDE.

Algunas opciones recomendadas son:

    Visual Studio Code.

    Visual Studio.

    Code::Blocks.

    Dev-C++.

    MinGW / GCC.

    CLion.

▶️ Compilación

Si se utiliza g++, el programa puede compilarse mediante:

g++ main.cpp -o sistema_escolar

Posteriormente, puede ejecutarse con:
Windows

sistema_escolar.exe

Linux / macOS

./sistema_escolar

💡 Ejemplo de uso

Un flujo básico del programa podría ser:

1. Registrar Alumno
   ↓
2. Agregar Materia
   ↓
3. Registrar Calificación
   ↓
4. Mostrar Historial Académico

Por ejemplo:

Nombre: Juan
Edad: 20
Matricula: A001

Alumno registrado.

Nombre del alumno: Juan
Nombre de la materia: Programacion
Clave de la materia: PROG01

Materia agregada.

Nombre del alumno: Juan
Clave de la materia: PROG01
Nota: 9.5

Calificacion registrada.

Posteriormente, al consultar el historial:

Historial de Juan

Materia: Programacion
Clave: PROG01
Nota: 9.5
---------------------

⚠️ Consideraciones

Este proyecto utiliza almacenamiento en memoria, por lo que la información no se conserva después de cerrar el programa.

También utiliza arreglos de tamaño fijo, por lo que existen límites establecidos para la cantidad de registros.

El programa está pensado principalmente con fines académicos y educativos, especialmente para demostrar la implementación de conceptos de programación orientada a objetos en C++.
🔮 Posibles mejoras futuras

Como posibles extensiones del proyecto se podrían implementar:

    Persistencia de información mediante archivos .txt o .csv.

    Uso de archivos binarios.

    Base de datos.

    Interfaz gráfica.

    Validaciones más completas de entradas.

    Búsqueda por matrícula.

    Modificación de materias y calificaciones.

    Eliminación de materias.

    Promedio de calificaciones por alumno.

    Promedio general de cada materia.

    Sistema de usuarios y contraseñas.

    Uso de vector en lugar de arreglos estáticos.

    Uso de smart pointers para una gestión de memoria más segura.

    Separación del proyecto en archivos .h y .cpp.

📁 Posible estructura de archivos

Actualmente el programa puede mantenerse en un solo archivo, por ejemplo:

SistemaEscolar/
│
├── main.cpp
└── README.md

Sin embargo, para una estructura más profesional podría dividirse de la siguiente manera:

SistemaEscolar/
│
├── main.cpp
│
├── Persona.h
├── Persona.cpp
│
├── Alumno.h
├── Alumno.cpp
│
├── Maestro.h
├── Maestro.cpp
│
├── Administrador.h
├── Administrador.cpp
│
├── Materia.h
├── Materia.cpp
│
├── Calificacion.h
├── Calificacion.cpp
│
└── README.md

👨‍💻 Objetivo académico

El objetivo principal de este proyecto es aplicar de manera práctica los fundamentos de Programación Orientada a Objetos en C++, mediante el desarrollo de un sistema que simula algunas operaciones básicas de una institución educativa.

A través de su implementación se practican conceptos como encapsulamiento, herencia, polimorfismo, constructores, destructores, arreglos de objetos, funciones, validaciones y manejo de memoria dinámica.
📄 Licencia

Este proyecto fue desarrollado con fines educativos y puede ser utilizado, modificado y adaptado para prácticas académicas relacionadas con programación en C++.
⭐ Conclusión

El sistema representa una implementación básica de un entorno de gestión escolar utilizando C++. Su estructura permite demostrar cómo diferentes clases pueden relacionarse entre sí para representar entidades del mundo real y cómo los principios de la Programación Orientada a Objetos pueden utilizarse para construir aplicaciones modulares y organizadas.
