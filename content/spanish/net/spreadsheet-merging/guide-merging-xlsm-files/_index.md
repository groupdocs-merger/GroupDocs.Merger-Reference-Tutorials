---
title: Guía para fusionar archivos XLSM
linktitle: Guía para fusionar archivos XLSM
second_title: API GroupDocs.Merger .NET
description: Combine archivos XLSM sin problemas con GroupDocs.Merger para .NET. Combine eficientemente libros de Excel mediante programación. Mejore sus capacidades de manipulación de documentos.
weight: 13
url: /es/net/spreadsheet-merging/guide-merging-xlsm-files/
---

# Guía para fusionar archivos XLSM

## Introducción
En este tutorial, exploraremos cómo fusionar archivos XLSM (libro de trabajo habilitado para macros de Excel). GroupDocs.Merger es una poderosa biblioteca que permite a los desarrolladores manipular formatos de documentos, incluida la combinación, división y modificación de archivos mediante programación.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
-  GroupDocs.Merger para .NET: descargue e instale la biblioteca desde[aquí](https://releases.groupdocs.com/merger/net/).
- Entorno de desarrollo: configure Visual Studio o cualquier entorno de desarrollo .NET compatible.
- Archivos XLSM: prepare los archivos XLSM que desea fusionar.

## Importar espacios de nombres
Primero, incluya los espacios de nombres necesarios en su proyecto .NET:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Paso 1: definir la carpeta de salida y el nombre del archivo
Comience definiendo la carpeta de salida y el nombre del archivo XLSM combinado:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Paso 2: cargar y fusionar archivos XLSM
A continuación, cargue los archivos XLSM de origen y combínelos en un solo archivo:
```csharp
// Cargue el archivo XLSM de origen
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Agregue otro archivo XLSM para fusionar
    merger.Join("Your Sample File");
    // Fusionar archivos XLSM y guardar el resultado
    merger.Save(outputFile);
}
```
## Paso 3: Verifique la finalización de la fusión
Finalmente, notifique al usuario sobre la finalización exitosa de la fusión y muestre la ruta de salida:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
Ha aprendido cómo fusionar archivos XLSM mediante programación. Esta biblioteca simplifica las tareas de manipulación de documentos, permitiendo una combinación eficiente de archivos dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### ¿Puede GroupDocs.Merger manejar archivos XLSM de gran tamaño?
Sí, GroupDocs.Merger maneja eficientemente archivos XLSM de gran tamaño sin problemas de rendimiento.
### ¿GroupDocs.Merger admite otros formatos de archivo además de XLSM?
Sí, GroupDocs.Merger admite varios formatos de documentos como DOCX, PDF, PPTX y más.
### ¿GroupDocs.Merger es compatible con aplicaciones .NET Core?
Sí, GroupDocs.Merger es compatible con los entornos .NET Framework y .NET Core.
### ¿Puedo fusionar archivos XLSM cifrados usando GroupDocs.Merger?
Sí, GroupDocs.Merger admite la combinación de archivos XLSM cifrados con las credenciales correctas.
### ¿GroupDocs.Merger proporciona capacidades de procesamiento por lotes?
Sí, GroupDocs.Merger permite el procesamiento por lotes para fusionar varios archivos XLSM simultáneamente.