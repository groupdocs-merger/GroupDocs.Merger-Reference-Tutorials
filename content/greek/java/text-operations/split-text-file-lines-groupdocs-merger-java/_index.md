---
date: '2026-08-26'
description: Μάθετε πώς να διαιρείτε μεγάλο αρχείο κειμένου σε ξεχωριστά έγγραφα γραμμής
  με το GroupDocs Merger for Java, να εξάγετε γραμμές από το κείμενο και να διαχειρίζεστε
  μεγάλα αρχεία αποδοτικά.
keywords:
- split large text file
- extract lines from text
- java split file lines
- manage large text files
- text file line splitting
lastmod: '2026-08-26'
og_description: Διαίρεση μεγάλου αρχείου κειμένου σε έγγραφα γραμμής με το GroupDocs
  Merger for Java. Ακολουθήστε αυτόν τον οδηγό βήμα-προς-βήμα για να εξάγετε γραμμές
  από το κείμενο και να βελτιώσετε τη διαχείριση των δεδομένων.
og_image_alt: Developer guide showing how to split a large text file into separate
  line documents using GroupDocs Merger for Java
og_title: Διαίρεση μεγάλου αρχείου κειμένου σε γραμμές με το GroupDocs Merger Java
schemas:
- author: GroupDocs
  dateModified: '2026-08-26'
  description: Learn how to split large text file into separate line documents with
    GroupDocs Merger for Java, extract lines from text and manage huge files efficiently.
  headline: Split large text file into lines using GroupDocs Merger Java
  type: TechArticle
