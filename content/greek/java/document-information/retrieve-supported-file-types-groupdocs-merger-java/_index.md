---
date: '2026-07-06'
description: Μάθετε πώς να ανακτήσετε τους υποστηριζόμενους τύπους αρχείων με το GroupDocs.Merger
  για Java, ελέγξτε τις υποστηριζόμενες επεκτάσεις java και ενσωματώστε τη λίστα στη
  ροή εργασίας σας.
keywords:
- groupdocs merger supported formats
- check supported extensions java
- how to get supported file types java
schemas:
- author: GroupDocs
  dateModified: '2026-07-06'
  description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  headline: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  type: TechArticle
- description: Learn how to retrieve supported file types with GroupDocs.Merger for
    Java, check supported extensions java, and integrate the list into your workflow.
  name: GroupDocs.Merger Supported Formats – Retrieve Types in Java
  steps:
  - name: Obtain Supported File Types
    text: 'First, retrieve the list of supported file types from the `FileType` class:
      This method returns a list containing all the file types that GroupDocs.Merger
      supports.'
  - name: Display Supported Extensions
    text: 'Next, iterate through each `FileType` object and print its extension. This
      is the part where we **display supported extensions** for developers or end‑users:
      The loop goes through each supported file type and outputs its extension to
      the console.'
  - name: Confirmation Message
    text: 'Finally, output a confirmation message indicating successful retrieval:'
  type: HowTo
- questions:
  - answer: It’s a Java library that enables merging, splitting, and converting a
      wide range of document formats without requiring Microsoft Office.
    question: What is GroupDocs.Merger for Java?
  - answer: Add the Maven or Gradle dependency, obtain a trial or full license, and
      initialize the library as shown in the setup section.
    question: How do I get started with GroupDocs.Merger?
  - answer: Yes, a free trial is available for evaluation; a full license is required
      for production deployments.
    question: Can I use GroupDocs.Merger for free?
  - answer: Use the `FileType.getSupportedFileTypes()` method to retrieve a list of
      **70+** supported formats, including PDF, DOCX, PPTX, XLSX, HTML, and image
      types.
    question: What file types does GroupDocs.Merger support?
  - answer: Validate uploads against the supported list before processing; reject
      or convert unsupported files early to avoid runtime errors.
    question: How do I handle unsupported file types?
  type: FAQPage
title: GroupDocs.Merger Υποστηριζόμενες μορφές – Ανάκτηση τύπων σε Java
type: docs
url: /el/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger Υποστηριζόμενες Μορφές – Ανάκτηση Τύπων σε Java

Η εργασία με μια ευρεία ποικιλία μορφών εγγράφων σε Java μπορεί γρήγορα να γίνει πηγή άγχους εάν δεν γνωρίζετε ποιες μορφές υποστηρίζει πραγματικά η βιβλιοθήκη σας. **GroupDocs.Merger supported formats** σας παρέχει ένα αξιόπιστο σημείο αναφοράς, επιτρέποντάς σας να επικυρώνετε τα ανεβάσματα, να αποφεύγετε σφάλματα χρόνου εκτέλεσης και να σχεδιάζετε πιο έξυπνες ροές διαχείρισης εγγράφων. Σε αυτό το tutorial θα δείτε ακριβώς πώς να ανακτήσετε τη λίστα των υποστηριζόμενων τύπων αρχείων χρησιμοποιώντας το GroupDocs.Merger για Java, γιατί είναι σημαντικό και πώς να ενσωματώσετε τις πληροφορίες σε πραγματικές εφαρμογές.

### Γρήγορες Απαντήσεις
- **Τι κάνει η “retrieve supported file types”;**  
  Επιστρέφει μια λίστα με κάθε μορφή εγγράφου που μπορεί να επεξεργαστεί το GroupDocs.Merger.
- **Ποια μέθοδος παρέχει τη λίστα;**  
  `FileType.getSupportedFileTypes()` from the `com.groupdocs.merger.domain` package.
- **Χρειάζομαι άδεια για να καλέσω αυτή τη μέθοδο;**  
  Απαιτείται δοκιμαστική ή πλήρης άδεια για χρήση σε παραγωγή· η μέθοδος λειτουργεί σε λειτουργία αξιολόγησης.
- **Μπορώ να φιλτράρω τη λίστα ώστε να περιλαμβάνει μόνο τις επεκτάσεις που χρειάζομαι;**  
  Ναι – επαναλάβετε τη λίστα που επιστρέφεται και κρατήστε τις επεκτάσεις που σας ενδιαφέρουν.
- **Είναι αυτή η λειτουργία βαριά από άποψη απόδοσης;**  
  Όχι, απλώς διαβάζει μια στατική συλλογή, επομένως εκτελείται άμεσα.

