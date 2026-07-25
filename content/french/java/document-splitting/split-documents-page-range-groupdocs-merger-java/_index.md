---
date: '2026-07-25'
description: Apprenez à diviser les pages d'un document Word à l'aide de GroupDocs.Merger
  for Java, avec des exemples pas à pas pour PDF, DOCX et PPTX, plus des filtres odd/even
  page.
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Apprenez à diviser les pages d'un document Word à l'aide de GroupDocs.Merger
  for Java, avec des exemples pas à pas pour PDF, DOCX et PPTX, plus des filtres odd/even
  page.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Diviser les pages d'un document Word avec GroupDocs.Merger for Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Diviser les pages d'un document Word avec GroupDocs.Merger for Java
type: docs
url: /fr/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Diviser les pages d'un document Word avec GroupDocs.Merger pour Java

Dans ce tutoriel, vous apprendrez comment **diviser les pages d'un document Word**—et d'autres formats comme PDF et PPTX—en utilisant GroupDocs.Merger pour Java. Que vous ayez besoin d'extraire une clause de contrat unique, de générer des supports à partir d'une présentation, ou de découper un rapport volumineux en morceaux gérables, l'API vous permet de spécifier des plages de pages précises, des filtres impairs/pairs, ou des sorties d'une seule page avec seulement quelques lignes de code.

## Réponses rapides
- **Que signifie « extrait des pages spécifiques » ?** Cela signifie créer de nouveaux documents qui ne contiennent que les pages que vous sélectionnez dans le fichier source.  
- **Quels formats sont pris en charge ?** PDF, DOCX, PPTX, et de nombreux autres formats populaires.  
- **Puis-je filtrer par pages impaires ou paires ?** Oui, en utilisant l'option `RangeMode` (par ex., `OddPages`).  
- **Ai-je besoin d'une licence ?** Un essai gratuit suffit pour l'évaluation ; une licence permanente est requise pour la production.  
- **Est‑il adapté aux gros documents ?** Oui—divisez les sections de gros documents pour maintenir une faible utilisation de la mémoire.

## Qu'est-ce que l'extraction de pages spécifiques ?
L'extraction de pages spécifiques consiste à prendre un sous‑ensemble sélectionné de pages d'un document original et à créer un nouveau fichier indépendant qui ne contient que ces pages. Cette technique est utile pour générer des rapports ciblés, partager des clauses de contrat individuelles, ou distribuer des diapositives de présentation spécifiques sans exposer l'intégralité du document source.

## Pourquoi utiliser GroupDocs.Merger pour Java pour diviser les PDF et les documents Word ?
Chargez uniquement les pages dont vous avez besoin et laissez GroupDocs.Merger gérer le travail lourd. La bibliothèque prend en charge **plus de 50 formats d'entrée et de sortie**, peut traiter des fichiers jusqu'à **2 Go** sans charger le document complet en mémoire, et fournit une API cohérente pour PDF, DOCX, PPTX, et plus encore—vous évitant ainsi de jongler avec plusieurs outils.

## Prérequis
- **GroupDocs.Merger for Java** (dernière version)  
- **JDK 8+**  
- Un IDE tel qu'IntelliJ IDEA ou Eclipse  
- Maven ou Gradle pour la gestion des dépendances  

## Configuration de GroupDocs.Merger pour Java
Ajoutez la bibliothèque à votre projet en utilisant l'outil de construction de votre choix.

