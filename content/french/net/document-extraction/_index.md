---
date: 2026-08-31
description: Apprenez à extraire des pages PDF spécifiques en utilisant GroupDocs.Merger
  pour .NET. Des guides étape par étape couvrent les scénarios d'extraction de Word,
  PDF et DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Apprenez à extraire des pages PDF spécifiques en utilisant GroupDocs.Merger
  pour .NET. Des guides détaillés vous aident à extraire efficacement des pages de
  fichiers PDF, Word et DOCX.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Comment extraire des pages PDF spécifiques avec GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Comment extraire des pages PDF spécifiques avec GroupDocs.Merger
type: docs
url: /fr/net/document-extraction/
weight: 9
---

# Comment extraire des pages spécifiques d'un PDF avec GroupDocs.Merger

L'extraction de pages spécifiques d'un PDF est une exigence courante lorsque vous devez réutiliser, partager ou archiver uniquement une partie d'un document plus volumineux. Avec GroupDocs.Merger pour .NET, vous pouvez extraire programmatiquement des pages individuelles, des plages de pages ou des sélections personnalisées à partir de fichiers PDF, Word et DOCX sans édition manuelle. Ce tutoriel vous guide à travers les concepts, les prérequis et le flux de travail étape par étape afin que vous puissiez intégrer l'extraction de pages dans n'importe quelle application .NET.

## Réponses rapides
- **Que signifie « extraire des pages spécifiques d'un PDF » ?** Cela signifie sélectionner des pages individuelles ou des plages dans un PDF (ou autre format pris en charge) et les enregistrer comme un nouveau document plus petit.  
- **Quels formats sont pris en charge ?** GroupDocs.Merger gère plus de 50 formats d'entrée et de sortie, y compris PDF, DOCX, PPTX et les images.  
- **Ai-je besoin d'une licence ?** Une licence temporaire fonctionne pour les tests ; une licence complète est requise pour une utilisation en production.  
- **Puis-je traiter de gros fichiers ?** Oui – la bibliothèque traite des fichiers de plusieurs centaines de pages en utilisant le streaming, ce qui maintient une faible consommation de mémoire.  
- **Le .NET Core est-il pris en charge ?** Absolument – l'API fonctionne avec .NET Framework 4.6+, .NET Core 3.1+ et .NET 6/7.

