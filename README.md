# 🏥 Sistema de Evaluación de Compatibilidad para Trasplantes Renales

![Pharo Smalltalk](https://img.shields.io/badge/Language-Pharo_Smalltalk-blue)
![Paradigm](https://img.shields.io/badge/Paradigm-Object_Oriented_Programming-brightgreen)
![Status](https://img.shields.io/badge/Status-Completed-success)

## 💻 ¿De qué trata el proyecto?
Desarrollamos un sistema de gestión en **Pharo Smalltalk** para un centro de trasplantes. El corazón del proyecto es un algoritmo capaz de evaluar automáticamente la compatibilidad médica entre pacientes en lista de espera y posibles donantes. 

Para ello, modelamos reglas médicas reales divididas en:
* **Criterios Obligatorios:** Evaluaciones excluyentes como compatibilidad de grupo sanguíneo (ABO), pruebas de Crossmatch y serologías. Si no se cumplen, el trasplante no puede realizarse.
* **Criterios Deseables:** Factores como compatibilidad HLA, tamaño corporal y edad, los cuales otorgan un porcentaje de afinidad para priorizar al donante más adecuado.

El sistema procesa esta información y genera reportes detallados en formato `.csv` con los pacientes, donantes registrados y los resultados de compatibilidades para la toma de decisiones.

## 🛠️ Tecnologías y Conceptos
* **Lenguaje:** Pharo Smalltalk.
* **Patrones / Conceptos:** Herencia, Polimorfismo, Clases Abstractas, Manejo de Colecciones, FileStreams para escritura de archivos CSV.
* **Contexto Académico:** Paradigmas de Programación - UTN FRSF.

## 🚀 Instalación y Uso
Para ejecutar este proyecto, necesitarás tener instalado [Pharo](https://pharo.org/) (se recomienda la versión 11 o superior).

### 1. Importar el código
1. Abre tu imagen de Pharo.
2. Arrastra el archivo `TP1.st` directamente hacia la ventana de Pharo.
3. En el menú emergente, selecciona **"File-in entire file"**. Esto cargará automáticamente todas las clases y métodos en el paquete llamado `TP1`.

### 2. Configuración inicial
Antes de realizar las evaluaciones, el sistema requiere definir un **Mínimo de Compatibilidad** (por defecto es 50%). 
Puedes ajustarlo ejecutando:
`ResultadoCompatibilidad minimoCompatibilidad: 60`. "Define el umbral de aprobación"

### 3. Ejecución de Pruebas (Playground)
Utiliza el código de prueba para verificar el flujo completo:  
1) Abre un Playground `(Ctrl + O, W)`.
2) Registra pacientes, donantes y sus estudios clínicos.
3) Configura el EvaluadorCompatibilidad con criterios obligatorios y deseables.
4) Ejecuta el cálculo y observa los resultados en el `Transcript`.

### 4. Generación de Reportes CSV
El sistema genera tres archivos de salida para la gestión del centro:
* `_pacientes.csv`: DNI, nombre, apellido y meses en lista de espera.
* `_donantes.csv`: Datos de donantes con pacientes asociados.
* `_compatibilidades.csv`: Resultados que superan el mínimo de compatibilidad.

### Ejemplo de ejecución:
`centro guardaRegistros: 'HospitalCentral'.`

## 🧠 ¿Qué aprendí?
* **Programación Orientada a Objetos (POO):** Llevamos la teoría a la práctica aplicando encapsulamiento, polimorfismo y herencia para modelar entidades complejas como pacientes, estudios clínicos y evaluadores de criterios.
* **Pensamiento 100% en Objetos:** Salir de los lenguajes tradicionales y programar en Smalltalk me ayudó a estructurar mi mente para pensar la arquitectura del software basándome puramente en el envío de mensajes entre objetos.
* **Trabajo en Equipo y Diseño:** Al ser un desarrollo en equipo, debatir el diagrama de clases y coordinar el código fue fundamental para lograr una solución escalable. Además, incorporamos y documentamos el uso responsable de herramientas de IA para analizar posibles soluciones.

## 🌟 El valor personal del proyecto
Más allá del código, este trabajo me demostró cómo el software puede abstraer problemas reales y sensibles (como la salud pública) para aportar soluciones eficientes. Fue un gran desafío que afianzó mis bases lógicas y mi capacidad de trabajar colaborativamente.

## 👥 Equipo de Desarrollo
Este proyecto fue desarrollado colaborativamente por:
* Williams Condorí
* Eros Faccioli
* Marcos Lupotti
* Miqueas Vera
