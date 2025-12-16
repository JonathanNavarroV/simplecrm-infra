## Uso de namespaces y nombres de tipos

Al generar o completar código en C#:

* No utilices nombres completamente calificados (fully qualified names) en el cuerpo del código cuando exista o pueda existir un using adecuado.
* Prioriza siempre:

  * Agregar o reutilizar using explícitos al inicio del archivo.
  * Usar nombres de tipos y miembros en su forma corta y legible.

Ejemplos:

Evitar:

builder.HasData(Infrastructure.Persistence.SeedData.RolePermissions.SeedData);

Preferir:

using Infrastructure.Persistence.SeedData;

builder.HasData(RolePermissions.SeedData);

Excepciones permitidas:

* Cuando exista ambigüedad real de nombres que no pueda resolverse con using.
* En código estrictamente generado, reflejado o experimental.

El objetivo es:

* Mejorar legibilidad.
* Reducir ruido visual.
* Mantener consistencia con Clean Architecture y código mantenible.

## Reutilizar código existente antes de crear algo nuevo

Siempre que propongas una solución, primero debes buscar y reutilizar código que ya exista en este proyecto.

* Prioriza buscar implementaciones similares:

  * En el mismo archivo donde se está trabajando.
  * En archivos del mismo directorio.
  * En módulos, servicios o componentes relacionados dentro del proyecto.

Solo crea nuevas funciones, servicios, componentes o utilidades cuando no exista nada razonablemente reutilizable o adaptable.

No preguntes al usuario si ya existe algo similar: realiza tú mismo la validación usando el contexto disponible y actúa en consecuencia.

## Idioma de comentarios

Todos los comentarios en el código deben estar escritos **exclusivamente en español**.

* Incluye comentarios de clase, método y bloques relevantes de lógica.
* No utilices comentarios en inglés, incluso si el código, librerías o frameworks están en inglés.
* Mantén un lenguaje claro, técnico y coherente con el dominio del proyecto.

Esta regla aplica a:

* Código de producción.
* Configuraciones (por ejemplo, EF Core, validaciones, mapeos).
* Código de ejemplo o snippets incluidos en el proyecto.

## Reglas para commits

Cuando recomiendes realizar un commit, debes seguir este procedimiento:

1. Asume siempre que el usuario utilizará:

   * git add . para agregar todos los cambios al staging area.

2. Antes de sugerir el mensaje de commit:

   * Revisa el contexto de los cambios realizados (diff disponible en el entorno de desarrollo).
   * Analiza la intención del cambio para generar un mensaje coherente y descriptivo.

3. Mensajes de commit:

   * Deben ser en español.
   * Deben ser claros, breves y descriptivos, como un título.
   * No usar prefijos como feat, fix, chore ni otros similares.
   * No incluir cuerpo del commit salvo que el usuario lo solicite explícitamente.

Ejemplos válidos:

* Actualizar validaciones del formulario de cliente
* Agregar componente para edición de contactos
* Corregir cálculo de totales en el modal de recursos
