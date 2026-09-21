---
date: '2026-09-21'
description: Apprenez à intégrer un PDF dans des feuilles de calcul Excel avec GroupDocs.Merger
  pour .NET, améliorant la présentation des données et la fonctionnalité.
keywords:
- embed pdf in excel
- how to embed ole
- add ole object excel
- add ole to excel
lastmod: '2026-09-21'
og_description: Apprenez à intégrer un PDF dans Excel avec GroupDocs.Merger pour .NET.
  Suivez des instructions étape par étape, consultez des réponses rapides et évitez
  les pièges courants.
og_image_alt: Developer guide showing PDF embedded in an Excel spreadsheet via GroupDocs.Merger
  for .NET
og_title: Comment intégrer un PDF dans Excel avec GroupDocs.Merger pour .NET
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  headline: How to embed PDF in Excel using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed PDF in Excel spreadsheets with GroupDocs.Merger
    for .NET, enhancing data presentation and functionality.
  name: How to embed PDF in Excel using GroupDocs.Merger for .NET
  steps:
  - name: '**Free trial** – test the library without cost.'
    text: '**Free trial** – test the library without cost.'
  - name: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
    text: '**Temporary license** – request a temporary license on the [temporary‑license
      page](https://purchase.groupdocs.com/temporary-license/).'
  - name: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
    text: '**Purchase** – consider purchasing a license on the [GroupDocs purchase
      page](https://purchase.groupdocs.com/buy).'
  - name: '**Financial reports** – attach audited statements directly beside summary
      tables.'
    text: '**Financial reports** – attach audited statements directly beside summary
      tables.'
  - name: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
    text: '**Project documentation** – keep design specs, risk analyses, or contracts
      within a master tracker.'
  - name: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
    text: '**Training dashboards** – embed user manuals or policy PDFs for quick reference
      by staff.'
  type: HowTo
- questions:
  - answer: An OLE (Object Linking and Embedding) object stores another file (PDF,
      Word, image, etc.) inside a host document, allowing in‑place editing or opening.
    question: What is an OLE object?
  - answer: Yes—GroupDocs.Merger also supports Word, PowerPoint, and Visio files.
    question: Can I embed OLE objects in other Office formats?
  - answer: Provide the password when creating the `OleSpreadsheetOptions` instance;
      the library will decrypt the file automatically.
    question: How do I handle password‑protected PDFs?
  - answer: Technically no hard limit, but files larger than 10 MB may noticeably
      increase workbook load time.
    question: Is there a size limitation for embedded PDFs?
  - answer: Visit the official [GroupDocs Documentation](https://docs.groupdocs.com/merger/net/)
      for additional code samples and API references.
    question: Where can I find more examples?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- .NET Excel integration
title: Comment intégrer un PDF dans Excel avec GroupDocs.Merger pour .NET
type: docs
url: /fr/net/document-import/embed-ole-objects-groupdocs-merger-net/
weight: 1
---

# Comment intégrer un PDF dans Excel avec GroupDocs.Merger pour .NET

## Introduction

Intégrer un PDF dans Excel vous permet de conserver les documents d’accompagnement — tels que les contrats, rapports ou spécifications — directement là où se trouvent les données. Avec **GroupDocs.Merger for .NET**, vous pouvez ajouter des objets OLE aux cellules en quelques lignes de code seulement, transformant une feuille de calcul ordinaire en un classeur interactif et autonome. Ce tutoriel vous guide à travers tout ce que vous devez savoir, de l’installation au dépannage.

**Ce que vous apprendrez**

- Comment configurer GroupDocs.Merger pour .NET dans un projet C#  
- Les étapes exactes pour intégrer un PDF (ou tout fichier compatible OLE) dans une cellule Excel  
- Options de configuration, conseils de performance et pièges courants  

Vérifions que vous avez tout le nécessaire avant de commencer.

## Réponses rapides
- **Puis-je intégrer n'importe quel type de fichier ?** Oui — tout format pris en charge en tant qu'objet OLE (PDF, Word, image, etc.).  
- **Ai-je besoin d'une licence pour le développement ?** Un essai gratuit suffit pour les tests ; une licence permanente est requise pour la production.  
- **Quelles versions de .NET sont prises en charge ?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7+.  
- **La taille du fichier Excel augmentera-t-elle de façon spectaculaire ?** Seulement de la taille du document intégré ; gardez les fichiers en dessous de quelques Mo pour de meilleures performances.  
- **Existe-t-il une limite au nombre d'objets OLE ?** Pratiquement aucune, mais des classeurs très volumineux peuvent affecter le temps de chargement.

## Qu'est-ce que l'intégration de PDF dans Excel ?

Intégrer un PDF dans Excel insère le PDF complet comme un objet OLE qui peut être ouvert directement depuis la feuille de calcul. Les utilisateurs cliquent sur l'icône et consultent le document original sans quitter Excel. Cette approche préserve la mise en page originale, permet une référence rapide et élimine la nécessité de gérer des fichiers séparés. Le PDF intégré se comporte comme tout autre objet OLE, permettant aux utilisateurs de double‑cliquer sur l'icône pour lancer le visualiseur PDF tout en restant dans l'environnement Excel.

## Pourquoi intégrer des objets OLE dans Excel ?

GroupDocs.Merger prend en charge **plus de 120 formats d'entrée et de sortie** et peut intégrer des objets sans charger le fichier complet en mémoire, permettant un traitement rapide de PDF de plusieurs centaines de pages. Cela réduit le besoin de dépôts de fichiers séparés et garde les données associées ensemble. Cela simplifie également le contrôle de version et garantit que toute la documentation pertinente accompagne le classeur, améliorant la collaboration entre les équipes.

## Prérequis

- **GroupDocs.Merger for .NET** (dernier package NuGet)  
- **.NET Framework** 4.5+ **or** **.NET Core/5+/6+**  
- Visual Studio 2022 or later  
- Connaissances de base en C# et familiarité avec les entrées/sorties de fichiers  

## Configuration de GroupDocs.Merger pour .NET

### Installation

Ajoutez le package en utilisant l'une des méthodes suivantes :

**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI**  
Recherchez « GroupDocs.Merger » et installez la dernière version.

### Obtention de licence

1. **Essai gratuit** – testez la bibliothèque sans frais.  
2. **Licence temporaire** – demandez une licence temporaire sur la [page de licence temporaire](https://purchase.groupdocs.com/temporary-license/).  
3. **Achat** – envisagez d'acheter une licence sur la [page d'achat GroupDocs](https://purchase.groupdocs.com/buy).

### Initialisation de base

`Merger` est le point d'entrée pour toutes les opérations.  
```csharp
using (Merger merger = new Merger("path_to_your_spreadsheet.xlsx"))
{
    // Your code to work with the document
}
```  

## Comment intégrer des objets OLE dans Excel ?

Chargez votre classeur source, configurez les options OLE, et laissez `Merger` insérer l'objet. Les sections suivantes vous offrent un flux de travail concis et prêt à l'emploi.

### Vue d'ensemble de la fonctionnalité
Intégrer des objets OLE vous permet de stocker un PDF complet dans une cellule, en préservant la mise en page originale et en permettant un accès en un clic depuis Excel.

### Mise en œuvre étape par étape

#### 1. Définir les chemins et le numéro de page
Spécifiez la feuille de calcul, le fichier à intégrer et l'adresse de la cellule cible.

```csharp
string filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
string embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_PDF";
int pageNumber = 2; // The specific page to embed

// Output path for the modified spreadsheet
string filePathOut = Path.Combine("YOUR_OUTPUT_DIRECTORY", "OUT_SAMPLE_NAME.xlsx");
```  

#### 2. Configurer OleSpreadsheetOptions
`OleSpreadsheetOptions` définit où l'objet OLE sera placé dans la feuille de calcul et comment son icône apparaît.  
```csharp
// Specify row and column indices for embedding
OleSpreadsheetOptions oleCellsOptions = new OleSpreadsheetOptions(embeddedFilePath, pageNumber)
{
    RowIndex = 2,
    ColumnIndex = 2
};
```  

#### 3. Initialiser Merger et effectuer l'intégration
La classe `Merger` gère l'insertion réelle. Après l'appel, le classeur contient l'icône OLE.

```csharp
using (Merger merger = new Merger(filePath))
{
    merger.ImportDocument(oleCellsOptions); // Import the specified document as an OLE object into the spreadsheet
    merger.Save(filePathOut); // Save the modified document
}
```  

### Conseils de dépannage courants
- Vérifiez que tous les chemins de fichiers sont absolus ou correctement résolus par rapport à l'exécutable.  
- Assurez‑vous que le numéro de page spécifié existe dans le PDF source ; sinon une exception est levée.  
- Si l'objet intégré ne s'affiche pas, confirmez que la version cible d'Excel prend en charge OLE (la plupart des versions modernes le font).

## Applications pratiques

Intégrer un PDF dans Excel est utile pour :

1. **Rapports financiers** – joindre les états audités directement à côté des tableaux récapitulatifs.  
2. **Documentation de projet** – conserver les spécifications de conception, analyses de risques ou contrats dans un tableau de suivi principal.  
3. **Tableaux de bord de formation** – intégrer les manuels d'utilisateur ou les PDF de politique pour une référence rapide par le personnel.

## Considérations de performance

- **Taille du fichier** – gardez les PDF intégrés en dessous de 5 Mo pour éviter d'alourdir le classeur.  
- **Utilisation de la mémoire** – `GroupDocs.Merger` diffuse les données, ainsi la consommation mémoire reste faible même avec de gros fichiers source.  
- **Libérer les objets** – appelez toujours `Dispose()` sur les instances de `Merger` pour libérer rapidement les poignées de fichiers.

## Questions fréquentes

**Q : Qu'est‑ce qu'un objet OLE ?**  
R : Un objet OLE (Object Linking and Embedding) stocke un autre fichier (PDF, Word, image, etc.) à l'intérieur d'un document hôte, permettant une édition ou une ouverture sur place.

**Q : Puis‑je intégrer des objets OLE dans d'autres formats Office ?**  
R : Oui — GroupDocs.Merger prend également en charge les fichiers Word, PowerPoint et Visio.

**Q : Comment gérer les PDF protégés par mot de passe ?**  
R : Fournissez le mot de passe lors de la création de l'instance `OleSpreadsheetOptions` ; la bibliothèque déchiffrera automatiquement le fichier.

**Q : Existe‑t‑il une limitation de taille pour les PDF intégrés ?**  
R : Techniquement, aucune limite stricte, mais les fichiers supérieurs à 10 Mo peuvent augmenter de façon notable le temps de chargement du classeur.

**Q : Où puis‑je trouver plus d'exemples ?**  
R : Consultez la [documentation officielle de GroupDocs](https://docs.groupdocs.com/merger/net/) pour des exemples de code supplémentaires et des références API.

## Ressources supplémentaires
- **Documentation** : [GroupDocs.Merger .NET Docs](https://docs.groupdocs.com/merger/net/)  
- **Référence API** : [GroupDocs API Reference](https://reference.groupdocs.com/merger/net/)  
- **Téléchargements** : [GroupDocs Releases](https://releases.groupdocs.com/merger/net/)  
- **Achat de licence GroupDocs** : [Buy GroupDocs License](https://purchase.groupdocs.com/buy)  
- **Essai gratuit GroupDocs** : [Try GroupDocs Free Trial](https://releases.groupdocs.com/merger/net/)  
- **Demander une licence temporaire** : [Request Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Forum de support GroupDocs** : [GroupDocs Support Forum](https://forum.groupdocs.com/c/merger)

---

**Last Updated:** 2026-09-21  
**Tested with:** GroupDocs.Merger 23.12 for .NET  
**Author:** GroupDocs

## Tutoriels associés

- [Intégrer un PDF en tant qu'OLE dans PowerPoint avec GroupDocs.Merger pour .NET : Guide étape par étape](/merger/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/)
- [Intégrer un PDF dans Word avec GroupDocs.Merger pour .NET : Guide étape par étape](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Charger un PDF depuis une URL en .NET avec GroupDocs.Merger : Guide complet](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)


{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}