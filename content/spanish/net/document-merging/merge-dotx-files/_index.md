---
title: Fusionar archivos DOTX
linktitle: Fusionar archivos DOTX
second_title: API GroupDocs.Merger .NET
description: Aprenda a fusionar archivos DOTX en .NET usando GroupDocs.Merger sin esfuerzo. Mejore sus capacidades de manipulación de documentos.
weight: 15
url: /es/net/document-merging/merge-dotx-files/
type: docs
---
# Fusionar archivos DOTX

## Introducción
En este tutorial, exploraremos cómo fusionar archivos DOTX (plantilla de Word) usando GroupDocs.Merger para .NET. GroupDocs.Merger es una potente API que permite a los desarrolladores manipular varios formatos de documentos sin problemas dentro de aplicaciones .NET. Al aprovechar esta API, puede fusionar de manera eficiente varios archivos DOTX en un solo documento con solo unas pocas líneas de código.
## Requisitos previos
Antes de sumergirse en el tutorial, asegúrese de tener lo siguiente:
- Visual Studio instalado en su máquina
- .NET SDK (versión compatible) instalado
-  GroupDocs.Merger para .NET instalado (consulte la[guía de instalación](https://tutorials.groupdocs.com/merger/net/) para detalles)
- Conocimientos básicos de programación en C#.

## Importar espacios de nombres
Para comenzar, importe los espacios de nombres necesarios a su proyecto C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Paso 1: configurar el directorio de salida y el nombre del archivo
Primero, defina la ruta del directorio de salida y el nombre del archivo DOTX fusionado.
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.dotx");
```
 Reemplazar`"YourOutputDirectory"` con la ruta donde desea guardar el archivo DOTX fusionado.
## Paso 2: fusionar archivos DOTX
A continuación, utilice GroupDocs.Merger para fusionar varios archivos DOTX en un solo documento.
```csharp
// Cargue el archivo DOTX de origen
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Agregue otro archivo DOTX para fusionar
    merger.Join("Your Sample File");
    
    // Fusionar archivos DOTX y guardar el resultado
    merger.Save(outputFile);
}
Console.WriteLine("\nDOTX files merge completed successfully. \nCheck output in {0}", outputFolder);
```
En este fragmento de código:
- `"Your Sample File"` y`"Your Sample File"` representan rutas a los archivos DOTX que desea fusionar. Reemplácelos con las rutas de archivos reales.
- `merger.Join()` se utiliza para agregar archivos DOTX adicionales a la fusión.
- `merger.Save()` combina los archivos DOTX y guarda el resultado combinado en el lugar especificado`outputFile` camino.

## Conclusión
En este tutorial, cubrimos cómo fusionar archivos DOTX usando GroupDocs.Merger para .NET. Si sigue estos pasos y aprovecha el poder de GroupDocs.Merger, podrá manipular eficientemente archivos de plantillas de Word dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### ¿Puede GroupDocs.Merger fusionar otros formatos de documentos además de DOTX?
Sí, GroupDocs.Merger admite la combinación de varios formatos de documentos como DOCX, XLSX, PPTX, PDF y más.
### ¿GroupDocs.Merger es compatible con .NET Core?
Sí, GroupDocs.Merger es compatible tanto con .NET Framework como con .NET Core.
### ¿Dónde puedo encontrar soporte o documentación adicional para GroupDocs.Merger?
 Puedes consultar el[Documentación de GroupDocs.Merger](https://tutorials.groupdocs.com/merger/net/) para obtener referencias detalladas de API y ejemplos de uso.
### ¿GroupDocs.Merger ofrece una prueba gratuita?
 Sí, puedes acceder a un[versión de prueba gratuita](https://releases.groupdocs.com/) para evaluar GroupDocs.Merger.
### ¿Cómo puedo comprar una licencia para GroupDocs.Merger?
 Puede adquirir una licencia en el[Sitio web de GroupDocs](https://purchase.groupdocs.com/buy) según sus requisitos de uso.