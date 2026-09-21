---
date: '2026-09-21'
description: Aprenda cómo incrustar PDF en hojas de cálculo de Excel con GroupDocs.Merger
  para .NET, mejorando la presentación de datos y la funcionalidad.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Aprenda cómo incrustar PDF en Excel con GroupDocs.Merger para .NET.
  Siga instrucciones paso a paso, vea respuestas rápidas y evite errores comunes.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Cómo incrustar PDF en Excel usando GroupDocs.Merger para .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: Cómo incrustar PDF en Excel usando GroupDocs.Merger para .NET
type: docs
url: /es/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Cómo incrustar PDF en Excel usando GroupDocs.Merger para .NET

## Introducción

Incrustar PDF en Excel le permite mantener los documentos de soporte —como contratos, informes o especificaciones— justo donde viven los datos. Con **GroupDocs.Merger for .NET**, puede agregar objetos OLE a celdas en solo unas pocas líneas de código, convirtiendo una hoja de cálculo simple en un libro de trabajo interactivo y autocontenido. Este tutorial le guía a través de todo lo que necesita saber, desde la instalación hasta la solución de problemas.

**Lo que aprenderá**

- Cómo configurar GroupDocs.Merger para .NET en un proyecto C#  
- Los pasos exactos para incrustar un PDF (o cualquier archivo compatible con OLE) en una celda de Excel  
- Opciones de configuración, consejos de rendimiento y errores comunes  

Confirmemos que tiene todo listo antes de comenzar.

## Respuestas rápidas
- **¿Puedo incrustar cualquier tipo de archivo?** Sí—cualquier formato compatible como objeto OLE (PDF, Word, imagen, etc.).  
- **¿Necesito una licencia para desarrollo?** Una prueba gratuita funciona para pruebas; se requiere una licencia permanente para producción.  
- **¿Qué versiones de .NET son compatibles?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **¿Aumentará drásticamente el tamaño del archivo Excel?** Solo por el tamaño del documento incrustado; mantenga los archivos por debajo de unos pocos MB para obtener el mejor rendimiento.  
- **¿Hay un límite en la cantidad de objetos OLE?** Prácticamente ninguno, pero libros de trabajo muy grandes pueden afectar el tiempo de carga.

## ¿Qué es incrustar PDF en Excel?

Incrustar PDF en Excel inserta el PDF completo como un objeto OLE que puede abrirse directamente desde la hoja de cálculo. Los usuarios hacen clic en el ícono y ven el documento original sin salir de Excel. Este enfoque preserva el diseño original, permite una referencia rápida y elimina la necesidad de gestionar archivos separados. El PDF incrustado se comporta como cualquier otro objeto OLE, permitiendo a los usuarios hacer doble clic en el ícono para lanzar el visor de PDF mientras permanecen dentro del entorno de Excel.

## ¿Por qué incrustar objetos OLE en Excel?

GroupDocs.Merger soporta **120+ input and output formats** y puede incrustar objetos sin cargar todo el archivo en memoria, lo que permite un procesamiento rápido de PDFs de cientos de páginas. Esto reduce la necesidad de repositorios de archivos separados y mantiene los datos relacionados juntos. También simplifica el control de versiones y asegura que toda la documentación relevante viaje con el libro de trabajo, mejorando la colaboración entre equipos.

## Requisitos previos

- **GroupDocs.Merger for .NET** (latest NuGet package)  
- **.NET Framework** 4.5+ **or** **.NET Core/5+/6+**  
- Visual Studio 2022 or later  
- Basic C# knowledge and familiarity with file I/O  

## Configuración de GroupDocs.Merger para .NET

### Instalación

Add the package using one of the following methods:

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Busque “GroupDocs.Merger” e instale la última versión.

### Obtención de licencia

