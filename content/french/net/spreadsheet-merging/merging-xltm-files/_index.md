---
title: Fusion de fichiers XLTM
linktitle: Fusion de fichiers XLTM
second_title: API GroupDocs.Merger .NET
description: Découvrez comment fusionner des fichiers XLTM par programme. Guide étape par étape avec des exemples de code.
weight: 16
url: /fr/net/spreadsheet-merging/merging-xltm-files/
type: docs
---
# Fusion de fichiers XLTM

## Introduction
Dans ce didacticiel, nous allons explorer comment fusionner des fichiers XLTM (Excel Macro-Enabled Template). GroupDocs.Merger pour .NET est une bibliothèque puissante qui permet aux développeurs de manipuler et de fusionner divers formats de documents par programme. Ce guide vous guidera pas à pas tout au long du processus de fusion de fichiers XLTM à l'aide de C#.
## Conditions préalables
Avant de commencer, assurez-vous que les conditions préalables suivantes sont remplies :
- Visual Studio installé sur votre système.
- Connaissance de base de la programmation C#.
-  GroupDocs.Merger pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/merger/net/).
- Accès aux fichiers XLTM que vous souhaitez fusionner.

## Importer des espaces de noms
Commencez par importer les espaces de noms nécessaires dans votre projet C#.
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```

Passons maintenant à la fusion de fichiers XLTM.
## Étape 1 : initialiser le répertoire de sortie
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xltm");
```
 Remplacer`"Your Output Directory"` avec le chemin où vous souhaitez enregistrer le fichier XLTM fusionné.
## Étape 2 : Fusionner les fichiers XLTM
```csharp
// Charger le fichier source XLTM
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Ajouter un autre fichier XLTM à fusionner
    merger.Join("Your Sample File");
    //Fusionner les fichiers XLTM et enregistrer le résultat
    merger.Save(outputFile);
}
```
Dans cet extrait de code :
- « Votre fichier exemple » et « Votre fichier exemple » représentent les chemins d'accès à vos fichiers XLTM d'entrée. Assurez-vous de les remplacer par les chemins de fichiers réels.
## Étape 3 : Afficher l'emplacement de sortie
```csharp
Console.WriteLine("\nXLTM files merge completed successfully. \nCheck output in {0}", outputFolder);
```
Ce code affichera un message indiquant la réussite de l'opération de fusion ainsi que le chemin du répertoire de sortie.

## Conclusion
En suivant ce tutoriel, vous avez appris à fusionner des fichiers XLTM. Cette bibliothèque offre des fonctionnalités étendues pour la manipulation de documents, offrant aux développeurs un ensemble d'outils robustes pour gérer les tâches liées aux documents par programmation.

## FAQ
### GroupDocs.Merger peut-il fusionner d'autres formats de documents que XLTM ?
Oui, GroupDocs.Merger prend en charge la fusion de divers formats de documents tels que DOCX, XLSX, PPTX, PDF, etc.
### GroupDocs.Merger nécessite-t-il une licence pour une utilisation commerciale ?
 Oui, vous aurez besoin d'une licence valide pour utiliser GroupDocs.Merger dans un environnement commercial. Vous pouvez obtenir une licence[ici](https://purchase.groupdocs.com/buy).
### Existe-t-il un essai gratuit disponible pour GroupDocs.Merger ?
 Oui, vous pouvez accéder à un essai gratuit de GroupDocs.Merger[ici](https://releases.groupdocs.com/).
### Où puis-je trouver de la documentation pour GroupDocs.Merger ?
Vous pouvez vous référer à la documentation complète de GroupDocs.Merger[ici](https://tutorials.groupdocs.com/merger/net/).
### Où puis-je obtenir une assistance technique pour GroupDocs.Merger ?
 Pour une assistance technique et un support, visitez le forum GroupDocs.Merger[ici](https://forum.groupdocs.com/c/merger/32).