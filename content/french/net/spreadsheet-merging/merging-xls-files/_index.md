---
title: Fusion de fichiers XLS
linktitle: Fusion de fichiers XLS
second_title: API GroupDocs.Merger .NET
description: Découvrez comment fusionner des fichiers Excel dans .NET à l'aide de GroupDocs.Merger pour une manipulation transparente des documents. Suivez notre tutoriel étape par étape.
weight: 11
url: /fr/net/spreadsheet-merging/merging-xls-files/
type: docs
---
# Fusion de fichiers XLS

## Introduction
Dans ce didacticiel, nous explorerons comment fusionner des fichiers XLS (Excel). GroupDocs.Merger est une puissante API de manipulation de documents qui permet aux développeurs de fusionner, diviser, réorganiser et manipuler des documents sans effort au sein de leurs applications .NET. Plus précisément, nous nous concentrerons sur la fusion de fichiers XLS étape par étape à l'aide des méthodes intuitives de GroupDocs.Merger.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir configuré les conditions préalables suivantes :
- Visual Studio : installez Visual Studio sur votre ordinateur.
-  GroupDocs.Merger pour .NET : téléchargez et installez GroupDocs.Merger pour .NET à partir de[ici](https://releases.groupdocs.com/merger/net/).
- .NET Framework : assurez-vous que le framework .NET est installé.
- Exemples de fichiers XLS : préparez les fichiers XLS que vous souhaitez fusionner.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires pour utiliser GroupDocs.Merger dans votre projet :
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Étape 1 : initialiser le répertoire de sortie
Tout d'abord, spécifiez le répertoire dans lequel vous souhaitez enregistrer le fichier XLS fusionné :
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Étape 2 : Charger et fusionner des fichiers XLS
Maintenant, chargeons et fusionnons les fichiers XLS à l'aide de GroupDocs.Merger :
```csharp
// Charger le fichier source XLS
using (var merger = new Merger("Your Sample File"))
{
    // Ajouter un autre fichier XLS à fusionner
    merger.Join("Your Sample File");
    
    // Fusionner les fichiers XLS et enregistrer le résultat
    merger.Save(outputFile);
}
```
## Étape 3 : Afficher l'emplacement de sortie
Enfin, affichez un message indiquant la complétion et l'emplacement du fichier XLS fusionné :
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
Dans ce didacticiel, nous avons appris à fusionner des fichiers XLS. En suivant les étapes fournies, vous pouvez combiner efficacement plusieurs fichiers Excel par programmation dans vos applications .NET.

## FAQ
### GroupDocs.Merger est-il compatible avec d’autres formats de documents ?
Oui, GroupDocs.Merger prend en charge divers formats de documents tels que PDF, DOCX, XLSX, PPTX, etc.
### Puis-je diviser des documents à l’aide de GroupDocs.Merger ?
Absolument! GroupDocs.Merger vous permet de diviser des documents en fonction de vos besoins.
### Où puis-je trouver plus de ressources et d’assistance pour GroupDocs.Merger ?
Vous pouvez explorer la documentation et poser des questions sur le[Forum GroupDocs](https://forum.groupdocs.com/c/merger/32).
### Existe-t-il un essai gratuit disponible pour GroupDocs.Merger ?
 Oui, vous pouvez commencer par un[essai gratuit](https://releases.groupdocs.com/) pour évaluer la fonctionnalité.
### Comment puis-je acheter une licence pour GroupDocs.Merger ?
 Visiter le[page d'achat](https://purchase.groupdocs.com/buy) pour acquérir une licence adaptée à vos besoins.