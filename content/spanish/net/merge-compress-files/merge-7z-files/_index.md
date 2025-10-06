---
title: Cómo fusionar archivos 7z
linktitle: Cómo fusionar archivos 7z
second_title: API GroupDocs.Merger .NET
description: Fusione archivos 7z sin esfuerzo utilizando GroupDocs.Merger para .NET. Siga nuestra guía paso a paso para combinar varios archivos en uno sin problemas.
weight: 10
url: /es/net/merge-compress-files/merge-7z-files/
type: docs
---
# Cómo fusionar archivos 7z

## Introducción
La combinación de archivos 7z se puede realizar de manera eficiente utilizando GroupDocs.Merger para .NET, una potente biblioteca de manipulación de documentos. Este tutorial lo guiará a través del proceso paso a paso, permitiéndole fusionar fácilmente sus archivos 7z.
## Requisitos previos
Antes de comenzar, asegúrese de tener lo siguiente:
- Visual Studio instalado en su sistema.
-  Biblioteca GroupDocs.Merger para .NET instalada. Puedes descargarlo desde[aquí](https://releases.groupdocs.com/merger/net/).
- Conocimientos básicos de programación en C#.

## Importar espacios de nombres
Primero, incluya los espacios de nombres necesarios en su código C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Paso 1: cargar el archivo fuente 7Z
Comience especificando el directorio de salida y el nombre del archivo para el archivo 7z fusionado:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Paso 2: fusionar archivos 7Z
Cargue el archivo 7Z de origen y agregue otro archivo 7Z que desee fusionar:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Paso 3: guarde el archivo 7Z combinado
Ejecute la operación de combinación y guarde el archivo 7Z combinado resultante:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusión
En este tutorial, exploramos cómo fusionar archivos 7z usando GroupDocs.Merger para .NET. Si sigue estos sencillos pasos, puede combinar de manera eficiente varios archivos 7z en un único archivo unificado.

## Preguntas frecuentes
### ¿Puedo fusionar más de dos archivos 7z usando GroupDocs.Merger?
 Sí, puede fusionar cualquier cantidad de archivos 7z utilizando esta biblioteca. Simplemente agregue cada archivo usando el`Join` método.
### ¿GroupDocs.Merger para .NET es compatible con otros formatos de archivo?
Sí, GroupDocs.Merger admite la combinación de varios formatos de documentos, incluidos archivos como ZIP, 7z y RAR.
### ¿Dónde puedo encontrar soporte o asistencia adicional con GroupDocs.Merger?
 Para obtener más ayuda, visite el[Foro GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### ¿Puedo probar GroupDocs.Merger para .NET antes de comprarlo?
 Sí, puede explorar las funcionalidades de GroupDocs.Merger descargando el[versión de prueba gratuita](https://releases.groupdocs.com/).
### ¿Cómo puedo obtener una licencia temporal para GroupDocs.Merger?
 Si necesita una licencia temporal, visite[aquí](https://purchase.groupdocs.com/temporary-license/).