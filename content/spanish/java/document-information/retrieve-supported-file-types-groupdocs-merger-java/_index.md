---
date: '2026-07-06'
description: Aprenda cómo recuperar los tipos de archivo compatibles con GroupDocs.Merger
  para Java, verifique las extensiones compatibles java e integre la lista en su flujo
  de trabajo.
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: Formatos compatibles de GroupDocs.Merger – Recuperar tipos en Java
type: docs
url: /es/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# Formatos admitidos por GroupDocs.Merger – Recuperar tipos en Java

Trabajar con una amplia variedad de formatos de documentos en Java puede convertirse rápidamente en un dolor de cabeza si no sabes cuáles admite realmente tu biblioteca. **GroupDocs.Merger supported formats** te brinda un punto de referencia confiable, permitiéndote validar cargas, evitar errores en tiempo de ejecución y diseñar flujos de trabajo de gestión de documentos más inteligentes. En este tutorial verás exactamente cómo obtener la lista de tipos de archivo admitidos usando GroupDocs.Merger para Java, por qué es importante y cómo incorporar la información en aplicaciones del mundo real.

### Respuestas rápidas
- **¿Qué hace “retrieve supported file types”?**  
  Devuelve una lista de todos los formatos de documento que GroupDocs.Merger puede procesar.
- **¿Qué método proporciona la lista?**  
  `FileType.getSupportedFileTypes()` from the `com.groupdocs.merger.domain` package.
- **¿Necesito una licencia para llamar a este método?**  
  Se requiere una licencia de prueba o completa para uso en producción; el método funciona en modo de evaluación.
- **¿Puedo filtrar la lista solo para las extensiones que necesito?**  
  Sí – itera la lista devuelta y conserva las extensiones que te interesan.
- **¿Esta operación es pesada en cuanto a rendimiento?**  
  No, simplemente lee una colección estática, por lo que se ejecuta instantáneamente.

## ¿Cuáles son los formatos admitidos por GroupDocs.Merger?

GroupDocs.Merger admite **más de 70** formatos de entrada y salida —incluidos PDF, DOCX, PPTX, XLSX, HTML y tipos de imagen comunes— lo que te permite trabajar con prácticamente cualquier documento empresarial. La tabla de formatos de la biblioteca se almacena internamente como una colección estática, por lo que obtenerla es una operación O(1) que se completa en unos pocos milisegundos, incluso en hardware modesto.

## ¿Cómo puedo comprobar las extensiones admitidas en Java?

Llama al método estático `FileType.getSupportedFileTypes()`, luego recorre la colección devuelta para leer cada extensión. Esta llamada de una sola línea te proporciona un `List<FileType>` listo para usar que puedes filtrar, mostrar o almacenar para validaciones posteriores.

## ¿Por qué debería recuperar los tipos de archivo admitidos antes de procesar?

Conocer la lista exacta de formatos evita excepciones evitables, reduce la necesidad de codificación defensiva y te permite presentar a los usuarios un mensaje claro de “tipos de archivo permitidos”. También te permite crear componentes de UI dinámicos —como filtros de selector de archivos— que solo muestran extensiones compatibles, mejorando la experiencia general del usuario.

## Requisitos previos

- **Java Development Kit (JDK):** Se recomienda la versión 8 o superior.  
- **Integrated Development Environment (IDE):** Cualquier IDE como IntelliJ IDEA o Eclipse funcionará.  
- **GroupDocs.Merger Library:** Incluye esta biblioteca en las dependencias de tu proyecto.  

Familiaridad con conceptos básicos de programación Java y experiencia trabajando con bibliotecas en un entorno Maven o Gradle también son útiles. Si eres nuevo en estas herramientas, considera revisar su documentación primero.

## Configuración de GroupDocs.Merger para Java

Para usar GroupDocs.Merger para Java, configura la biblioteca en tu proyecto usando Maven, Gradle o descargándola directamente desde el sitio oficial.

### Instalación con Maven

Add the following dependency to your `pom.xml` file:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Instalación con Gradle

Include this line in your `build.gradle` file:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Descarga directa