1. **Prueba gratuita** – pruebe la biblioteca sin costo.  
2. **Licencia temporal** – solicite una licencia temporal en la [página de licencia temporal](https://purchase.groupdocs.com/temporary-license/).  
3. **Compra** – considere comprar una licencia en la [página de compra de GroupDocs](https://purchase.groupdocs.com/buy).

### Inicialización básica

`Merger` es el punto de entrada para todas las operaciones.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## ¿Cómo incrustar objetos OLE en Excel?

Load your source workbook, configure the OLE options, and let `Merger` insert the object. The following sections give you a concise, ready‑to‑run workflow.

### Descripción general de la función
Incrustar objetos OLE le permite almacenar un PDF completo dentro de una celda, preservando el diseño original y habilitando el acceso con un solo clic desde Excel.

### Implementación paso a paso

#### 1. Establecer rutas y número de página
Especifique la hoja de cálculo, el archivo a incrustar y la dirección de la celda de destino.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Configurar OleSpreadsheetOptions
`OleSpreadsheetOptions` defines where the OLE object will be placed in the worksheet and how its icon appears.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Inicializar Merger y realizar la incrustación
The `Merger` class handles the actual insertion. After the call, the workbook contains the OLE icon.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Consejos comunes de solución de problemas
- Verifique que todas las rutas de archivo sean absolutas o estén resueltas correctamente en relación con el ejecutable.  
- Asegúrese de que el número de página que especifica exista en el PDF de origen; de lo contrario se lanzará una excepción.  
- Si el objeto incrustado no se muestra, confirme que la versión de Excel de destino admite OLE (la mayoría de las versiones modernas lo hacen).

## Aplicaciones prácticas

Incrustar PDF en Excel es útil para:

1. **Informes financieros** – adjunte estados auditados directamente junto a las tablas resumidas.  
2. **Documentación de proyecto** – mantenga especificaciones de diseño, análisis de riesgos o contratos dentro de un rastreador maestro.  
3. **Paneles de entrenamiento** – incruste manuales de usuario o PDFs de políticas para referencia rápida por el personal.

## Consideraciones de rendimiento

- **Tamaño de archivo** – mantenga los PDFs incrustados por debajo de 5 MB para evitar inflar el libro de trabajo.  
- **Uso de memoria** – `GroupDocs.Merger` transmite datos, por lo que el consumo de memoria se mantiene bajo incluso con archivos de origen grandes.  
- **Liberar objetos** – siempre llame a `Dispose()` en las instancias de `Merger` para liberar los manejadores de archivo rápidamente.

## Preguntas frecuentes

**P: ¿Qué es un objeto OLE?**  
R: Un objeto OLE (Object Linking and Embedding) almacena otro archivo (PDF, Word, imagen, etc.) dentro de un documento anfitrión, permitiendo la edición o apertura in situ.

**P: ¿Puedo incrustar objetos OLE en otros formatos de Office?**  
R: Sí—GroupDocs.Merger también admite archivos Word, PowerPoint y Visio.

**P: ¿Cómo manejo PDFs protegidos con contraseña?**  
R: Proporcione la contraseña al crear la instancia `OleSpreadsheetOptions`; la biblioteca descifrará el archivo automáticamente.

**P: ¿Hay una limitación de tamaño para los PDFs incrustados?**  
R: Técnicamente no hay un límite estricto, pero los archivos mayores de 10 MB pueden aumentar notablemente el tiempo de carga del libro.

**P: ¿Dónde puedo encontrar más ejemplos?**  
R: Visite la [Documentación oficial de GroupDocs](https://docs.groupdocs.com/merger/net/) para obtener ejemplos de código adicionales y referencias de API.

## Recursos adicionales
- **Documentation**: [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **API reference**: [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Downloads**: [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **License purchase**: [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Free trial**: [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Temporary license**: [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Support forum**: [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-09-21  
**Tested with:** GroupDocs.Merger 23.12 for .NET  
**Author:** GroupDocs

## Tutoriales relacionados

- [Incrustar PDF como OLE en PowerPoint usando GroupDocs.Merger para .NET: Guía paso a paso](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Incrustar PDF en Word usando GroupDocs.Merger para .NET: Guía paso a paso](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Cargar PDF desde URL en .NET usando GroupDocs.Merger: Guía completa](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}