---
date: '2026-09-21'
description: Apprenez comment intégrer un PDF dans PowerPoint en tant qu'objet OLE
  avec GroupDocs.Merger pour .NET. Ce guide étape par étape vous montre les appels
  d'API exacts et les meilleures pratiques.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: intégrez un PDF dans PowerPoint en utilisant GroupDocs.Merger pour
  .NET. Suivez ce tutoriel concis pour ajouter des objets OLE, configurer les options
  et éviter les pièges courants.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: intégrer pdf dans PowerPoint – intégrer PDF en tant qu'OLE avec GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: Comment intégrer un PDF dans PowerPoint en tant qu'OLE avec GroupDocs.Merger
  pour .NET
type: docs
url: /fr/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# Intégrer un PDF dans PowerPoint en tant qu'OLE avec GroupDocs.Merger pour .NET

Intégrer directement un PDF dans une diapositive PowerPoint vous permet de conserver le document original intact tout en offrant à votre audience un accès instantané. Dans ce tutoriel, vous apprendrez **comment intégrer un PDF dans PowerPoint** en tant qu'objet OLE avec GroupDocs.Merger pour .NET, découvrirez les options d'API requises et des astuces pour des performances fiables.

## Réponses rapides
- **Quelle bibliothèque gère l'intégration OLE ?** GroupDocs.Merger pour .NET fournit la classe `OlePresentationOptions` à cet effet.  
- **Ai-je besoin d'une licence ?** Une licence d'essai fonctionne pour le développement ; une licence complète est requise pour la production.  
- **Puis-je intégrer plusieurs PDF ?** Oui – répétez l'étape d'importation pour chaque diapositive ciblée.  
- **Quelles versions de .NET sont prises en charge ?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **Le processus est‑il efficace en mémoire ?** L'API diffuse les fichiers, ainsi même les PDF de plusieurs centaines de pages peuvent être intégrés sans charger le fichier complet en mémoire.

## Qu'est-ce que l'intégration d'un PDF dans PowerPoint ?
**embed pdf in powerpoint** signifie insérer un fichier PDF en tant qu'objet OLE (Object Linking and Embedding) afin que la diapositive affiche une icône ou un aperçu qui, lorsqu'on double‑clique, ouvre le PDF original dans le visualiseur par défaut. Cette approche préserve la mise en forme, les hyperliens et les paramètres de sécurité du document source.

## Pourquoi utiliser l'intégration OLE plutôt que de convertir le PDF ?
L'intégration conserve la taille et la mise en page du fichier original, élimine les erreurs de conversion et vous permet de mettre à jour le PDF source sans réexporter la présentation. GroupDocs.Merger prend en charge **plus de 50 formats d'entrée et de sortie** et peut intégrer des PDF de plusieurs centaines de mégaoctets tout en diffusant les données pour maintenir l'utilisation de la mémoire en dessous de 100 Mo.

## Prérequis
- Visual Studio 2022 (ou tout IDE compatible .NET)  
- Runtime .NET Framework 4.5+ ou .NET Core 3.1+  
- Une licence valide de GroupDocs.Merger pour .NET (essai ou commerciale)  
- Un fichier PowerPoint (.pptx) et le PDF que vous souhaitez intégrer  

## Configuration de GroupDocs.Merger pour .NET

### Comment installer la bibliothèque ?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**Interface UI du gestionnaire de packages NuGet** – recherchez “GroupDocs.Merger” et cliquez sur **Install** pour obtenir la dernière version.

### Comment obtenir une licence ?
- **Essai gratuit** – inscrivez‑vous sur le site Web de GroupDocs pour obtenir une clé de licence temporaire.  
- **Licence temporaire** – demandez un essai prolongé si vous avez besoin de plus de 30 jours.  
- **Achat complet** – achetez une licence commerciale pour une utilisation en production illimitée.

### Comment initialiser l'API ?
`Merger` est la classe principale qui fournit des opérations de manipulation de documents telles que l'importation, la fusion et la conversion.  
Ajoutez les directives `using` requises en haut de votre fichier C# et créez une instance `Merger` avec le chemin du fichier de licence :

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## Guide de mise en œuvre

### Comment intégrer un PDF dans PowerPoint en tant qu'OLE ?
Chargez votre présentation, configurez les options OLE et appelez la méthode d'importation – l'opération complète se déroule en trois étapes logiques.

**Étape 1 – définir les emplacements des fichiers**  
Spécifiez les chemins absolus ou relatifs du PDF source, du fichier PowerPoint cible et du dossier où la présentation modifiée sera enregistrée.

**Étape 2 – configurer les options OLE**  
`OlePresentationOptions` est la classe qui indique à GroupDocs.Merger quel fichier intégrer, sur quelle diapositive et à quelles coordonnées. Elle vous permet également de définir la largeur, la hauteur et le mode d'affichage de l'objet intégré.

**Étape 3 – importer le PDF**  
`ImportDocument` est l'appel API de Merger qui insère l'objet OLE dans le fichier PowerPoint en utilisant les options fournies. La méthode diffuse le PDF dans la diapositive sans charger le document complet en mémoire.