Alternativamente, descarga la última versión desde [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Pasos para obtener la licencia
1. **Free Trial:** Comienza con una prueba gratuita para explorar las funciones de la biblioteca.  
2. **Temporary License:** Obtén una licencia temporal si necesitas acceso ampliado sin limitaciones.  
3. **Purchase:** Considera comprar una licencia completa para uso a largo plazo.

## Inicialización y configuración básicas

To initialize GroupDocs.Merger in your Java application, import the necessary classes:

```java
import com.groupdocs.merger.domain.FileType;
```

Ahora, pasemos a implementar la funcionalidad que recupera los tipos de archivo admitidos.

## ¿Qué es la clase FileType?

La clase `FileType` es el modelo central en GroupDocs.Merger que representa un único formato de documento, exponiendo su extensión, tipo MIME y un nombre amigable para mostrar. Interactúas con esta clase cuando llamas a `FileType.getSupportedFileTypes()` para obtener el catálogo completo de formatos.

## ¿Cómo recuperar los tipos de archivo admitidos?

Para obtener los formatos admitidos, simplemente llama al método estático `FileType.getSupportedFileTypes()` provisto por la biblioteca GroupDocs.Merger. Esta llamada devuelve un `List<FileType>` que contiene cada formato que la biblioteca puede manejar. La operación es ligera y puede ejecutarse al iniciar la aplicación o siempre que necesites validar cargas de archivos.

### Paso 1: Obtener los tipos de archivo admitidos

Primero, recupera la lista de tipos de archivo admitidos desde la clase `FileType`:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

Este método devuelve una lista que contiene todos los tipos de archivo que GroupDocs.Merger admite.

### Paso 2: Mostrar extensiones admitidas

A continuación, itera cada objeto `FileType` e imprime su extensión. Esta es la parte donde **mostramos extensiones admitidas** para desarrolladores o usuarios finales:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

El bucle recorre cada tipo de archivo admitido y muestra su extensión en la consola.

### Paso 3: Mensaje de confirmación

Finalmente, muestra un mensaje de confirmación indicando que la recuperación fue exitosa:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Aplicaciones prácticas

Comprender los tipos de archivo admitidos es esencial para diversas aplicaciones:

1. **Document Management Systems:** Categoriza automáticamente los documentos según su tipo.  
2. **File Conversion Tools:** Asegura la compatibilidad antes de convertir archivos entre formatos.  
3. **Merging Applications:** Valida los archivos de entrada antes de combinar para evitar errores.  

La integración con otros sistemas —como almacenamiento en la nube o servicios de procesamiento de documentos— puede mejorar aún más la funcionalidad.

## Consideraciones de rendimiento

Al trabajar con GroupDocs.Merger en Java, considera los siguientes consejos de rendimiento:

- **Optimize Memory Usage:** Libera los objetos cuando ya no sean necesarios.  
- **Batch Processing:** Procesa archivos en lotes para reducir el consumo de recursos.  
- **Asynchronous Operations:** Utiliza métodos asíncronos para operaciones no bloqueantes.  

## Problemas comunes y soluciones

- **Dependency Issues:** Verifica que las dependencias de Maven o Gradle estén declaradas correctamente; versiones incompatibles provocan errores de clase no encontrada.  
- **Library Version:** Siempre usa la última versión de GroupDocs.Merger para beneficiarte de los formatos añadidos recientemente y correcciones de errores.  
- **License Errors:** Si ves excepciones de licencia, confirma que el archivo de licencia de prueba o permanente está referenciado correctamente en tu código.

## Preguntas frecuentes

**Q: ¿Qué es GroupDocs.Merger para Java?**  
A: Es una biblioteca Java que permite combinar, dividir y convertir una amplia gama de formatos de documentos sin requerir Microsoft Office.

**Q: ¿Cómo empiezo con GroupDocs.Merger?**  
A: Añade la dependencia Maven o Gradle, obtén una licencia de prueba o completa, e inicializa la biblioteca como se muestra en la sección de configuración.

**Q: ¿Puedo usar GroupDocs.Merger de forma gratuita?**  
A: Sí, hay una prueba gratuita disponible para evaluación; se requiere una licencia completa para implementaciones en producción.

**Q: ¿Qué tipos de archivo admite GroupDocs.Merger?**  
A: Usa el método `FileType.getSupportedFileTypes()` para obtener una lista de **más de 70** formatos admitidos, incluidos PDF, DOCX, PPTX, XLSX, HTML y tipos de imagen.

**Q: ¿Cómo manejo los tipos de archivo no admitidos?**  
A: Valida las cargas contra la lista de formatos admitidos antes de procesar; rechaza o convierte los archivos no admitidos temprano para evitar errores en tiempo de ejecución.

**Q: ¿Puedo filtrar la lista para mostrar solo las extensiones que necesito?**  
A: Sí. Después de llamar a `getSupportedFileTypes()`, recorre la lista y conserva solo las extensiones que te interesan.

**Q: ¿Se requiere una licencia para compilaciones de desarrollo?**  
A: Una licencia de prueba funciona para desarrollo y pruebas; se requiere una licencia completa para uso comercial en producción.

**Q: ¿Este método afecta el tiempo de inicio de la aplicación?**  
A: No. La lista de tipos de archivo admitidos es estática, por lo que la recuperación es prácticamente instantánea.

**Q: ¿Cambiará la lista con nuevas versiones de la biblioteca?**  
A: Las nuevas versiones pueden agregar o deprecar formatos; siempre usa la versión más reciente para obtener la lista más actualizada.

## Recursos
- [Documentación](https://docs.groupdocs.com/merger/java/)
- [Referencia de API](https://reference.groupdocs.com/merger/java/)
- [Descarga](https://releases.groupdocs.com/merger/java/)
- [Compra](https://purchase.groupdocs.com/buy)
- [Prueba gratuita](https://releases.groupdocs.com/merger/java/)
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/)
- [Soporte](https://forum.groupdocs.com/c/merger/) 

Siéntete libre de explorar estos recursos para obtener información más detallada y soporte. ¡Feliz codificación!

---

**Última actualización:** 2026-07-06  
**Probado con:** GroupDocs.Merger última versión (a partir de 2026)  
**Autor:** GroupDocs  

## Tutoriales relacionados

- [GroupDocs.Merger para Java: Guía de configuración de licencia y verificación de existencia de archivo](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Cargar documento local Java usando GroupDocs.Merger – Guía](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Combinar páginas específicas Java – Tutoriales de unión de documentos para GroupDocs.Merger](/merger/java/document-joining/)