**Maven**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Téléchargement direct** : Vous pouvez également télécharger la bibliothèque directement depuis [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisition de licence
Vous pouvez acquérir une licence via :
- **Essai gratuit** – Testez toutes les fonctionnalités sans limitations.  
- **Licence temporaire** – Période d'évaluation prolongée.  
- **Achat** – Licence de production permanente.

**Initialisation et configuration de base**  
La classe `Merger` est le point d'entrée pour toutes les opérations de division. Elle représente un document en mémoire et fournit des méthodes pour manipuler les pages. Pour initialiser GroupDocs.Merger, créez une instance de `Merger` avec le chemin de votre document :  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Comment extraire des pages spécifiques avec GroupDocs.Merger pour Java
Pour extraire des pages spécifiques, chargez le document source avec une instance `Merger`, configurez un objet `SplitOptions` avec les pages de début et de fin souhaitées et, éventuellement, définissez `RangeMode` (par ex., `OddPages` ou `EvenPages`). Ensuite, appelez `merger.split(options)` qui crée de nouveaux fichiers ne contenant que les pages sélectionnées.

### Réponse directe
Créez une instance `Merger`, configurez un objet `SplitOptions` avec `RangeMode.OddPages` et les pages de début/fin souhaitées, puis appelez `merger.split(options)`. Ce flux en une seule étape extrait uniquement les pages impaires de la plage spécifiée et les écrit selon le modèle de sortie que vous fournissez.

### Étape 1 : Définir les chemins d'entrée et de sortie
Définissez le fichier source et le modèle de destination pour les fichiers découpés :  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Étape 2 : Configurer les options de division (Plage & Filtre)
La classe `SplitOptions` indique à la bibliothèque quelles pages extraire et quel filtre appliquer. `RangeMode` est une énumération qui spécifie les pages à inclure, comme impaires, paires ou toutes les pages. La propriété `filePathOut` définit le modèle de nommage, tandis que `startPage` et `endPage` définissent la plage inclusive. `RangeMode.OddPages` ne conserve que les pages impaires de cette plage, extrayant ainsi **des pages spécifiques**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Étape 3 : Effectuer l'opération de division
Exécutez la division en utilisant les options configurées :  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Conseils de dépannage
- Vérifiez que les chemins de fichiers sont corrects et accessibles.  
- Assurez‑vous que les numéros de page sont compris dans le nombre total de pages du document ; sinon une exception sera levée.  

## Comment diviser un PDF en pages individuelles (split pdf single pages)
Pour diviser un PDF en pages individuelles, ouvrez le fichier avec une instance `Merger` et définissez `RangeMode.AllPages` dans un objet `SplitOptions`. Spécifiez un modèle de nommage de sortie, puis invoquez `merger.split(options)`. La bibliothèque générera un fichier PDF distinct pour chaque page, en préservant le contenu et la mise en forme d'origine.

## Comment diviser efficacement un gros document (split large document)
Lors du traitement de très gros documents, divisez-les en petites plages de pages (par ex., 1‑100, 101‑200) pour réduire la consommation de mémoire. Créez des `SplitOptions` séparés pour chaque plage, exécutez `merger.split(options)` séquentiellement, et fermez l'instance `Merger` après chaque lot. Cette approche maintient une utilisation gérable du CPU et des entrées/sorties.

## Comment diviser les pages impaires d'un PDF (split pdf odd pages)
Pour extraire uniquement les pages impaires d'un PDF, configurez un objet `SplitOptions` avec `RangeMode.OddPages`. Définissez le modèle de sortie souhaité et, éventuellement, spécifiez une plage de pages si vous n'avez pas besoin de l'ensemble du document. Appelez `merger.split(options)` et la bibliothèque produira des fichiers ne contenant que les pages impaires.

## Applications pratiques
1. **Segmentation de documents** – Découpez les contrats en PDF au niveau des clauses pour une révision plus facile.  
2. **Gestion de rapports** – Extrayez un chapitre ou une annexe spécifique d'un rapport annuel volumineux.  
3. **Préparation de présentations** – Isolez des diapositives individuelles pour des réunions ciblées.  

Vous pouvez également intégrer cette logique avec des bases de données ou des systèmes de gestion de contenu pour automatiser les pipelines de flux de travail.

## Considérations de performance
- **Gestion de la mémoire** – Appelez `merger.close()` (ou comptez sur try‑with‑resources) après le traitement pour libérer les descripteurs de fichiers.  
- **Plages sélectives** – Demandez uniquement les pages dont vous avez réellement besoin ; cela minimise l'utilisation du CPU et des I/O.

## Conclusion
Vous disposez maintenant d'une méthode claire, étape par étape, pour **diviser les pages d'un document Word** (et d'autres formats pris en charge) en utilisant GroupDocs.Merger pour Java. Cette capacité simplifie vos flux de travail documentaires et vous permet de fournir exactement le contenu dont vos utilisateurs ont besoin.

### Prochaines étapes
- Expérimentez avec différentes valeurs de `RangeMode` (par ex., `EvenPages`, `AllPages`).  
- Combinez la division avec la fonctionnalité de **fusion** pour réorganiser ou concaténer les pages extraites.  
- Explorez l'API complète pour les documents protégés par mot de passe, les filigranes, et plus encore.  

## Questions fréquentes
**Q : Qu'est‑ce que GroupDocs.Merger pour Java ?**  
R : GroupDocs.Merger pour Java est une bibliothèque robuste qui permet de fusionner, diviser et réorganiser les pages de nombreux formats de documents, y compris PDF, DOCX et PPTX.

**Q : Puis‑je utiliser GroupDocs.Merger avec d'autres langages de programmation ?**  
R : Oui, des capacités similaires existent pour .NET et C++.

**Q : Comment gérer les exceptions lors du traitement de documents ?**  
R : `MergerException` est le type d'exception lancé par GroupDocs.Merger lorsqu'une erreur de traitement se produit. Enveloppez les appels dans des blocs `try‑catch` et examinez `MergerException` pour obtenir des informations détaillées sur l'erreur.

**Q : Est‑il possible de diviser des documents sans filtrer par pages impaires/paires ?**  
R : Absolument—définissez `RangeMode.AllPages` ou omettez le paramètre de filtre pour diviser selon des numéros de pages exacts.

**Q : Quelles sont les exigences système pour utiliser GroupDocs.Merger ?**  
R : Java 8 ou supérieur et un IDE compatible ; aucune dépendance native supplémentaire n'est requise.

## Ressources
- [Documentation GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Référence API](https://reference.groupdocs.com/merger/java/)
- [Télécharger la bibliothèque](https://releases.groupdocs.com/merger/java/)
- [Acheter une licence](https://purchase.groupdocs.com/buy)
- [Essai gratuit et licence temporaire](https://releases.groupdocs.com/merger/java/)
- [Forum d'assistance](https://forum.groupdocs.com/c/merger/)

---

**Dernière mise à jour** : 2026-07-25  
**Testé avec** : dernière version de GroupDocs.Merger (Java)  
**Auteur** : GroupDocs

## Tutoriels associés

- [Supprimer efficacement des pages de documents Word avec GroupDocs.Merger pour Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Gestion maîtresse de documents – Fusionner des documents Word avec GroupDocs.Merger pour Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Comment diviser des documents en fichiers multi‑pages avec GroupDocs.Merger pour Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)