#### Ancres de définition
- `OlePresentationOptions` est le conteneur d'options qui définit le fichier intégré, sa position (X/Y), sa taille et le numéro de diapositive cible.  
- `ImportDocument` est l'appel API de Merger qui insère l'objet OLE dans le fichier PowerPoint en utilisant les options fournies.

## Paramètres de configuration courants
- **SlideNumber** – l'indice basé sur 1 de la diapositive qui hébergera l'objet OLE.  
- **XCoordinate / YCoordinate** – position mesurée en points depuis le coin supérieur gauche de la diapositive.  
- **Width / Height** – dimensions de l'espace réservé OLE ; définissez à 0 pour utiliser la taille par défaut.  
- **ObjectName** – nom convivial optionnel affiché lorsque l'objet est sélectionné dans PowerPoint.

## Applications pratiques
Intégrer un PDF en tant qu'objet OLE est très utile dans de nombreux scénarios réels :

1. **Présentations d'entreprise** – joignez le dernier rapport financier sans alourdir la présentation.  
2. **Cours universitaires** – fournissez des articles de recherche complets en même temps que les résumés des diapositives.  
3. **Mises à jour de l'état du projet** – intégrez un plan de projet en direct que les parties prenantes peuvent ouvrir pour obtenir des détails.  
4. **Présentations commerciales** – incluez des fiches techniques produit que les commerciaux peuvent ouvrir à la demande.  
5. **Ateliers techniques** – présentez des schémas ou des fiches techniques que les ingénieurs peuvent inspecter instantanément.

## Considérations de performance
Pour que le processus d'intégration reste rapide et peu gourmand en mémoire :

- **Diffuser les fichiers** – GroupDocs.Merger lit et écrit des flux, ainsi même un PDF de 200 pages utilise moins de 100 Mo de RAM.  
- **Traitement par lots** – lors de la mise à jour de nombreuses présentations, réutilisez une seule instance `Merger` et fermez les flux rapidement.  
- **Redimensionner les gros PDF** – compressez ou sous‑échantillonnez les images du PDF source si vous constatez des temps de chargement lents.

## Questions fréquemment posées

**Q : Puis-je intégrer plusieurs PDF dans une même présentation ?**  
R : Oui. Appelez `ImportDocument` pour chaque PDF, en spécifiant un `SlideNumber` différent ou une position différente sur la même diapositive.

**Q : Quelle taille de PDF puis‑je intégrer ?**  
R : La limite pratique dépend de la mémoire de votre serveur ; des intégrations jusqu'à 500 Mo ont été testées sans problème grâce au streaming.

**Q : L'objet OLE conserve‑t‑il les éléments interactifs comme les hyperliens ?**  
R : Absolument. Le PDF intégré s'ouvre dans le visualiseur par défaut, préservant tous les liens internes et les signets.

**Q : Que faire si le PDF est protégé par un mot de passe ?**  
R : Fournissez le mot de passe via la propriété `Password` de `OlePresentationOptions` avant d’appeler `ImportDocument`.

**Q : L'objet intégré fonctionnera‑t‑il sur toutes les versions de PowerPoint ?**  
R : Le format OLE est pris en charge par PowerPoint 2007 et versions ultérieures, y compris Office 365.

## Conclusion
Vous disposez désormais d’un flux de travail complet et prêt pour la production pour **embed pdf in powerpoint** en tant qu'objet OLE avec GroupDocs.Merger pour .NET. En diffusant les fichiers, en configurant `OlePresentationOptions` et en appelant `ImportDocument`, vous pouvez enrichir les présentations avec les PDF originaux tout en maintenant une faible utilisation de la mémoire et en préservant toutes les fonctionnalités interactives. Explorez les capacités supplémentaires de Merger telles que la fusion de diapositives, la conversion de formats et le filigrane pour automatiser davantage vos pipelines de documents.

---

**Dernière mise à jour :** 2026-09-21  
**Testé avec :** GroupDocs.Merger 23.12 pour .NET  
**Auteur :** GroupDocs  

## Ressources
- **Documentation :** [Documentation GroupDocs.Merger pour .NET](https://docs.groupdocs.com/merger/net/)  
- **Référence API :** [Référence API GroupDocs.Merger](https://reference.groupdocs.com/merger/net/)  
- **Téléchargement :** [Téléchargements GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- **Achat :** [Acheter une licence GroupDocs](https://purchase.groupdocs.com/buy)  
- **Essai gratuit :** [Essai gratuit GroupDocs](https://releases.groupdocs.com/merger/net/)  
- **Licence temporaire :** [Obtenir une licence temporaire](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## Tutoriels associés

- [Intégrer un PDF dans Word avec GroupDocs.Merger pour .NET : guide étape par étape](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [Charger un PDF depuis une URL en .NET avec GroupDocs.Merger : guide complet](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [Comment récupérer les informations d'un document avec GroupDocs.Merger pour .NET : guide complet](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)