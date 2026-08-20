---
date: '2026-08-20'
description: Aprenda a combinar PDFs con bookmarks usando GroupDocs.Merger for .NET,
  incluyendo setup, code examples y best practices para combinar PDF documents.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Aprenda a combinar PDFs con bookmarks usando GroupDocs.Merger for
  .NET. Siga el código step‑by‑step para combinar PDF documents mientras se preserva
  navigation.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Cómo combinar PDFs con bookmarks usando GroupDocs.Merger for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Cómo combinar PDFs con bookmarks usando GroupDocs.Merger for .NET
type: docs
url: /es/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Cómo combinar PDFs con marcadores usando GroupDocs.Merger para .NET

Combinar varios archivos PDF mientras se conservan sus marcadores originales puede ahorrarle horas de reorganización manual. En este tutorial aprenderá cómo **combinar PDFs con marcadores** usando GroupDocs.Merger para .NET, desde la configuración del proyecto hasta un ejemplo de código completo y listo para producción.

## Respuestas rápidas
- **¿Qué biblioteca admite fusiones que conservan los marcadores?** GroupDocs.Merger para .NET.  
- **¿Puedo combinar más de dos PDFs a la vez?** Sí, agregue tantos archivos de origen como necesite.  
- **¿Necesito una licencia para desarrollo?** Una prueba gratuita funciona para pruebas; se requiere una licencia permanente para producción.  
- **¿Se admite .NET Core?** Absolutamente, la biblioteca funciona con .NET Core, .NET 5/6 y el .NET Framework completo.  
- **¿Cuál es el tamaño máximo de archivo que puede manejar?** Hasta 2 GB por documento, procesado sin cargar todo el archivo en memoria.

## ¿Qué es combinar PDFs con marcadores?
**Combinar PDFs con marcadores** significa tomar varios documentos PDF y combinarlos en un solo archivo mientras se mantiene intacta la jerarquía de marcadores de cada documento de origen. El PDF resultante conserva la estructura de navegación original, permitiendo a los lectores saltar directamente a las secciones que provienen de cada archivo individual, lo cual es esencial para informes extensos o manuales compilados.

## ¿Por qué combinar PDFs con marcadores?
Conservar los marcadores al combinar PDFs mejora la navegación en documentos consolidados, permitiendo a los usuarios localizar rápidamente capítulos o secciones específicas sin desplazarse por todo el archivo. GroupDocs.Merger mantiene la jerarquía de esquema original, reduce el esfuerzo de reorganización manual y admite archivos grandes de hasta 2 GB mientras usa una memoria mínima, lo que lo hace ideal para flujos de trabajo a escala empresarial.

## Requisitos previos
- **SDK de .NET Core** (3.1 o posterior) o **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** o cualquier IDE que admita desarrollo .NET.  
- Conocimientos básicos de C# y familiaridad con entrada/salida de archivos.  

## Configuración de GroupDocs.Merger para .NET

### Instalación
Agregue la biblioteca a su proyecto con uno de los siguientes comandos:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**NuGet Package Manager UI:**  
- Search for “GroupDocs.Merger” and install the latest version.

