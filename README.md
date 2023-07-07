# NotesApp Samples

Este repositorio contiene varios ejemplos con una pequeña aplicación de notas, cuyo objetivo es mostrar la implementación de historias de usuario, pruebas de aceptación y pruebas de integración.

Este es un proyecto de ejemplo para las asignaturas Diseño de Software (EI1039) y Paradigmas de Software (EI1048) del Grado en Ingeniería Informática de la Universitat Jaume I de Castellón,España.

## Descripción de aplicación

La aplicación implementada en los diversos submódulos es una aplicación simple de gestión de notas. Por lo tanto, el **requisito** principal y único de la aplicación es la gestión de notas. A partir de dicho requisito, se definen y especifican las siguientes **historias de usuario**, **escenarios** y **pruebas de aceptación**.

### Historias de usuario

- **HU01**: Como usuario quiero crear una nota con un titulo y una descripción con el fin de recordar algo.
- **HU02**: Como usuario quiero ver las notas que he creado con el fin de leerlas.
- **HU03**: Como usuario quiero editar una nota con el fin de modificar su contenido.
- **HU04**: Como usuario quiero borrar una nota con el fin de eliminarla de mi lista de notas.

### Escenarios y pruebas de aceptación

> **Regla de negocio**: una nota debe tener título, pero puede no tener descripción.

#### HU01

| Escenario | ¿Hay título? | ¿Hay descripción? | ¿Se añade nota? |
|-----------|--------------|-------------------|-----------------|
| E01       |  Sí          | Sí                | Sí              |
| E02       |  Sí          | No                | Sí              |
| E03       |  No          | --                | No              |


##### E01

- **Given**: no hay ninguna nota almacenada.
- **When**: se intenta crear una nota con el título "Test title 1" y la descripción "Test description 1".
- **Then**: se almacena la nota {"title": "Test title 1", "description": "Test description 1", ...}.

##### E03

- **Given**: no hay ninguna nota almacenada.
- **When**: se intenta crear una nota con el título "" y la descripción "Test description 1".
- **Then**: se lanza la excepción EmptyTitleException.

#### HU02

| Escenario | ¿Hay notas? | ¿Se recuperan las notas? |
|-----------|-------------|--------------------------|
| E01       |  No         | Sí                       |
| E02       |  Sí         | Sí                       |


##### E01

- **Given**: no hay ninguna nota almacenada.
- **When**: se intenta acceder al listado de notas.
- **Then**: se obtiene un listado vacio.

##### E02

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1"...}, {"title": "Test title 2", "description": "Test description 2"...}].
- **When**: se intenta acceder al listado de notas.
- **Then**: se obtiene un listado con las notas almacenadas: [{"title": "Test title 1", "description": "Test description 1"...}, {"title": "Test title 2", "description": "Test description 2"...}].


#### HU03

| Escenario | ¿Nota existe? | ¿Datos válidos? | ¿Se actualiza? |
|-----------|---------------|-----------------|----------------|
| E01       |  Sí           | Sí              | Sí             |
| E02       |  Sí           | No              | No             |
| E03       |  No           | --              | No             |


##### E01

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}].
- **When**: se intenta modificar el título de la nota con "id" == "2" a "New note title".
- **Then**: se actualiza el título de la nota con "id" == "2". Notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "New note title", "description": "Test description 2", "id": "2", ...}]

##### E02

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}].
- **When**: se intenta modificar el título de la nota con "id" == "2" a "".
- **Then**: se lanza la excepción EmptyTitleException.

##### E03

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}].
- **When**: se intenta modificar el título de la nota con "id" == "" a "Other title".
- **Then**: se lanza la excepción NoteNotFoundException.


#### HU04

| Escenario | ¿Existe? | ¿Se elimina? |
|-----------|----------|--------------|
| E01       |  Sí      | Sí           |
| E02       |  No      | No           |


##### E01

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}].
- **When**: se intenta eliminar la nota con "id" == "1".
- **Then**: se elimina la nota con "id" == "1". Notas almacenadas: [ {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}]

##### E02

- **Given**: hay dos notas almacenadas: [{"title": "Test title 1", "description": "Test description 1", "id": "1", ...}, {"title": "Test title 2", "description": "Test description 2", "id": "2", ...}].
- **When**: se intenta eliminar la nota con "id" == "".
- **Then**: se lanza la excepción NoteNotFoundException.


## Ejemplos implementados

La siguiente tabla contiene un listado con los ejemplos implementados y las tecnologías empleadas en cada uno:

| Repositorio | Tipo app | Lenguaje/Framework | Testing |
|-------------|----------|--------------------|---------|
| [NotesAppAndroid](https://github.com/matey97/NotesAppAndroid) | Móvil (Android) | Kotlin + Jetpack Compose | JUnit + Mockito |
| [NotesAppNativeScript](https://github.com/matey97/NotesAppNativeScript) | Móvil (Android/iOS) | NativeScript + TypeScript | Karma + Jasmine |
| TODO | TODO | TODO | TODO |

Para más información, consultar el README de cada repositorio.

## Autor

<a href="https://github.com/matey97" title="Miguel Matey Sanz">
  <img src="https://avatars3.githubusercontent.com/u/25453537?s=120" alt="Miguel Matey Sanz" width="120"/>
</a>
