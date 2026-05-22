---
date: 2026-05-22
description: Apprenez à créer des fichiers PDF à page unique et à diviser des PDF
  en utilisant GroupDocs.Merger pour Java. Inclut des guides étape par étape pour
  split pdf java et plus encore.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: Créer un PDF à page unique avec GroupDocs.Merger Java
type: docs
url: /fr/java/document-splitting/
weight: 12
---

# Créer un PDF d'une seule page avec GroupDocs.Merger Java

Si vous devez **créer des PDF d'une seule page** à partir de documents plus volumineux ou simplement diviser les PDF en morceaux plus faciles à gérer, vous êtes au bon endroit. Ce guide vous présente les scénarios de division les plus courants — fichiers multi‑pages, plages de pages, pages impaires/paires, division de DOCX, et même divisions basées sur du texte — en utilisant la puissante bibliothèque GroupDocs.Merger pour Java. À la fin de ce tutoriel, vous saurez exactement comment intégrer ces techniques dans vos propres applications, améliorer les performances de gestion des documents et garder votre base de code propre et maintenable.

## Réponses rapides
- **Que signifie “create single page PDF” ?** Cela signifie extraire une page d'un document source et l'enregistrer en tant que fichier PDF indépendant.  
- **Quelle bibliothèque gère la tâche ?** GroupDocs.Merger for Java fournit une API fluide pour toutes les opérations de division.  
- **Ai‑je besoin d'une licence ?** Une licence temporaire fonctionne pour le développement ; une licence complète est requise pour la production.  
- **Puis‑je diviser les pages impaires et paires d'un PDF ?** Oui — GroupDocs.Merger vous permet de filtrer les pages par numéros impairs/pairs.  
- **La division de DOCX est‑elle prise en charge ?** Absolument ; vous pouvez diviser les fichiers DOCX page par page ou par plages personnalisées.  

## Qu’est‑ce que “create single page PDF” ?
Créer un PDF d’une seule page consiste à prendre un document source multi‑pages (PDF, DOCX, PPTX, etc.) et à extraire une seule page dans son propre fichier PDF. Cela est utile pour générer des factures, des certificats ou des images d’aperçu où seule une page spécifique est requise.

## Pourquoi utiliser GroupDocs.Merger pour Java ?
GroupDocs.Merger pour Java propose une API unique et cohérente qui gère de nombreux formats de documents tout en offrant des performances élevées et une faible consommation de mémoire. Elle simplifie le développement en abstraisant la gestion complexe des fichiers, vous permettant de vous concentrer sur la logique métier plutôt que sur les détails de traitement de bas niveau.

- **API unifiée** – Fonctionne avec PDF, DOCX, PPTX, images et de nombreux autres formats.  
- **Haute performance** – Optimisé pour les gros fichiers et les opérations par lots ; il peut traiter des documents jusqu’à 2 Go sans charger le fichier complet en mémoire.  
- **Contrôle granulaire** – Division par plage de pages, pages impaires/paires ou délimiteurs personnalisés.  
- **Compatible flux** – La sortie peut être enregistrée dans un fichier ou renvoyée sous forme de flux pour les services web.

## Prérequis
- Java 8 ou version supérieure.  
- GroupDocs.Merger pour Java ajouté à votre projet (Maven/Gradle).  
- Un fichier de licence GroupDocs valide (temporaire ou complet).

## Comment créer un PDF d’une seule page ?
Créer un PDF d’une seule page avec GroupDocs.Merger consiste à charger le fichier source, spécifier la page ou la plage exacte, invoquer l’opération de division, puis persister le résultat. Ce flux de travail garantit que le document original reste intact tandis que la page extraite est enregistrée en tant que fichier PDF indépendant.

La classe `Merger` est le composant principal qui charge les documents source et fournit la fonctionnalité de division.

### Étape 1 : Initialiser le Merger
La classe `Merger` est le composant principal de GroupDocs.Merger qui charge un document source et fournit des opérations de division. Créez une instance en passant le chemin du fichier ou un flux d’entrée.

### Étape 2 : Définir les critères de division
Choisissez le numéro de page exact ou la plage dont vous avez besoin. Pour une extraction d’une seule page, vous spécifierez une plage comme `1‑1`. Lorsque vous devez **split pdf by range**, vous pouvez passer plusieurs plages telles que `1‑5, 6‑10`.

### Étape 3 : Exécuter la division
Appelez la méthode `split` appropriée. Par exemple, `merger.split(new int[]{1})` extrait la première page, tandis que `merger.splitByRange(new int[][]{{1,5},{6,10}})` gère plusieurs plages en un seul appel.

### Étape 4 : Enregistrer le résultat
Écrivez chaque sortie vers un chemin de fichier ou renvoyez‑la sous forme de `java.io.InputStream`. Cela facilite l’intégration avec les API web ou le stockage du résultat dans le cloud.

> **Astuce :** Lors du traitement de gros PDF, appelez `merger.setOptimizeResources(true)` avant la division pour réduire la consommation de mémoire.

## Comment diviser les fichiers PDF java en plusieurs pages
La classe `Merger` fournit l’API principale pour charger et manipuler les fichiers PDF. Pour diviser un PDF en fichiers d’une page distincts, il suffit de charger le document avec l’instance Merger et d’appeler la méthode split sans paramètres. La bibliothèque crée automatiquement un nouveau PDF pour chaque page, en préservant le contenu et les métadonnées d’origine, ce qui est idéal pour le traitement par lots de factures ou de rapports.

