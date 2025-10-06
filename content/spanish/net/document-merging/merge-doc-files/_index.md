---
title: Fusionar archivos DOC con GroupDocs.Merger para .NET
linktitle: Fusionar archivos DOC con GroupDocs.Merger para .NET
second_title: API GroupDocs.Merger .NET
description: Aprenda a fusionar archivos DOC mediante programación utilizando GroupDocs.Merger para .NET. Siga nuestra guía paso a paso para combinar sin problemas varios documentos en uno.
weight: 10
url: /es/net/document-merging/merge-doc-files/
type: docs
---
# Fusionar archivos DOC con GroupDocs.Merger para .NET

## Introducción
En este tutorial, exploraremos cómo fusionar archivos DOC usando GroupDocs.Merger para .NET. GroupDocs.Merger para .NET es una potente API que permite a los desarrolladores combinar, dividir y manipular varios formatos de documentos mediante programación. Al aprovechar esta API, puede fusionar sin problemas varios archivos DOC en un solo documento. Le proporcionaremos instrucciones paso a paso para guiarlo a través del proceso de combinación de archivos DOC utilizando GroupDocs.Merger para .NET.
## Requisitos previos
Antes de comenzar, asegúrese de tener configurados los siguientes requisitos previos:
1. Visual Studio: instale Visual Studio en su máquina de desarrollo.
2.  GroupDocs.Merger para .NET: obtenga la biblioteca GroupDocs.Merger para .NET. Puedes descargarlo desde el[sitio web](https://releases.groupdocs.com/merger/net/).
3. Conocimiento de C#: Comprensión básica del lenguaje de programación C#.
## Importar espacios de nombres
Para comenzar a trabajar con GroupDocs.Merger para .NET, importe los espacios de nombres necesarios a su proyecto C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Paso 1: configurar el directorio de salida
Comience especificando el directorio de salida donde se guardará el archivo DOC combinado:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
 Reemplazar`"Your Output Directory"` con la ruta a la carpeta de salida deseada.
## Paso 2: cargar archivos DOC de origen
A continuación, cargue los archivos DOC de origen que desea fusionar utilizando GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // Agregue otro archivo DOC para fusionar
    merger.Join("Your Sample Document File 2");
    // Fusionar archivos DOC y guardar el resultado
    merger.Save(outputFile);
}
```
En este fragmento de código:
- `"Your Sample Document File"` y`"Your Sample Document File 2"` representan las rutas a los archivos DOC que desea fusionar.
- `merger.Join(...)` se utiliza para agregar otro archivo DOC a la operación de fusión.
- `merger.Save(outputFile)` combina los archivos DOC cargados y guarda el documento combinado en el archivo de salida especificado (`merged.doc`).
 Asegúrese de reemplazar`"Your Sample Document File"` y`"Your Sample Document File 2"` con las rutas reales a sus archivos DOC.
## Conclusión
En este tutorial, cubrimos el proceso de fusionar archivos DOC usando GroupDocs.Merger para .NET. Si sigue los pasos descritos anteriormente, puede combinar de manera efectiva varios archivos DOC en un solo documento mediante programación. GroupDocs.Merger para .NET proporciona una manera sencilla y eficiente de manipular formatos de documentos dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### ¿Puede GroupDocs.Merger para .NET manejar otros formatos de documentos además de DOC?
Sí, GroupDocs.Merger para .NET admite la combinación de varios formatos de documentos, como DOCX, PDF, XLSX, PPTX y más.
### ¿GroupDocs.Merger para .NET es compatible con .NET Core?
Sí, GroupDocs.Merger para .NET es compatible con .NET Core y .NET Framework.
### ¿GroupDocs.Merger para .NET requiere una licencia para uso comercial?
 Sí, se requiere una licencia válida para uso comercial. Puede obtener una licencia de[Documentos de grupo](https://purchase.groupdocs.com/buy).
### ¿Puedo probar GroupDocs.Merger para .NET gratis?
 Sí, puedes explorar GroupDocs.Merger para .NET con una prueba gratuita disponible[aquí](https://releases.groupdocs.com/).
### ¿Dónde puedo obtener soporte técnico para GroupDocs.Merger para .NET?
 Para asistencia técnica y apoyo comunitario, visite el[Foro de documentos de grupo](https://forum.groupdocs.com/c/merger/32).