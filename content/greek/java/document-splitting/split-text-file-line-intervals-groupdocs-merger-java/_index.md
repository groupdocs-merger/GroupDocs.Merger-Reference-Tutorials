---
date: '2026-07-25'
description: Μάθετε πώς να χωρίσετε ένα αρχείο ανά γραμμές χρησιμοποιώντας το GroupDocs.Merger
  for Java – ένας οδηγός βήμα‑βήμα για αποδοτικό διαχωρισμό εγγράφων σε έργα Java.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Διαχωρίστε ένα αρχείο ανά γραμμές χρησιμοποιώντας το GroupDocs.Merger
  for Java. Αυτός ο οδηγός δείχνει πώς να χωρίσετε γρήγορα μεγάλα αρχεία κειμένου
  σε μέρη, με παραδείγματα κώδικα και συμβουλές βέλτιστων πρακτικών.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Διαχωρισμός αρχείου ανά γραμμές με το GroupDocs.Merger for Java – Γρήγορα
  & Εύκολα
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: Πώς να χωρίσετε ένα αρχείο ανά γραμμές με το GroupDocs.Merger for Java
type: docs
url: /el/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Πώς να Διαχωρίσετε Αρχείο ανά Γραμμές με το GroupDocs.Merger για Java

Αν χρειάζεστε **διαχωρισμό αρχείου ανά γραμμές**—για παράδειγμα, για να χωρίσετε ένα τεράστιο αρχείο καταγραφής σε μικρά κομμάτια, να τροφοδοτήσετε παρτίδες δεδομένων σε μια γραμμή επεξεργασίας ή να μετατρέψετε μια μακρά αναφορά σε ξεχωριστά αρχεία κεφαλαίων—αυτό το σεμινάριο σας δείχνει ακριβώς πώς να το κάνετε με το GroupDocs.Merger για Java. Θα δείτε γιατί η βιβλιοθήκη εξοικονομεί χρόνο, θα λάβετε μια έτοιμη υλοποίηση και θα μάθετε πρακτικές συμβουλές που διατηρούν την εφαρμογή σας γρήγορη και αξιόπιστη.

## Γρήγορες Απαντήσεις
- **Τι σημαίνει το «διαχωρισμός αρχείου ανά γραμμές»;** Δημιουργεί ξεχωριστά αρχεία κειμένου που το καθένα περιέχει ένα καθορισμένο εύρος αριθμών γραμμών από το αρχικό έγγραφο.  
- **Ποια βιβλιοθήκη διαχειρίζεται το διαχωρισμό;** Το GroupDocs.Merger για Java παρέχει ένα απλό API για διαχωρισμό με βάση τα διαστήματα γραμμών.  
- **Χρειάζομαι άδεια;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται μόνιμη άδεια για χρήση σε παραγωγή.  
- **Μπορώ να διαχωρίσω με βάση τον αριθμό χαρακτήρων αντί για γραμμές;** Δεν είναι άμεσα· χρησιμοποιήστε ένα βήμα προεπεξεργασίας για να αναδιαμορφώσετε το αρχείο πριν το διαχωρισμό.  
- **Ποια έκδοση της Java υποστηρίζεται;** Οποιοδήποτε runtime Java 8+ είναι συμβατό.

## Τι είναι το «διαχωρισμός αρχείου ανά γραμμές»;
**Διαχωρισμός αρχείου ανά γραμμές** σημαίνει τη λήψη ενός ενιαίου εγγράφου κειμένου και τον διαχωρισμό του σε πολλαπλά αρχεία, το καθένα περιέχοντας ένα συγκεκριμένο εύρος διαδοχικών γραμμών (π.χ., γραμμές 1‑3, 4‑6, κλπ.). Αυτή η προσέγγιση είναι ιδανική όταν θέλετε να επεξεργαστείτε δεδομένα παράλληλα, να μειώσετε την πίεση μνήμης ή απλώς να κάνετε τα μεγάλα αρχεία πιο εύκολα στην πλοήγηση.

## Γιατί να Χρησιμοποιήσετε το GroupDocs.Merger για Java;
Το GroupDocs.Merger αφαιρεί την πολυπλοκότητα του χαμηλού επιπέδου file‑I/O, επιτρέποντάς σας να εστιάσετε στη λογική της επιχείρησης. Διαχειρίζεται αποδοτικά αρχεία έως 2 GB χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη, υποστηρίζει **70+** μορφές εισόδου και εξόδου, και παρέχει ένα ευέλικτο API που ενσωματώνεται ομαλά με τις κατασκευές Maven ή Gradle. Η χρήση αυτής της βιβλιοθήκης μειώνει τον χρόνο ανάπτυξης έως και **80 %** σε σύγκριση με χειροκίνητους βρόχους I/O.