## Comment diviser les pages impaires et paires d’un PDF
La classe `Merger` est le composant principal qui exécute les opérations de division sur les documents. Lorsque vous avez besoin uniquement des pages impaires ou paires d’un PDF, fournissez une liste des numéros de pages souhaités à la fonction split. Le Merger générera un nouveau document contenant uniquement ces pages, vous permettant de créer rapidement des fichiers séparés pour le contenu impairs ou pairs.

## Comment diviser les fichiers docx (how to split docx)
La classe `Merger` fonctionne également avec les fichiers DOCX. Utilisez `splitByPage` pour générer un DOCX (ou PDF) par page, ou combinez‑le avec `saveAsPdf` si vous avez besoin d’une sortie PDF. Cela couvre le flux de travail de conversion **docx to pdf java** en une seule étape.

## Comment diviser les documents en fichiers multi‑pages
La classe `Merger` gère la pagination et la création de fichiers pour les opérations de division. Si vous préférez découper un grand document en morceaux de taille fixe, spécifiez le nombre de pages par fichier de sortie. Le Merger parcourra la source, créant de nouveaux PDF contenant chacun le nombre de pages défini, ce qui simplifie l’archivage, la distribution et le traitement parallèle de documents volumineux.

## Tutoriels disponibles

### [Comment diviser les documents en fichiers multi‑pages avec GroupDocs.Merger pour Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Apprenez à diviser efficacement de gros documents en fichiers plus petits et multi‑pages en utilisant GroupDocs.Merger pour Java. Optimisez la gestion des documents en toute simplicité.

### [Comment diviser un fichier texte par intervalles de lignes avec GroupDocs.Merger pour Java | Guide de division de documents](./split-text-file-line-intervals-groupdocs-merger-java/)
Apprenez à diviser les fichiers texte en sections gérables en utilisant des intervalles de lignes avec GroupDocs.Merger pour Java. Un guide complet pour une gestion efficace des documents.

### [Maîtriser la division de documents par plage de pages avec GroupDocs.Merger pour Java](./split-documents-page-range-groupdocs-merger-java/)
Apprenez à diviser les documents en plages de pages spécifiques en utilisant GroupDocs.Merger pour Java. Rationalisez la gestion des documents et appliquez des filtres comme les pages impaires/paires.

### [Maîtriser la division de documents avec GroupDocs.Merger : Un guide complet](./master-document-splitting-groupdocs-merger-java/)
Apprenez à diviser efficacement les documents en pages uniques en utilisant GroupDocs.Merger pour Java. Ce guide couvre l’installation, la mise en œuvre et les applications pratiques.

### [Maîtriser la division de documents Java avec GroupDocs.Merger : Diviser les pages DOCX en fichiers et flux](./master-java-document-splitting-groupdocs-merger/)
Apprenez à diviser efficacement les documents DOCX en pages séparées ou en flux en utilisant GroupDocs.Merger pour Java. Ce guide couvre l’installation, la mise en œuvre et les applications pratiques.

## Ressources supplémentaires

- [Documentation GroupDocs.Merger pour Java](https://docs.groupdocs.com/merger/java/)
- [Référence API GroupDocs.Merger pour Java](https://reference.groupdocs.com/merger/java/)
- [Télécharger GroupDocs.Merger pour Java](https://releases.groupdocs.com/merger/java/)
- [Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Support gratuit](https://forum.groupdocs.com/)
- [Licence temporaire](https://purchase.groupdocs.com/temporary-license/)

## Problèmes courants et solutions

| Problème | Solution |
|----------|----------|
| **Surcharge mémoire sur de gros PDF** | Activez l’optimisation des ressources : `merger.setOptimizeResources(true);` |
| **Numéros de page incorrects après la division** | Rappelez‑vous que l’indexation des pages commence à 1, pas à 0. |
| **Licence introuvable** | Vérifiez le chemin vers votre fichier `GroupDocs.Merger.lic` et assurez‑vous qu’il est inclus dans le classpath. |
| **La division de DOCX donne des pages vides** | Assurez‑vous que le DOCX source possède des sauts de page appropriés ; sinon, utilisez `splitByParagraph` comme solution de secours. |

## Questions fréquentes

**Q : Puis‑je diviser un PDF protégé par mot de passe ?**  
R : Oui. Chargez le document avec le paramètre du mot de passe, puis effectuez toute opération de division comme d’habitude.

**Q : Comment diviser uniquement les pages impaires d’un PDF ?**  
R : Fournissez une liste de pages contenant uniquement les nombres impairs (par ex., 1,3,5…) à la méthode `split`.

**Q : Est‑il possible de diviser directement un DOCX en PDF ?**  
R : Absolument. Après avoir chargé le DOCX, appelez `saveAsPdf` sur chaque segment divisé.

**Q : Quels formats GroupDocs.Merger prend‑il en charge pour la division ?**  
R : PDF, DOCX, PPTX, TXT, HTML et de nombreux formats d’image (PNG, JPEG, etc.).

**Q : Ai‑je besoin d’une licence séparée pour chaque type de fichier ?**  
R : Non. Une seule licence GroupDocs.Merger couvre tous les formats pris en charge.

**Dernière mise à jour :** 2026-05-22  
**Testé avec :** GroupDocs.Merger 23.11 pour Java  
**Auteur :** GroupDocs

## Tutoriels associés

- [split pdf java : Division de documents avec GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Maîtriser la division de documents par plage de pages avec GroupDocs.Merger pour Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Fusionner efficacement des PDF avec GroupDocs.Merger pour Java : Guide étape par étape](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)