## Ποιες είναι οι υποστηριζόμενες μορφές του GroupDocs.Merger;

Το GroupDocs.Merger υποστηρίζει **70+** μορφές εισόδου και εξόδου — συμπεριλαμβανομένων PDF, DOCX, PPTX, XLSX, HTML και κοινών τύπων εικόνων — επιτρέποντάς σας να εργάζεστε με σχεδόν οποιοδήποτε επιχειρηματικό έγγραφο. Ο πίνακας μορφών της βιβλιοθήκης αποθηκεύεται εσωτερικά ως στατική συλλογή, έτσι η ανάκτησή του είναι μια λειτουργία O(1) που ολοκληρώνεται σε λίγα χιλιοστά του δευτερολέπτου, ακόμη και σε μέτριο υλικό.

## Πώς μπορώ να ελέγξω τις υποστηριζόμενες επεκτάσεις σε Java;

Καλέστε τη στατική μέθοδο `FileType.getSupportedFileTypes()`, στη συνέχεια επαναλάβετε τη συλλογή που επιστρέφεται για να διαβάσετε κάθε επέκταση. Αυτή η κλήση μιας γραμμής σας παρέχει ένα έτοιμο προς χρήση `List<FileType>` που μπορείτε να φιλτράρετε, να εμφανίσετε ή να αποθηκεύσετε για μελλοντική επικύρωση.

## Γιατί πρέπει να ανακτήσω τις υποστηριζόμενες μορφές αρχείων πριν την επεξεργασία;

Η γνώση της ακριβούς λίστας μορφών αποτρέπει αποφεύξιμες εξαιρέσεις, μειώνει την ανάγκη για αμυντικό κώδικα και σας επιτρέπει να παρουσιάζετε στους χρήστες ένα σαφές μήνυμα “επιτρεπόμενων τύπων αρχείων”. Επίσης, σας δίνει τη δυνατότητα να δημιουργήσετε δυναμικά UI στοιχεία — όπως φίλτρα επιλογέα αρχείων — που εμφανίζουν μόνο συμβατές επεκτάσεις, βελτιώνοντας τη συνολική εμπειρία χρήστη.

## Προαπαιτούμενα

- **Java Development Kit (JDK):** Συνιστάται έκδοση 8 ή νεότερη.  
- **Integrated Development Environment (IDE):** Οποιοδήποτε IDE όπως IntelliJ IDEA ή Eclipse θα λειτουργήσει.  
- **GroupDocs.Merger Library:** Συμπεριλάβετε αυτή τη βιβλιοθήκη στις εξαρτήσεις του έργου σας.  

Η εξοικείωση με βασικές έννοιες προγραμματισμού Java και η εμπειρία εργασίας με βιβλιοθήκες σε περιβάλλον Maven ή Gradle είναι επίσης ωφέλιμες. Εάν είστε νέοι σε αυτά τα εργαλεία, σκεφτείτε να εξετάσετε πρώτα την τεκμηρίωσή τους.

## Ρύθμιση του GroupDocs.Merger για Java

Για να χρησιμοποιήσετε το GroupDocs.Merger για Java, ρυθμίστε τη βιβλιοθήκη στο έργο σας χρησιμοποιώντας Maven, Gradle ή κατεβάζοντας απευθείας από τον επίσημο ιστότοπο.

### Εγκατάσταση μέσω Maven

Προσθέστε την ακόλουθη εξάρτηση στο αρχείο `pom.xml` σας:

```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Εγκατάσταση μέσω Gradle

Συμπεριλάβετε αυτή τη γραμμή στο αρχείο `build.gradle` σας:

```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### Άμεση Λήψη