- description: Learn how to split large text file into separate line documents with
    GroupDocs Merger for Java, extract lines from text and manage huge files efficiently.
  name: Split large text file into lines using GroupDocs Merger Java
  steps:
  - name: import necessary packages
    text: '`Merger`, `TextSplitOptions`, and standard I/O classes must be imported
      before any processing.'
  - name: define file paths
    text: Specify the absolute or relative paths for the source text file and the
      output directory where each line will be saved.
  - name: create a Merger instance
    text: The `Merger` class is the entry point for all document operations in GroupDocs
      Merger.
  - name: configure split options
    text: '`TextSplitOptions` lets you control line delimiters, output naming, and
      whether to overwrite existing files.'
  - name: perform the split operation
    text: Call the `split` method with the output folder, overwrite flag, and desired
      file extension. The method returns a collection of generated file paths, which
      you can log or further process. **Parameters explained** - **Output folder**
      – where each line document will be written. - **Overwrite flag** – `
  type: HowTo
- questions:
  - answer: The out‑of‑the‑box API splits by line delimiters, but you can supply a
      custom delimiter (e.g., `"\n\n"`) to treat blank‑line separated paragraphs as
      split units.
    question: Can I split a file into paragraphs instead of lines?
  - answer: A free trial is available for evaluation; a paid license is required for
      production deployments.
    question: Is GroupDocs Merger free for commercial projects?
  - answer: The library automatically detects UTF‑8 encoding; you can also specify
      a different charset in the `Merger` constructor if needed.
    question: What if my text file contains Unicode characters?
  - answer: It streams each line to disk, keeping memory usage under 100 MB regardless
      of source size, which makes it suitable for multi‑GB files.
    question: How does the splitter handle extremely large files (multi‑GB)?
  - answer: Yes – you can output each line as PDF, DOCX, HTML, or any of the 50+ formats
      listed in the product documentation.
    question: Does the API support other formats besides TXT?
  type: FAQPage
tags:
- split large text file
- GroupDocs Merger
- Java file processing
title: Διαίρεση μεγάλου αρχείου κειμένου σε γραμμές με το GroupDocs Merger Java
type: docs
url: /el/java/text-operations/split-text-file-lines-groupdocs-merger-java/
weight: 1
---

# Διαχωρισμός μεγάλου αρχείου κειμένου σε γραμμές χρησιμοποιώντας το GroupDocs Merger Java

Σε αυτό το σεμινάριο θα ανακαλύψετε πώς να **διαχωρίσετε το περιεχόμενο μεγάλου αρχείου κειμένου** σε μεμονωμένα έγγραφα βασισμένα σε γραμμές με το GroupDocs Merger for Java. Είτε επεξεργάζεστε αρχεία καταγραφής, εξαγωγές CSV, ή οποιαδήποτε τεράστια πηγή απλού κειμένου, η διάσπαση του αρχείου σε διαχειρίσιμα κομμάτια καθιστά την ανάλυση, την παράλληλη επεξεργασία και την αποθήκευση πολύ πιο εύκολη.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη διαχειρίζεται το διαχωρισμό;** GroupDocs Merger for Java.  
- **Πόσες γραμμές μπορούν να επεξεργαστούν;** Μπορεί να χειριστεί αρχεία με εκατομμύρια γραμμές· το API μεταδίδει δεδομένα έτσι ώστε η χρήση μνήμης να παραμένει χαμηλή.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για αξιολόγηση· απαιτείται εμπορική άδεια για παραγωγή.  
- **Ποια έκδοση της Java απαιτείται;** JDK 8 ή νεότερη.  
- **Μπορώ να αλλάξω τη μορφή εξόδου;** Ναι – μπορείτε να εξάγετε κάθε γραμμή ως TXT, PDF, DOCX ή οποιαδήποτε από τις 50+ υποστηριζόμενες μορφές.

## Τι είναι το διαχωρισμός μεγάλου αρχείου κειμένου;
Ο διαχωρισμός ενός μεγάλου αρχείου κειμένου σημαίνει την ανάγνωση κάθε γραμμής και την εγγραφή της σε ξεχωριστό έγγραφο, επιτρέποντας ανεξάρτητη διαχείριση κάθε εγγραφής. Αυτή η προσέγγιση μειώνει την πίεση στη μνήμη και επιτρέπει παράλληλες ροές εργασίας.

## Γιατί να χρησιμοποιήσετε το GroupDocs Merger for Java;
Το GroupDocs Merger υποστηρίζει **50+ μορφές εισόδου και εξόδου**, επεξεργάζεται έγγραφα με εκατοντάδες σελίδες χωρίς να φορτώνει ολόκληρο το αρχείο στη μνήμη, και παρέχει ενσωματωμένη ροή δεδομένων για να διατηρεί τη χρήση του σωρού κάτω από 100 MB ακόμη και για αρχεία μεγαλύτερα από 2 GB. Αυτά τα μετρήσιμα οφέλη το καθιστούν κορυφαία επιλογή για επεξεργασία κειμένου επιχειρησιακού επιπέδου.

## Προαπαιτούμενα
- **Java Development Kit (JDK)** 8 ή νεότερο εγκατεστημένο.  
- **Εργαλείο κατασκευής** – Maven ή Gradle για διαχείριση εξαρτήσεων.  
- **Βιβλιοθήκη GroupDocs Merger for Java** (λήψη μέσω Maven/Gradle ή χειροκίνητο JAR).  

### Απαιτούμενες βιβλιοθήκες και εξαρτήσεις
Προσθέστε το GroupDocs Merger στο έργο σας:

**Maven:**  

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/). Για περισσότερες πληροφορίες, δείτε τον άλλο σύνδεσμο [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/) link.

### Βήματα απόκτησης άδειας
1. **Δωρεάν δοκιμή** – δοκιμάστε όλες τις λειτουργίες χωρίς κόστος.  
2. **Προσωρινή άδεια** – ζητήστε ένα βραχυπρόθεσμο κλειδί από τη [temporary license page](https://purchase.groupdocs.com/temporary-license/) εάν υπερβείτε τα όρια της δοκιμής.  
3. **Αγορά** – αποκτήστε πλήρη άδεια στη [GroupDocs' purchase page](https://purchase.groupdocs.com/buy) για απεριόριστη χρήση σε παραγωγή. Μπορείτε επίσης να επισκεφθείτε το [GroupDocs' purchase site](https://purchase.groupdocs.com/buy) για λεπτομέρειες τιμολόγησης.

## Πώς να διαχωρίσετε ένα μεγάλο αρχείο κειμένου σε έγγραφα γραμμής χρησιμοποιώντας το GroupDocs Merger;
Φορτώστε το αρχείο προέλευσης, διαμορφώστε το `TextSplitOptions` και καλέστε τη μέθοδο `split`. Το API μεταδίδει κάθε γραμμή, την γράφει στον φάκελο προορισμού και απελευθερώνει τους πόρους αυτόματα, έτσι ακόμη και αρχεία με εκατομμύρια γραμμές επεξεργάζονται αποδοτικά. Χρησιμοποιώντας την προσέγγιση ροής, η κατανάλωση μνήμης παραμένει κάτω από 100 MB, και η λειτουργία μπορεί να παραλληλοποιηθεί σε πολλούς πυρήνες CPU για ταχύτερη επεξεργασία μεγάλων συνόλων δεδομένων.

### Βήμα 1: εισαγωγή απαραίτητων πακέτων
`Merger`, `TextSplitOptions` και οι τυπικές κλάσεις I/O πρέπει να εισαχθούν πριν από οποιαδήποτε επεξεργασία.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger("path/to/your/file.txt");
```