## Qu'est-ce que l'extraction de pages spécifiques d'un PDF ?
`extract specific pages pdf` fait référence à l'opération consistant à prendre une ou plusieurs pages d'un PDF existant (ou d'un document pris en charge) et à créer un nouveau PDF ne contenant que ces pages. Cela vous permet de partager uniquement les sections pertinentes tout en conservant le fichier original intact.

## Pourquoi extraire des pages spécifiques d'un PDF avec GroupDocs.Merger ?
GroupDocs.Merger traite jusqu'à **plus de 50 formats de fichiers** et peut extraire des pages de documents contenant **plus de 500 pages** en moins de **2 secondes** sur un CPU de serveur standard. L'API fonctionne sans nécessiter l'installation de Microsoft Office ou d'Adobe Acrobat, ce qui réduit la complexité du déploiement et les coûts de licence.

## Prérequis
- SDK .NET 6 (ou .NET Core 3.1 / .NET Framework 4.6+) installé sur votre machine de développement.  
- Un package NuGet valide GroupDocs.Merger for .NET (`GroupDocs.Merger`) ajouté à votre projet.  
- (Facultatif) Un fichier de licence temporaire ou complet si vous prévoyez d'exécuter le code au-delà de la période d'évaluation.

## Comment extraire des pages spécifiques d'un PDF en C# avec GroupDocs.Merger

Chargez le document source, spécifiez les pages dont vous avez besoin, puis enregistrez le résultat. La bibliothèque abstrait tous les détails spécifiques aux formats, de sorte que le même code fonctionne pour PDF, DOCX, PPTX et plus encore.

Chargez votre fichier source et appelez la méthode `Extract` avec les numéros de pages souhaités. La méthode `Extract` crée un nouveau document contenant uniquement les pages spécifiées. La méthode renvoie un nouvel objet `Document` que vous pouvez enregistrer immédiatement. Un objet `Document` représente une représentation en mémoire du fichier résultant.

### Étape 1 : créer une instance Merger
La classe `Merger` est le point d'entrée pour charger et manipuler les documents. Instanciez la classe `Merger` en passant le chemin du fichier source. Cet objet représente le document avec lequel vous allez travailler.

### Étape 2 : spécifier les pages à extraire
Fournissez une liste d'index de pages (commençant à 1) ou une chaîne de plage telle que "1-3,5" pour indiquer à la bibliothèque quelles pages conserver.

### Étape 3 : enregistrer le document extrait
Appelez `Save` sur l'objet `Document`, en fournissant le chemin de sortie et le format souhaité (par ex., `SaveFormat.Pdf`). `SaveFormat` est une énumération qui spécifie le type de fichier de sortie, comme le PDF. L'opération écrit un nouveau fichier contenant uniquement les pages sélectionnées.

## Problèmes courants et solutions
- **Les pages sont décalées d'une unité :** GroupDocs.Merger utilise une numérotation des pages à partir de 1. Assurez‑vous que votre liste commence à 1, pas à 0.  
- **Fichiers protégés par mot de passe :** Transmettez le mot de passe au constructeur `Merger` ou utilisez l'objet `LoadOptions`. `LoadOptions` fournit des paramètres qui contrôlent la façon dont un document est chargé, par ex., l'activation du cache mémoire.  
- **Les gros fichiers provoquent des dépassements de délai :** Activez le streaming en définissant `LoadOptions.UseMemoryCache = true` pour maintenir une faible consommation de mémoire.

## Questions fréquemment posées

**Q : Puis‑je extraire des pages d'un document Word au format PDF ?**  
R : Oui – le même appel `Extract` fonctionne pour DOCX, et vous pouvez enregistrer le résultat directement au format PDF en utilisant `SaveFormat.Pdf`.

**Q : Est‑il possible d'extraire des pages non consécutives ?**  
R : Absolument. Fournissez une liste séparée par des virgules comme "2,4,7" ou une plage mixte "1-2,5,8-10".

**Q : La bibliothèque prend‑elle en charge les PDF chiffrés ?**  
R : Oui. Fournissez le mot de passe lors de l'ouverture du document ; l'API le déchiffrera automatiquement.

**Q : Comment GroupDocs.Merger gère‑t‑il les images à l'intérieur des PDF ?**  
R : Les images sont conservées exactement comme elles apparaissent sur les pages sélectionnées ; aucune étape de conversion supplémentaire n'est nécessaire.

**Q : Quelles versions de .NET sont officiellement prises en charge ?**  
R : .NET Framework 4.6+, .NET Core 3.1+ et .NET 5/6/7 sont pleinement pris en charge.

## Tutoriels disponibles

### [Extraire des pages spécifiques de documents avec GroupDocs.Merger pour .NET](./extract-pages-groupdocs-merger-net/)
Apprenez à extraire efficacement des pages spécifiques en utilisant GroupDocs.Merger pour .NET. Idéal pour gérer Word, PDF et plus dans des environnements professionnels.

### [Comment extraire des pages spécifiques d'un document en utilisant GroupDocs.Merger pour .NET en C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Apprenez à extraire des pages spécifiques de documents en utilisant GroupDocs.Merger pour .NET avec ce guide complet. Rationalisez vos tâches de gestion de documents sans effort.

## Ressources supplémentaires

- [Documentation GroupDocs.Merger pour .net](https://docs.groupdocs.com/merger/net/)
- [Référence API GroupDocs.Merger pour .net](https://reference.groupdocs.com/merger/net/)
- [Télécharger GroupDocs.Merger pour .net](https://releases.groupdocs.com/merger/net/)
- [Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

---

**Dernière mise à jour :** 2026-08-31  
**Testé avec :** GroupDocs.Merger 23.9 pour .NET  
**Auteur :** GroupDocs

## Tutoriels associés

- [Comment fusionner des pages PDF spécifiques avec GroupDocs.Merger pour .NET : Guide complet](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Comment fusionner des pages spécifiques de plusieurs documents en utilisant GroupDocs.Merger pour .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Faire pivoter des pages PDF dans .NET avec GroupDocs.Merger : Guide étape par étape](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)