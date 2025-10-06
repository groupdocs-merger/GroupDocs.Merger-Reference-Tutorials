---
title: Comment fusionner des fichiers XLSB
linktitle: Comment fusionner des fichiers XLSB
second_title: API GroupDocs.Merger .NET
description: Découvrez comment fusionner des fichiers XLSB. Ce guide étape par étape simplifie les tâches de manipulation de documents.
weight: 12
url: /fr/net/spreadsheet-merging/how-to-merge-xlsb-files/
type: docs
---
# Comment fusionner des fichiers XLSB

## Introduction
Dans ce didacticiel, nous allons explorer comment fusionner des fichiers XLSB (Excel Binary Workbook). GroupDocs.Merger pour .NET est une puissante API de manipulation de documents qui permet aux développeurs de fusionner, diviser et manipuler divers formats de documents de manière transparente au sein de leurs applications .NET. Plus précisément, nous nous concentrerons sur la fusion de fichiers XLSB à l'aide de cette bibliothèque polyvalente.
## Conditions préalables
Avant de plonger dans le didacticiel, assurez-vous d'avoir configuré les conditions préalables suivantes :
- Visual Studio installé sur votre système.
- Connaissance de base de la programmation C#.
- Bibliothèque GroupDocs.Merger pour .NET téléchargée et référencée dans votre projet.
  

## Importer des espaces de noms
Avant de commencer le codage, importez les espaces de noms nécessaires dans votre projet C# :
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Étape 1 : Configurez votre répertoire de sortie
```csharp
string outputFolder = "Your Output Directory";
```
## Étape 2 : Définir le chemin du fichier de sortie
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlsb");
```
## Étape 3 : Charger le fichier source XLSB
```csharp
// Charger le fichier XLSB source
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Ajouter un autre fichier XLSB à fusionner
    merger.Join("Your Sample File");
    // Fusionner les fichiers XLSB et enregistrer le résultat
    merger.Save(outputFile);
}
```
## Étape 4 : Afficher le message de fin de fusion
```csharp
Console.WriteLine("\nXLSB files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
En suivant ces étapes, vous pouvez facilement fusionner des fichiers XLSB. Cette API simplifie les tâches de manipulation de documents et offre une intégration transparente dans vos applications .NET.

## FAQ
### GroupDocs.Merger peut-il gérer d’autres formats de fichiers que XLSB ?
Oui, GroupDocs.Merger prend en charge un large éventail de formats de documents, notamment DOCX, PDF, XLSX, PPTX, etc.
### Où puis-je trouver plus de documentation sur GroupDocs.Merger ?
 Visiter le[Documentation](https://tutorials.groupdocs.com/merger/net/) pour des instructions d'utilisation détaillées et des références API.
### Existe-t-il un essai gratuit disponible pour GroupDocs.Merger ?
 Oui, vous pouvez accéder à un[essai gratuit](https://releases.groupdocs.com/)pour explorer les fonctionnalités de GroupDocs.Merger.
### Comment puis-je obtenir une assistance technique pour GroupDocs.Merger ?
 Rejoins[Forum GroupDocs](https://forum.groupdocs.com/c/merger/32) pour poser des questions et interagir avec la communauté.
### Où puis-je acheter une licence pour GroupDocs.Merger ?
 Vous pouvez acheter une licence auprès du[page d'achat](https://purchase.groupdocs.com/buy).