### Βήμα 2: ορισμός διαδρομών αρχείων
Καθορίστε τις απόλυτες ή σχετικές διαδρομές για το αρχείο κειμένου προέλευσης και τον φάκελο εξόδου όπου θα αποθηκευτεί κάθε γραμμή.

```java
import com.groupdocs.merger.Merger;

Merger merger = new Merger("path/to/your/file.txt");
```

### Βήμα 3: δημιουργία ενός αντικειμένου Merger
Η κλάση `Merger` είναι το σημείο εισόδου για όλες τις λειτουργίες εγγράφων στο GroupDocs Merger.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.TextSplitOptions;
import java.io.File;
import java.nio.file.Paths;
```

### Βήμα 4: διαμόρφωση επιλογών διαχωρισμού
`TextSplitOptions` σας επιτρέπει να ελέγξετε τους οριοθέτες γραμμών, την ονομασία εξόδου και αν θα αντικατασταθούν υπάρχοντα αρχεία.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/";
```

### Βήμα 5: εκτέλεση της λειτουργίας διαχωρισμού
Καλέστε τη μέθοδο `split` με το φάκελο εξόδου, τη σημαία αντικατάστασης και την επιθυμητή επέκταση αρχείου. Η μέθοδος επιστρέφει μια συλλογή από δημιουργημένες διαδρομές αρχείων, τις οποίες μπορείτε να καταγράψετε ή να επεξεργαστείτε περαιτέρω.

```java
Merger merger = new Merger(filePath);
```

**Παράμετροι εξήγηση**  
- **Φάκελος εξόδου** – όπου θα γραφτεί κάθε έγγραφο γραμμής.  
- **Σημαία αντικατάστασης** – `true` αντικαθιστά υπάρχοντα αρχεία με το ίδιο όνομα.  
- **Επέκταση αρχείου** – επιλέξτε `".txt"` για απλό κείμενο ή `".pdf"` για PDF ανά γραμμή.

## Συνηθισμένα προβλήματα και λύσεις
- **Σφάλματα διαδρομής αρχείου** – ελέγξτε ξανά ότι το αρχείο εισόδου υπάρχει και ότι ο φάκελος εξόδου είναι εγγράψιμος.  
- **Προβλήματα δικαιωμάτων** – εκτελέστε το JVM με επαρκή δικαιώματα λειτουργικού συστήματος ή προσαρμόστε τα ACL του φακέλου.  
- **Συγκρούσεις εκδόσεων** – βεβαιωθείτε ότι η έκδοση του GroupDocs Merger JAR ταιριάζει με τις άλλες εξαρτήσεις σας· χρησιμοποιήστε την ίδια κύρια έκδοση σε όλο το στοίβα.

## Πρακτικές εφαρμογές
Ο διαχωρισμός μεγάλων αρχείων κειμένου σε έγγραφα βασισμένα σε γραμμές είναι χρήσιμος για:
1. **Σωλήνες επεξεργασίας δεδομένων** – τροφοδοτήστε κάθε γραμμή σε ξεχωριστή μικροϋπηρεσία ή εργασία Spark.  
2. **Διαχείριση αρχείων καταγραφής** – αρχειοθετήστε κάθε καταγραφή ως ξεχωριστό αρχείο για γρήγορη ανάκτηση και ελέγχους συμμόρφωσης.  
3. **Κατανομή περιεχομένου** – μετατρέψτε ένα τεράστιο προσχέδιο άρθρου σε αποσπάσματα ανά πρόταση ή ανά γραμμή για πλατφόρμες συνεργατικής επεξεργασίας.