Εναλλακτικά, κατεβάστε την πιο πρόσφατη έκδοση από [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

#### Βήματα Απόκτησης Άδειας
1. **Free Trial:** Ξεκινήστε με μια δωρεάν δοκιμή για να εξερευνήσετε τις δυνατότητες της βιβλιοθήκης.  
2. **Temporary License:** Αποκτήστε προσωρινή άδεια εάν χρειάζεστε εκτεταμένη πρόσβαση χωρίς περιορισμούς.  
3. **Purchase:** Σκεφτείτε την αγορά πλήρους άδειας για μακροπρόθεσμη χρήση.

## Βασική Αρχικοποίηση και Ρύθμιση

Για να αρχικοποιήσετε το GroupDocs.Merger στην εφαρμογή Java, εισάγετε τις απαραίτητες κλάσεις:

```java
import com.groupdocs.merger.domain.FileType;
```

Τώρα, ας προχωρήσουμε στην υλοποίηση της λειτουργίας που ανακτά τις υποστηριζόμενες μορφές αρχείων.

## Τι είναι η κλάση FileType;

Η κλάση `FileType` είναι το βασικό μοντέλο στο GroupDocs.Merger που αντιπροσωπεύει μια μοναδική μορφή εγγράφου, εκθέτοντας την επέκτασή της, τον τύπο MIME και ένα φιλικό όνομα εμφάνισης. Αλληλεπιδράτε με αυτήν την κλάση όταν καλείτε `FileType.getSupportedFileTypes()` για να λάβετε τον πλήρη κατάλογο μορφών.

## Πώς να ανακτήσετε τις υποστηριζόμενες μορφές αρχείων;

Για να ανακτήσετε τις υποστηριζόμενες μορφές, απλώς καλέστε τη στατική μέθοδο `FileType.getSupportedFileTypes()` που παρέχεται από τη βιβλιοθήκη GroupDocs.Merger. Αυτή η κλήση επιστρέφει ένα `List<FileType>` που περιέχει κάθε μορφή που μπορεί να χειριστεί η βιβλιοθήκη. Η λειτουργία είναι ελαφριά και μπορεί να εκτελεστεί κατά την εκκίνηση της εφαρμογής ή όποτε χρειάζεστε την επικύρωση ανεβασμένων αρχείων.

### Βήμα 1: Απόκτηση Υποστηριζόμενων Μορφών Αρχείων

Αρχικά, ανακτήστε τη λίστα των υποστηριζόμενων μορφών αρχείων από την κλάση `FileType`:

```java
List<FileType> fileTypes = FileType.getSupportedFileTypes();
```

Αυτή η μέθοδος επιστρέφει μια λίστα που περιέχει όλους τους τύπους αρχείων που υποστηρίζει το GroupDocs.Merger.

### Βήμα 2: Εμφάνιση Υποστηριζόμενων Επεκτάσεων

Στη συνέχεια, επαναλάβετε κάθε αντικείμενο `FileType` και εκτυπώστε την επέκτασή του. Αυτό είναι το τμήμα όπου **εμφανίζουμε τις υποστηριζόμενες επεκτάσεις** για προγραμματιστές ή τελικούς χρήστες:

```java
for (FileType fileType : fileTypes) {
    System.out.println(fileType.getExtension());
}
```

Ο βρόχος διασχίζει κάθε υποστηριζόμενη μορφή αρχείου και εκτυπώνει την επέκτασή της στην κονσόλα.

### Βήμα 3: Μήνυμα Επιβεβαίωσης

Τέλος, εκτυπώστε ένα μήνυμα επιβεβαίωσης που υποδεικνύει επιτυχή ανάκτηση:

```java
System.out.println("Supported file types retrieved successfully.");
```

## Πρακτικές Εφαρμογές

Η κατανόηση των υποστηριζόμενων τύπων αρχείων είναι ουσιώδης για διάφορες εφαρμογές:

1. **Document Management Systems:** Αυτόματη κατηγοριοποίηση εγγράφων βάσει του τύπου τους.  
2. **File Conversion Tools:** Διασφάλιση συμβατότητας πριν τη μετατροπή αρχείων μεταξύ μορφών.  
3. **Merging Applications:** Επικύρωση αρχείων εισόδου πριν τη συγχώνευση για αποφυγή σφαλμάτων.  

Η ενσωμάτωση με άλλα συστήματα — όπως αποθήκευση στο cloud ή υπηρεσίες επεξεργασίας εγγράφων — μπορεί να ενισχύσει περαιτέρω τη λειτουργικότητα.

## Σκέψεις Απόδοσης

Κατά την εργασία με το GroupDocs.Merger σε Java, λάβετε υπόψη τις παρακάτω συμβουλές απόδοσης:

- **Optimize Memory Usage:** Αποδεσμεύστε αντικείμενα όταν δεν χρειάζονται πλέον.  
- **Batch Processing:** Επεξεργαστείτε αρχεία σε παρτίδες για μείωση της κατανάλωσης πόρων.  
- **Asynchronous Operations:** Χρησιμοποιήστε ασύγχρονες μεθόδους για μη‑αποκλειστικές λειτουργίες.  

## Συνηθισμένα Προβλήματα και Λύσεις

- **Dependency Issues:** Επαληθεύστε ότι οι εξαρτήσεις Maven ή Gradle έχουν δηλωθεί σωστά· οι ασυμφωνίες εκδόσεων προκαλούν σφάλματα class‑not‑found.  
- **Library Version:** Χρησιμοποιείτε πάντα την πιο πρόσφατη έκδοση του GroupDocs.Merger για να επωφεληθείτε από νέες μορφές και διορθώσεις σφαλμάτων.  
- **License Errors:** Εάν εμφανίζονται εξαιρέσεις άδειας, βεβαιωθείτε ότι το αρχείο δοκιμαστικής ή μόνιμης άδειας αναφέρεται σωστά στον κώδικά σας.  

## Συχνές Ερωτήσεις

**Q: Τι είναι το GroupDocs.Merger για Java;**  
A: Είναι μια βιβλιοθήκη Java που επιτρέπει τη συγχώνευση, το διαχωρισμό και τη μετατροπή μιας ευρείας γκάμας μορφών εγγράφων χωρίς την ανάγκη του Microsoft Office.

**Q: Πώς μπορώ να ξεκινήσω με το GroupDocs.Merger;**  
A: Προσθέστε την εξάρτηση Maven ή Gradle, αποκτήστε δοκιμαστική ή πλήρη άδεια και αρχικοποιήστε τη βιβλιοθήκη όπως φαίνεται στην ενότητα ρύθμισης.

**Q: Μπορώ να χρησιμοποιήσω το GroupDocs.Merger δωρεάν;**  
A: Ναι, υπάρχει δωρεάν δοκιμή για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγικές εγκαταστάσεις.

**Q: Ποιους τύπους αρχείων υποστηρίζει το GroupDocs.Merger;**  
A: Χρησιμοποιήστε τη μέθοδο `FileType.getSupportedFileTypes()` για να λάβετε μια λίστα με **70+** υποστηριζόμενες μορφές, συμπεριλαμβανομένων PDF, DOCX, PPTX, XLSX, HTML και τύπων εικόνων.

**Q: Πώς να διαχειριστώ μη υποστηριζόμενους τύπους αρχείων;**  
A: Επικυρώστε τα ανεβάσματα έναντι της λίστας υποστηριζόμενων πριν την επεξεργασία· απορρίψτε ή μετατρέψτε νωρίς τα μη υποστηριζόμενα αρχεία για να αποφύγετε σφάλματα χρόνου εκτέλεσης.

**Q: Μπορώ να φιλτράρω τη λίστα ώστε να εμφανίζει μόνο τις επεκτάσεις που χρειάζομαι;**  
A: Ναι. Μετά την κλήση του `getSupportedFileTypes()`, επαναλάβετε τη λίστα και κρατήστε μόνο τις επεκτάσεις που σας ενδιαφέρουν.

**Q: Απαιτείται άδεια για εκδόσεις ανάπτυξης;**  
A: Μια δοκιμαστική άδεια λειτουργεί για ανάπτυξη και δοκιμές· απαιτείται πλήρης άδεια για εμπορική παραγωγική χρήση.

**Q: Επηρεάζει αυτή η μέθοδος τον χρόνο εκκίνησης της εφαρμογής;**  
A: Όχι. Η λίστα υποστηριζόμενων τύπων αρχείων είναι στατική, έτσι η ανάκτηση είναι σχεδόν άμεση.

**Q: Θα αλλάξει η λίστα με νέες εκδόσεις της βιβλιοθήκης;**  
A: Νέες εκδόσεις μπορεί να προσθέσουν ή να αποσύρουν μορφές· χρησιμοποιείτε πάντα την πιο πρόσφατη έκδοση για την πιο ενημερωμένη λίστα.

## Πόροι
- [Τεκμηρίωση](https://docs.groupdocs.com/merger/java/)
- [Αναφορά API](https://reference.groupdocs.com/merger/java/)
- [Λήψη](https://releases.groupdocs.com/merger/java/)
- [Αγορά](https://purchase.groupdocs.com/buy)
- [Δωρεάν Δοκιμή](https://releases.groupdocs.com/merger/java/)
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)
- [Υποστήριξη](https://forum.groupdocs.com/c/merger/) 

Μη διστάσετε να εξερευνήσετε αυτούς τους πόρους για πιο λεπτομερείς πληροφορίες και υποστήριξη. Καλό προγραμματισμό!

---

**Τελευταία Ενημέρωση:** 2026-07-06  
**Δοκιμάστηκε Με:** GroupDocs.Merger τελευταία έκδοση (ως το 2026)  
**Συγγραφέας:** GroupDocs  

## Σχετικά Μαθήματα

- [GroupDocs.Merger for Java: Οδηγός Ρύθμισης Άδειας & Ελέγχου Υπαρξης Αρχείου](/merger/java/licensing/groupdocs-merger-java-license-setup-file-existence-checks/)
- [Φόρτωση Τοπικού Εγγράφου Java Χρησιμοποιώντας GroupDocs.Merger – Οδηγός](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)
- [Συγχώνευση Συγκεκριμένων Σελίδων Java – Μαθήματα Συγκόλλησης Εγγράφων για GroupDocs.Merger](/merger/java/document-joining/)