### Obtención de licencia
- **Prueba gratuita:** Descargue desde la página [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Licencia temporal:** Obtenga una a través de la [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Licencia completa:** Compre en la [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).  

### Inicialización básica
La clase `Merger` es el punto de entrada para todas las operaciones de combinación.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Este espacio de nombres le brinda acceso al conjunto completo de funciones de manipulación de PDF.

## Cómo combinar PDFs con marcadores en .NET

Cargue su PDF principal, configure el manejo de marcadores, añada archivos adicionales y guarde el resultado, todo en unas pocas líneas concisas de código.

**Respuesta directa (40‑70 palabras):**  
Cree una instancia de `Merger` con el primer PDF, habilite `PdfJoinOptions.UseBookmarks`, añada cada PDF subsiguiente mediante `Join` y llame a `Save` para escribir el archivo combinado. Este enfoque conserva cada jerarquía de marcadores original y se ejecuta en una sola pasada, minimizando el consumo de memoria.

### Paso 1: definir rutas de directorios
Configure las carpetas de origen y salida para que el código pueda localizar los PDFs que desea combinar.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Paso 2: cargar el PDF principal
`Merger` representa el documento principal al que añadirá los demás.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Paso 3: configurar opciones de preservación de marcadores
`PdfJoinOptions` controla cómo se comporta la combinación; la bandera `UseBookmarks` indica al motor que conserve los marcadores existentes.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Paso 4: añadir PDFs adicionales
Llame a `Join` para cada archivo extra. La biblioteca combina automáticamente sus árboles de marcadores bajo el esquema del documento principal.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Paso 5: guardar el PDF combinado
Especifique la ruta y el formato de salida; la biblioteca escribe un único PDF que conserva todas las entradas de marcadores.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Problemas comunes y soluciones
- **Marcadores faltantes:** Verifique `UseBookmarks = true` en `PdfJoinOptions`.  
- **Errores de ruta:** Use `Path.Combine` y verifique la existencia del archivo antes de combinar.  
- **Los archivos grandes provocan picos de memoria:** Procese los PDFs secuencialmente y deseche el objeto `Merger` después de cada guardado.

## Aplicaciones prácticas
1. **Consolidar informes financieros** – mantenga las secciones trimestrales accesibles instantáneamente mediante marcadores.  
2. **Paquetes de material de cursos** – combine PDFs de conferencias conservando la navegación por capítulos para los estudiantes.  
3. **Paquetes de documentación de proyectos** – combine especificaciones de diseño, planes de prueba y notas de lanzamiento en un solo archivo buscable.  

## Consideraciones de rendimiento
- Procese un archivo a la vez al combinar más de 20 PDFs para mantener bajo el uso de RAM.  
- Use el runtime .NET más reciente (p. ej., .NET 6) para una compilación JIT y eficiencia de recolección de basura óptimas.  
- Para PDFs mayores de 500 MB, habilite el modo de transmisión mediante `MergerSettings` para evitar cargar todo el documento en memoria.

## Preguntas frecuentes

**Q: ¿Qué es GroupDocs.Merger?**  
A: GroupDocs.Merger es una biblioteca .NET que le permite combinar, dividir, rotar y manipular de otras formas PDFs y otros formatos de documentos de forma programática.

**Q: ¿Puedo combinar más de dos archivos PDF a la vez?**  
A: Sí, llame a `Join` repetidamente o pase una colección de rutas de archivo para combinar cualquier número de PDFs en una sola operación.

**Q: ¿Cómo manejo la licencia para uso en producción?**  
A: Obtenga una licencia permanente en la página de compra de GroupDocs; la licencia de prueba solo funciona para evaluación y expira después de 30 días.

**Q: Mi PDF combinado no muestra marcadores—¿qué salió mal?**  
A: Asegúrese de que `PdfJoinOptions.UseBookmarks` esté configurado en `true` y de que cada PDF de origen realmente contenga marcadores antes de combinar.

**Q: ¿Es la biblioteca compatible con .NET Core y .NET Framework?**  
A: Absolutamente, admite .NET Core 3.1+, .NET 5/6 y el .NET Framework completo 4.6.1+.

## Recursos
- [Documentación](https://docs.groupdocs.com/merger/net/)  
- [Referencia API](https://reference.groupdocs.com/merger/net/)  
- [Descargar GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Comprar licencia](https://purchase.groupdocs.com/buy)  
- [Versión de prueba gratuita](https://releases.groupdocs.com/merger/net/)  
- [Licencia temporal](https://purchase.groupdocs.com/temporary-license/)  
- [Foro de soporte](https://forum.groupdocs.com/c/merger/)  

---

**Última actualización:** 2026-08-20  
**Probado con:** GroupDocs.Merger 23.11 para .NET  
**Autor:** GroupDocs

## Tutoriales relacionados

- [Cómo combinar páginas PDF específicas con GroupDocs.Merger para .NET: Guía completa](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Cómo unir documentos fácilmente usando GroupDocs.Merger para .NET: Guía completa](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Añadir adjuntos a PDFs usando GroupDocs.Merger para .NET: Guía paso a paso](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)