## Σκέψεις απόδοσης
Κατά τη διαχείριση πολύ μεγάλων αρχείων:
- **Βελτιστοποίηση μνήμης** – βασιστείτε στο streaming API του GroupDocs Merger· αποφύγετε τη φόρτωση ολόκληρου του αρχείου σε `String`.  
- **Επεξεργασία σε παρτίδες** – διαχωρίστε τα αρχεία σε τμήματα (π.χ., 10 000 γραμμές ανά παρτίδα) για ομαλή λειτουργία I/O δίσκου.  
- **Ρύθμιση JVM** – αυξήστε το heap (`-Xmx2g`) μόνο εάν σχεδιάζετε επιπλέον επεξεργασία στη μνήμη πέρα από τη λειτουργία διαχωρισμού.

## Συμπέρασμα
Τώρα ξέρετε πώς να **διαχωρίσετε το περιεχόμενο μεγάλου αρχείου κειμένου** σε ξεχωριστά έγγραφα γραμμής χρησιμοποιώντας το GroupDocs Merger for Java. Αυτή η τεχνική βελτιώνει την κλιμακωσιμότητα, επιτρέπει την παράλληλη επεξεργασία και απλοποιεί τη διαχείριση των δεδομένων στο downstream.

### Επόμενα βήματα
- Πειραματιστείτε με άλλες μορφές εξόδου όπως PDF ή DOCX αλλάζοντας την επέκταση αρχείου στο `TextSplitOptions`.  
- Συνδυάστε τη λειτουργία διαχωρισμού με τις δυνατότητες **merge** και **watermark** του GroupDocs Merger για να δημιουργήσετε ολοκληρωμένες ροές εργασίας εγγράφων.  
- Ενσωματώστε τη λύση σε υπηρεσία Spring Boot ή σε λειτουργία serverless για αυτοματοποιημένες ροές επεξεργασίας.

## Συχνές ερωτήσεις

**Q: Μπορώ να διαχωρίσω ένα αρχείο σε παραγράφους αντί για γραμμές;**  
A: Το έτοιμο API διαχωρίζει με βάση τους οριοθέτες γραμμής, αλλά μπορείτε να παρέχετε έναν προσαρμοσμένο οριοθέτη (π.χ., `"\n\n"`) για να αντιμετωπίσετε τις παραγράφους που χωρίζονται με κενές γραμμές ως μονάδες διαχωρισμού.

**Q: Είναι το GroupDocs Merger δωρεάν για εμπορικά έργα;**  
A: Μια δωρεάν δοκιμή είναι διαθέσιμη για αξιολόγηση· απαιτείται πληρωμένη άδεια για παραγωγικές εγκαταστάσεις.

**Q: Τι γίνεται αν το αρχείο κειμένου περιέχει χαρακτήρες Unicode;**  
A: Η βιβλιοθήκη ανιχνεύει αυτόματα την κωδικοποίηση UTF‑8· μπορείτε επίσης να καθορίσετε διαφορετικό charset στον κατασκευαστή `Merger` αν χρειάζεται.

**Q: Πώς διαχειρίζεται ο διαχωριστής εξαιρετικά μεγάλα αρχεία (πολλαπλά GB);**  
A: Μεταδίδει κάθε γραμμή στο δίσκο, διατηρώντας τη χρήση μνήμης κάτω από 100 MB ανεξαρτήτως μεγέθους πηγής, κάτι που το καθιστά κατάλληλο για αρχεία πολλαπλών GB.

**Q: Υποστηρίζει το API άλλες μορφές εκτός από TXT;**  
A: Ναι – μπορείτε να εξάγετε κάθε γραμμή ως PDF, DOCX, HTML ή οποιαδήποτε από τις 50+ μορφές που αναφέρονται στην τεκμηρίωση του προϊόντος.

## Πόροι
- **Τεκμηρίωση**: [GroupDocs Merger for Java Documentation](https://docs.groupdocs.com/merger/java)

---

**Τελευταία ενημέρωση:** 2026-08-26  
**Δοκιμή με:** GroupDocs Merger 23.11 for Java  
**Συγγραφέας:** GroupDocs

```java
// Create TextSplitOptions instance specifying mode to split by lines.
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, true, true);
```

```java
merger.split(splitOptions);
```

## Σχετικά Μαθήματα

- [Πώς να διαχωρίσετε αρχείο ανά γραμμές με το GroupDocs.Merger for Java](/merger/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/)
- [java συγχώνευση αρχείων κειμένου με το GroupDocs.Merger for Java](/merger/java/document-joining/merge-txt-files-groupdocs-merger-java/)
- [Πώς να ανακτήσετε τους υποστηριζόμενους τύπους αρχείων χρησιμοποιώντας το GroupDocs.Merger for Java](/merger/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/)