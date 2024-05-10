---
title: Comment fusionner des fichiers 7z
linktitle: Comment fusionner des fichiers 7z
second_title: API GroupDocs.Merger .NET
description: Fusionnez sans effort des fichiers 7z à l'aide de GroupDocs.Merger pour .NET. Suivez notre guide étape par étape pour combiner plusieurs archives en une seule de manière transparente.
type: docs
weight: 10
url: /fr/net/merge-compress-files/merge-7z-files/
---
## Introduction
La fusion de fichiers 7z peut être effectuée efficacement à l'aide de GroupDocs.Merger pour .NET, une puissante bibliothèque de manipulation de documents. Ce didacticiel vous guidera étape par étape tout au long du processus, vous permettant de fusionner facilement et en toute transparence vos fichiers 7z.
## Conditions préalables
Avant de commencer, assurez-vous d'avoir les éléments suivants :
- Visual Studio installé sur votre système.
-  GroupDocs.Merger pour la bibliothèque .NET installée. Vous pouvez le télécharger depuis[ici](https://releases.groupdocs.com/merger/net/).
- Compréhension de base de la programmation C#.

## Importer des espaces de noms
Tout d’abord, incluez les espaces de noms nécessaires dans votre code C# :
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Étape 1 : Charger le fichier source 7Z
Commencez par spécifier le répertoire de sortie et le nom du fichier 7z fusionné :
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Étape 2 : Fusionner les fichiers 7Z
Chargez le fichier 7Z source et ajoutez un autre fichier 7Z que vous souhaitez fusionner :
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Étape 3 : Enregistrer le fichier 7Z fusionné
Exécutez l'opération de fusion et enregistrez le fichier 7Z fusionné résultant :
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusion
Dans ce didacticiel, nous avons exploré comment fusionner des fichiers 7z à l'aide de GroupDocs.Merger pour .NET. En suivant ces étapes simples, vous pouvez combiner efficacement plusieurs fichiers 7z en une seule archive unifiée.

## FAQ
### Puis-je fusionner plus de deux fichiers 7z à l’aide de GroupDocs.Merger ?
 Oui, vous pouvez fusionner n'importe quel nombre de fichiers 7z à l'aide de cette bibliothèque. Ajoutez simplement chaque fichier en utilisant le`Join` méthode.
### GroupDocs.Merger pour .NET est-il compatible avec d’autres formats d’archives ?
Oui, GroupDocs.Merger prend en charge la fusion de divers formats de documents, notamment des archives telles que ZIP, 7z et RAR.
### Où puis-je trouver une assistance ou une assistance supplémentaire avec GroupDocs.Merger ?
 Pour obtenir de l'aide supplémentaire, visitez le[Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### Puis-je essayer GroupDocs.Merger pour .NET avant d'acheter ?
 Oui, vous pouvez explorer les fonctionnalités de GroupDocs.Merger en téléchargeant le[version d'essai gratuite](https://releases.groupdocs.com/).
### Comment puis-je obtenir une licence temporaire pour GroupDocs.Merger ?
 Si vous avez besoin d'un permis temporaire, visitez[ici](https://purchase.groupdocs.com/temporary-license/).