---
title: Guide de fusion de fichiers XLSM
linktitle: Guide de fusion de fichiers XLSM
second_title: API GroupDocs.Merger .NET
description: Fusionnez des fichiers XLSM en toute transparence avec GroupDocs.Merger pour .NET. Combinez efficacement des classeurs Excel par programmation. Améliorez vos capacités de manipulation de documents.
weight: 13
url: /fr/net/spreadsheet-merging/guide-merging-xlsm-files/
---

# Guide de fusion de fichiers XLSM

## Introduction
Dans ce didacticiel, nous allons explorer comment fusionner des fichiers XLSM (Excel Macro-Enabled Workbook). GroupDocs.Merger est une bibliothèque puissante qui permet aux développeurs de manipuler les formats de documents, notamment la fusion, le fractionnement et la modification de fichiers par programme.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
-  GroupDocs.Merger pour .NET : téléchargez et installez la bibliothèque à partir de[ici](https://releases.groupdocs.com/merger/net/).
- Environnement de développement : configurez Visual Studio ou tout environnement de développement .NET compatible.
- Fichiers XLSM : préparez les fichiers XLSM que vous souhaitez fusionner.

## Importer des espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires dans votre projet .NET :
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Étape 1 : Définir le dossier de sortie et le nom du fichier
Commencez par définir le dossier de sortie et le nom du fichier XLSM fusionné :
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Étape 2 : Charger et fusionner des fichiers XLSM
Ensuite, chargez les fichiers XLSM sources et fusionnez-les en un seul fichier :
```csharp
// Charger le fichier XLSM source
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Ajouter un autre fichier XLSM à fusionner
    merger.Join("Your Sample File");
    // Fusionner les fichiers XLSM et enregistrer le résultat
    merger.Save(outputFile);
}
```
## Étape 3 : Vérifier la fin de la fusion
Enfin, informez l'utilisateur de la réussite de la fusion et affichez le chemin de sortie :
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
Vous avez appris à fusionner des fichiers XLSM par programme. Cette bibliothèque simplifie les tâches de manipulation de documents, permettant une fusion efficace des fichiers au sein de vos applications .NET.

## FAQ
### GroupDocs.Merger peut-il gérer de gros fichiers XLSM ?
Oui, GroupDocs.Merger gère efficacement les gros fichiers XLSM sans problèmes de performances.
### GroupDocs.Merger prend-il en charge d'autres formats de fichiers que XLSM ?
Oui, GroupDocs.Merger prend en charge divers formats de documents tels que DOCX, PDF, PPTX, etc.
### GroupDocs.Merger est-il compatible avec les applications .NET Core ?
Oui, GroupDocs.Merger est compatible avec les environnements .NET Framework et .NET Core.
### Puis-je fusionner des fichiers XLSM cryptés à l’aide de GroupDocs.Merger ?
Oui, GroupDocs.Merger prend en charge la fusion de fichiers XLSM cryptés avec les informations d'identification correctes.
### GroupDocs.Merger offre-t-il des capacités de traitement par lots ?
Oui, GroupDocs.Merger permet le traitement par lots pour fusionner plusieurs fichiers XLSM simultanément.