## Προαπαιτούμενα
- **Java Development Kit (JDK) 8 ή νεότερο** – βεβαιωθείτε ότι τα `java` και `javac` βρίσκονται στο PATH σας.  
- **GroupDocs.Merger για Java** – προσθέστε τη βιβλιοθήκη μέσω Maven, Gradle ή άμεσης λήψης.  
- **Βασικές γνώσεις Java** – πρέπει να είστε άνετοι με κλάσεις, μεθόδους και διαχείριση εξαιρέσεων.

## Ρύθμιση του GroupDocs.Merger για Java
Προσθέστε τη βιβλιοθήκη στο έργο σας χρησιμοποιώντας μία από τις παρακάτω μεθόδους.

**Maven** – επικολλήστε αυτήν την εξάρτηση στο `pom.xml` σας:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – προσθέστε την παρακάτω γραμμή στο `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Άμεση Λήψη** – μπορείτε επίσης να κατεβάσετε το JAR από την επίσημη σελίδα κυκλοφορίας: [Κυκλοφορίες GroupDocs.Merger για Java](https://releases.groupdocs.com/merger/java/).

### Απόκτηση Άδειας
Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε το API. Για παραγωγικά φορτία εργασίας, αποκτήστε προσωρινή ή πλήρη άδεια από το portal του GroupDocs.

## Πώς να Διαχωρίσετε Αρχείο Κειμένου ανά Γραμμές (Υλοποίηση Java)

Παρακάτω υπάρχει ένας σύντομος, βήμα‑βήμα οδηγός. Κάθε βήμα εξηγείται με απλή γλώσσα πριν από το placeholder που υποδεικνύει πού βρίσκεται ο πραγματικός κώδικας, ώστε να γνωρίζετε ακριβώς τι συμβαίνει.

### Βήμα 1: Ορισμός Πηγής και Διαδρομών Εξόδου
Πρώτα, ενημερώστε τη βιβλιοθήκη πού βρίσκεται το αρχικό σας αρχείο και πού πρέπει να γραφτούν τα τμήματα του διαχωρισμού.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Βήμα 2: Διαμόρφωση Επιλογών Διαχωρισμού
Δημιουργήστε ένα αντικείμενο `TextSplitOptions` που περιγράφει τα διαστήματα γραμμών που θέλετε. Ο πίνακας `new int[] { 3, 6 }` λέει στο API να κόψει μετά τη γραμμή 3 και τη γραμμή 6, παράγοντας δύο μέρη: γραμμές 1‑3 και γραμμές 4‑6.  
**Ορισμός:** `TextSplitOptions` είναι ένα αντικείμενο διαμόρφωσης που κρατά τον πίνακα διαστημάτων γραμμών και προαιρετικούς κανόνες ονομασίας εξόδου.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Βήμα 3: Αρχικοποίηση του Merger και Εκτέλεση του Διαχωρισμού
Τέλος, δημιουργήστε ένα αντικείμενο `Merger` με το αρχείο προέλευσης και καλέστε τη μέθοδο `split()` με τις επιλογές που μόλις δημιουργήσατε.  
**Ορισμός:** `Merger` είναι η κεντρική κλάση στο GroupDocs.Merger που συντονίζει τις λειτουργίες διαχείρισης εγγράφων όπως διαχωρισμός, συγχώνευση και εξαγωγή σελίδων.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Όταν ολοκληρωθεί η κλήση `split()`, θα βρείτε δύο νέα αρχεία στο `YOUR_OUTPUT_DIRECTORY`, το καθένα περιέχει τις καθορισμένες περιοχές γραμμών.

## Πρακτικές Εφαρμογές (Γιατί Έχει Σημασία)
1. **Διαδρόμους Επεξεργασίας Δεδομένων** – Διαχωρίστε τεράστια αρχεία καταγραφής σε μικρότερα κομμάτια για παράλληλη ανάλυση, μειώνοντας δραματικά το συνολικό χρόνο επεξεργασίας.  
2. **Διαχείριση Εγγράφων** – Μετατρέψτε μια ενιαία αναφορά σε αρχεία επιπέδου κεφαλαίων, διευκολύνοντας τη διανομή σε διαφορετικές ομάδες.  
3. **Κατάτμηση Περιεχομένου** – Προετοιμάστε τμήματα ενός μεγάλου άρθρου για στοχευμένες πλατφόρμες δημοσίευσης, βελτιώνοντας το SEO και την αναγνωσιμότητα.

## Συμβουλές Απόδοσης
- **Βελτιστοποίηση I/O** – Προτιμήστε το `Files.newBufferedReader` όταν εργάζεστε με πολύ μεγάλα αρχεία για να διατηρήσετε τη χρήση μνήμης χαμηλή.  
- **Κλείσιμο Πόρων** – Παρόλο που το GroupDocs.Merger διαχειρίζεται την περισσότερη εκκαθάριση, το ρητό κλείσιμο τυχόν προσαρμοσμένων ροών αποτρέπει διαρροές.  
- **Παρακολούθηση Μνήμης** – Ο διαχωρισμός αρχείων μεγέθους gigabyte μπορεί να είναι απαιτητικός σε μνήμη· διαθέστε επαρκή heap (`-Xmx2g` ή μεγαλύτερο) εάν χρειάζεται.  
- **Επεξεργασία σε Παρτίδες** – Όταν διαχωρίζετε πολλά αρχεία, επαναχρησιμοποιήστε ένα ενιαίο αντικείμενο `Merger` για να μειώσετε το κόστος δημιουργίας αντικειμένων.

## Κοινά Προβλήματα και Λύσεις
| Πρόβλημα | Γιατί Συμβαίνει | Διόρθωση |
|----------|----------------|----------|
| `OutOfMemoryError` | Το μεγάλο αρχείο προέλευσης υπερβαίνει το διαθέσιμο heap. | Αυξήστε το heap της JVM ή διαχωρίστε χρησιμοποιώντας μικρότερα διαστήματα. |
| `FileNotFoundException` | Λανθασμένη διαδρομή ή έλλειψη δικαιωμάτων. | Επαληθεύστε ότι τα `filePath` και `filePathOut` είναι απόλυτα και εγγράψιμα. |
| Empty output files | Ο πίνακας διαστημάτων δεν καλύπτει ολόκληρο το έγγραφο. | Βεβαιωθείτε ότι το τελευταίο διάστημα λήγει στο ή πέρα από το συνολικό αριθμό γραμμών. |

## Συχνές Ερωτήσεις

**Q: Μπορώ να διαχωρίσω αρχεία βάσει αριθμού χαρακτήρων αντί για αριθμό γραμμών;**  
**A:** Αυτή τη στιγμή, το GroupDocs.Merger για Java εστιάζει σε διαστήματα γραμμών. Ωστόσο, μπορείτε να προεπεξεργαστείτε το κείμενό σας ώστε να ταιριάζει με τον επιθυμητό αριθμό χαρακτήρων ανά γραμμή πριν χρησιμοποιήσετε αυτή τη λειτουργία.

**Q: Υπάρχει όριο στον αριθμό των διαστημάτων που μπορώ να ορίσω για διαχωρισμό;**  
**A:** Δεν υπάρχει σκληρό όριο στη βιβλιοθήκη· η απόδοση μπορεί να υποχωρήσει αν ζητήσετε χιλιάδες μικρά διαχωρισμένα κομμάτια, επειδή κάθε διαχωρισμός επιφέρει επιπλέον κόστος I/O.

**Q: Πώς να διαχειριστώ σφάλματα κατά τον διαχωρισμό αρχείων;**  
**A:** Τυλίξτε τη λογική διαχωρισμού σε ένα μπλοκ try‑catch και καταγράψτε τις λεπτομέρειες του `MergerException`. Το API παρέχει σαφή μηνύματα που εντοπίζουν το σημείο αποτυχίας.

**Q: Υποστηρίζει η βιβλιοθήκη άλλες μορφές κειμένου όπως CSV ή TSV;**  
**A:** Ναι, επειδή τα CSV και TSV είναι αρχεία απλού κειμένου, η ίδια λογική διαστήματος γραμμών εφαρμόζεται. Θεωρήστε τα ως αρχεία `.txt` όταν καλείτε το API.

**Q: Μπορώ να αυτοματοποιήσω το διαχωρισμό για πολλαπλά αρχεία σε έναν φάκελο;**  
**A:** Απόλυτα. Επανάληψη μέσω `Files.list(Paths.get("folder"))`, εφαρμόστε τις ίδιες `TextSplitOptions` σε κάθε αρχείο και συλλέξτε τα παραγόμενα τμήματα.

## Πρόσθετοι Πόροι
- [Κυκλοφορίες GroupDocs.Merger για Java](https://releases.groupdocs.com/merger/java/)
- [Τεκμηρίωση GroupDocs.Merger για Java](https://docs.groupdocs.com/merger/java/)
- [Αναφορά API GroupDocs](https://reference.groupdocs.com/merger/java/)
- [Τελευταίες Κυκλοφορίες](https://releases.groupdocs.com/merger/java/)
- [Αγορά GroupDocs](https://purchase.groupdocs.com/buy)
- [Δωρεάν Δοκιμή GroupDocs](https://releases.groupdocs.com/merger/java/)
- [Απόκτηση Προσωρινής Άδειας](https://purchase.groupdocs.com/temporary-license/)
- [Υποστήριξη GroupDocs](https://forum.groupdocs.com/c/merger)

**Τελευταία Ενημέρωση:** 2026-07-25  
**Δοκιμάστηκε Με:** GroupDocs.Merger 23.12 για Java  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να Διαχωρίσετε ένα Αρχείο Κειμένου σε Ξεχωριστά Έγγραφα Γραμμών Χρησιμοποιώντας το GroupDocs.Merger για Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [Διαχωρισμός PDF Java: Διαχωρισμός Εγγράφων με το GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Φόρτωση Τοπικού Εγγράφου Java Χρησιμοποιώντας το GroupDocs.Merger – Οδηγός](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)