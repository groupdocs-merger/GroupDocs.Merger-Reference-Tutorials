---
title: Fusionar archivos XLS
linktitle: Fusionar archivos XLS
second_title: API GroupDocs.Merger .NET
description: Aprenda a combinar archivos de Excel en .NET usando GroupDocs.Merger para una manipulación de documentos perfecta. Sigue nuestro tutorial paso a paso.
type: docs
weight: 11
url: /es/net/spreadsheet-merging/merging-xls-files/
---
## Introducción
En este tutorial, exploraremos cómo fusionar archivos XLS (Excel). GroupDocs.Merger es una potente API de manipulación de documentos que permite a los desarrolladores fusionar, dividir, reorganizar y manipular documentos sin esfuerzo dentro de sus aplicaciones .NET. Específicamente, nos centraremos en fusionar archivos XLS paso a paso utilizando los métodos intuitivos de GroupDocs.Merger.
## Requisitos previos
Antes de comenzar, asegúrese de tener configurados los siguientes requisitos previos:
- Visual Studio: instale Visual Studio en su máquina.
-  GroupDocs.Merger para .NET: descargue e instale GroupDocs.Merger para .NET desde[aquí](https://releases.groupdocs.com/merger/net/).
- .NET Framework: asegúrese de tener instalado .NET Framework.
- Archivos XLS de muestra: prepare los archivos XLS que desea fusionar.

## Importar espacios de nombres
Comience importando los espacios de nombres necesarios para usar GroupDocs.Merger en su proyecto:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Paso 1: inicializar el directorio de salida
Primero, especifique el directorio donde desea guardar el archivo XLS combinado:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Paso 2: cargar y fusionar archivos XLS
Ahora, carguemos y combinemos los archivos XLS usando GroupDocs.Merger:
```csharp
// Cargue el archivo XLS de origen
using (var merger = new Merger("Your Sample File"))
{
    // Agregue otro archivo XLS para fusionar
    merger.Join("Your Sample File");
    
    // Fusionar archivos XLS y guardar el resultado
    merger.Save(outputFile);
}
```
## Paso 3: Mostrar la ubicación de salida
Finalmente, muestra un mensaje que indica la finalización y ubicación del archivo XLS fusionado:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
En este tutorial, hemos aprendido cómo fusionar archivos XLS. Si sigue los pasos proporcionados, puede combinar de manera eficiente varios archivos de Excel mediante programación dentro de sus aplicaciones .NET.

## Preguntas frecuentes
### ¿GroupDocs.Merger es compatible con otros formatos de documentos?
Sí, GroupDocs.Merger admite varios formatos de documentos como PDF, DOCX, XLSX, PPTX y más.
### ¿Puedo dividir documentos usando GroupDocs.Merger?
¡Absolutamente! GroupDocs.Merger le permite dividir documentos según sus requisitos.
### ¿Dónde puedo encontrar más recursos y soporte para GroupDocs.Merger?
Puede explorar la documentación y hacer preguntas en el[Foro de GroupDocs](https://forum.groupdocs.com/c/merger/32).
### ¿Hay una prueba gratuita disponible para GroupDocs.Merger?
 Sí, puedes empezar con un[prueba gratis](https://releases.groupdocs.com/) para evaluar la funcionalidad.
### ¿Cómo puedo comprar una licencia para GroupDocs.Merger?
 Visita el[pagina de compra](https://purchase.groupdocs.com/buy) para adquirir una licencia adaptada a sus necesidades.