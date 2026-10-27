---
date: 2026-10-27
description: Μάθετε πώς να μετατρέψετε PDF σε PNG σε Java χρησιμοποιώντας το GroupDocs.Merger,
  να δημιουργήσετε PDF previews, να διαχειριστείτε password‑protected αρχεία και να
  εμφανίσετε τη λίστα των υποστηριζόμενων μορφών.
keywords:
- convert pdf to png java
- merge images java
- generate pdf previews java
- create pdf thumbnails java
- preview password protected pdf
lastmod: 2026-10-27
og_description: Μετατρέψτε PDF σε PNG σε Java με το GroupDocs.Merger. Μάθετε γρήγορη
  δημιουργία preview, διαχείριση password‑protected και λίστα υποστηριζόμενων μορφών.
og_image_alt: Developer guide showing PDF to PNG conversion using GroupDocs.Merger
  for Java
og_title: Μετατροπή PDF σε PNG σε Java – Οδηγός GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  headline: How to convert PDF to PNG in Java with GroupDocs.Merger
  type: TechArticle
- description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  name: How to convert PDF to PNG in Java with GroupDocs.Merger
  steps:
  - name: '**Create a `Merger` instance** – this class is the entry point for all
      document operations.'
    text: '**Create a `Merger` instance** – this class is the entry point for all
      document operations.'
  - name: '**Load the PDF** using `Document` (the class that represents a single PDF
      in memory).'
    text: '**Load the PDF** using `Document` (the class that represents a single PDF
      in memory).'
  - name: '**Configure `PreviewOptions`** to set the image format to PNG and optionally
      define DPI for higher quality.'
    text: '**Configure `PreviewOptions`** to set the image format to PNG and optionally
      define DPI for higher quality.'
  - name: '**Call `preview`** – the method writes one PNG per page to the output directory.'
    text: '**Call `preview`** – the method writes one PNG per page to the output directory.'
  type: HowTo
- questions:
  - answer: Yes. The library streams pages one at a time, so memory consumption stays
      low even for very large files.
    question: Can I generate previews for large PDFs (hundreds of pages)?
  - answer: You can specify PNG, JPEG, or BMP when configuring the preview options
      in the API.
    question: How do I change the image format of the preview?
  - answer: Absolutely. Provide the password in the load options, and the preview
      generation will work as expected.
    question: Is it possible to generate previews for encrypted documents?
  - answer: No. The core GroupDocs.Merger library includes image‑merging capabilities
      out of the box.
    question: Does “merge images java” require a special module?
  - answer: Use the “retrieve supported file types” tutorial above, which calls the
      API method that returns the complete list of over 50 formats.
    question: Where can I find the full list of formats supported by “list supported
      formats java”?
  type: FAQPage
tags:
- convert PDF
- GroupDocs.Merger
- Java document processing
- PDF preview
- image conversion
- author: GroupDocs
  dateModified: '2026-10-27'
  description: Learn how to convert PDF to PNG in Java using GroupDocs.Merger, generate
    PDF previews, handle password‑protected files, and list supported formats.
  headline: How to convert PDF to PNG in Java with GroupDocs.Merger
  type: TechArticle
- questions:
  - answer: Yes. The library streams pages one at a time, so memory consumption stays
      low even for very large files.
    question: Can I generate previews for large PDFs (hundreds of pages)?
  - answer: You can specify PNG, JPEG, or BMP when configuring the preview options
      in the API.
    question: How do I change the image format of the preview?
  - answer: Absolutely. Provide the password in the load options, and the preview
      generation will work as expected.
    question: Is it possible to generate previews for encrypted documents?
  - answer: No. The core GroupDocs.Merger library includes image‑merging capabilities
      out of the box.
    question: Does “merge images java” require a special module?
  - answer: Use the “retrieve supported file types” tutorial above, which calls the
      API method that returns the complete list of over 50 formats.
    question: Where can I find the full list of formats supported by “list supported
      formats java”?
  type: FAQPage
title: Πώς να μετατρέψετε PDF σε PNG σε Java με το GroupDocs.Merger
type: docs
url: /el/java/document-information/
weight: 3
---

# Πώς να μετατρέψετε PDF σε PNG σε Java με το GroupDocs.Merger

Σε αυτόν τον ολοκληρωμένο οδηγό θα μάθετε **πώς να μετατρέψετε PDF σε PNG σε Java** χρησιμοποιώντας το GroupDocs.Merger. Είτε χρειάζεστε μικρογραφίες για μια πύλη διαχείρισης εγγράφων, γρήγορους οπτικούς ελέγχους πριν από τη συγχώνευση αρχείων, είτε επεξεργασία μεγάλων αρχείων σε παρτίδες, τα παρακάτω βήματα σας καθοδηγούν από τη βασική ρύθμιση μέχρι τη διαχείριση PDF με κωδικό πρόσβασης. Το tutorial επίσης παραπέμπει σε σχετικές λειτουργίες όπως η συγχώνευση εικόνων PNG, η λίστα των υποστηριζόμενων μορφών και η ανάκτηση μεταδεδομένων εγγράφου.

## Γρήγορες απαντήσεις
- **Τι σημαίνει “δημιουργία προεπισκοπήσεων”;** Δημιουργεί εικόνες (π.χ., PNG, JPEG) για κάθε σελίδα ενός πηγαίου εγγράφου.  
- **Ποιες μορφές υποστηρίζονται;** Όλες οι μορφές που εμφανίζονται στο “list supported formats Java” για το GroupDocs.Merger, συμπεριλαμβανομένων των PDF, DOCX, PPTX και αρχείων εικόνας.  
- **Χρειάζομαι άδεια;** Μια προσωρινή άδεια λειτουργεί για αξιολόγηση· απαιτείται πλήρης άδεια για παραγωγή.  
- **Μπορώ να δημιουργήσω προεπισκοπήσεις για αρχεία με κωδικό πρόσβασης;** Ναι – απλώς δώστε τον κωδικό πρόσβασης κατά το άνοιγμα του εγγράφου.  
- **Είναι η δημιουργία προεπισκοπήσεων γρήγορη;** Ναι, η βιβλιοθήκη μεταδίδει τις σελίδες, έτσι ακόμη και μεγάλα αρχεία επεξεργάζονται αποδοτικά.

## Τι είναι η μετατροπή PDF σε PNG σε Java;
`convert PDF to PNG in Java` σημαίνει τη μετατροπή κάθε σελίδας ενός εγγράφου PDF σε μια ραστερ εικόνα PNG που μπορεί να εμφανιστεί σε προγράμματα περιήγησης, κινητές εφαρμογές ή εξερευνητές αρχείων. Αυτή η μετατροπή παρέχει στους χρήστες μια οπτική εικόνα πριν αποφασίσουν να συγχωνεύσουν, επεξεργαστούν ή κατεβάσουν το αρχείο.

## Γιατί να δημιουργείτε προεπισκοπήσεις PDF με το GroupDocs.Merger για Java;
Το GroupDocs.Merger υποστηρίζει **πάνω από 50 μορφές εισόδου και εξόδου** και μπορεί να δημιουργήσει προεπισκοπήσεις για έγγραφα έως **500 σελίδες** διατηρώντας τη χρήση μνήμης κάτω από **50 MB**. Η βιβλιοθήκη επεξεργάζεται τις σελίδες κατά απαίτηση, παρέχοντας δημιουργία προεπισκοπήσεων σε λιγότερο από **2 δευτερόλεπτα ανά σελίδα** σε τυπική CPU 2 GHz. Η χρήση του GroupDocs.Merger εξαλείφει τις εξωτερικές μετατροπείς εικόνας και εγγυάται συνεπή απόδοση σε περιβάλλοντα Windows, Linux και macOS.

## Προαπαιτούμενα
- Εγκατεστημένο Java 8 ή νεότερο.  
- Βιβλιοθήκη GroupDocs.Merger for Java προστεθειμένη στο έργο σας (Maven/Gradle).  
- Ένα έγκυρο προσωρινό ή πλήρες κλειδί άδειας GroupDocs.  

## Πώς να μετατρέψετε PDF σε PNG σε Java;

Φορτώστε το πηγαίο PDF, διαμορφώστε το `PreviewOptions` για έξοδο PNG και καλέστε το API προεπισκοπήσεων. Η βιβλιοθήκη μεταδίδει κάθε σελίδα, γράφει ένα αρχείο PNG στον προορισμό και απελευθερώνει τη μνήμη αμέσως μετά την επεξεργασία κάθε σελίδας.

### Μετατροπή βήμα‑βήμα

1. **Δημιουργήστε ένα αντικείμενο `Merger`** – αυτή η κλάση είναι το σημείο εισόδου για όλες τις λειτουργίες εγγράφων.  
2. **Φορτώστε το PDF** χρησιμοποιώντας το `Document` (η κλάση που αντιπροσωπεύει ένα μόνο PDF στη μνήμη).  
3. **Διαμορφώστε το `PreviewOptions`** ώστε να ορίσετε τη μορφή εικόνας σε PNG και προαιρετικά να ορίσετε DPI για υψηλότερη ποιότητα.  
4. **Καλέστε το `preview`** – η μέθοδος γράφει ένα PNG ανά σελίδα στον φάκελο εξόδου.  

> **Άμεση απάντηση:** Για να μετατρέψετε ένα PDF σε PNG σε Java με το GroupDocs.Merger, δημιουργήστε ένα αντικείμενο `Merger`, φορτώστε το PDF μέσω `Document`, ορίστε το `PreviewOptions` σε PNG και καλέστε το `preview`. Η βιβλιοθήκη μεταδίδει κάθε σελίδα, δημιουργώντας ξεχωριστό αρχείο PNG για κάθε σελίδα χωρίς να φορτώνει ολόκληρο το έγγραφο στη μνήμη.

### Σημεία αναφοράς

`Merger` είναι η κύρια κλάση στο GroupDocs.Merger για φόρτωση, συγχώνευση και προεπισκόπηση εγγράφων.  
`Document` αντιπροσωπεύει ένα φορτωμένο αρχείο και παρέχει πρόσβαση στις σελίδες, τα μεταδεδομένα και τη διαχείριση ροής.  
`PreviewOptions` διαμορφώνει τον τρόπο δημιουργίας των εικόνων προεπισκόπησης, συμπεριλαμβανομένης της μορφής, DPI και εύρους σελίδων.

## Πώς να προεπισκοπήσετε PDF με κωδικό πρόσβασης σε Java;

`LoadOptions` είναι μια κλάση διαμόρφωσης που σας επιτρέπει να καθορίσετε παραμέτρους φόρτωσης εγγράφου όπως κωδικός πρόσβασης, λειτουργία μόνο για ανάγνωση και προσαρμοσμένη διαχείριση ροής. Παρέχετε τον κωδικό πρόσβασης στο `LoadOptions` κατά τη δημιουργία του `Document`. Η μηχανή προεπισκόπησης θα αποκρυπτογραφήσει το αρχείο κατά την εκτέλεση και θα παραγάγει εικόνες PNG ακριβώς όπως θα έκανε για ένα μη προστατευμένο PDF. Αυτή η προσέγγιση λειτουργεί για οποιοδήποτε κρυπτογραφημένο PDF υποστηρίζεται από το GroupDocs.Merger και δεν απαιτεί πρόσθετο κώδικα.

## Πώς να συγχωνεύσετε εικόνες java;

Το GroupDocs.Merger περιλαμβάνει ενσωματωμένες δυνατότητες συγχώνευσης εικόνων, ώστε να μπορείτε να συνδυάσετε πολλαπλά αρχεία PNG σε ένα ενιαίο έγγραφο χωρίς εξωτερικές εξαρτήσεις. Χρησιμοποιήστε τη μέθοδο `merge` σε ένα αντικείμενο `Merger`, προσθέστε κάθε PNG ως ξεχωριστό `Document` και ορίστε τη ζητούμενη μορφή εξόδου όπως PDF ή συνδυασμένη εικόνα. Αυτή η διαδικασία διατηρεί την ποιότητα της εικόνας και απαιτεί μόνο λίγες γραμμές κώδικα.

## Δημιουργία προεπισκοπήσεων pdf java – κοινά πρότυπα

- **Προεπισκόπηση μίας σελίδας:** Ορίστε `PreviewOptions.setPageNumber(1)` για να δημιουργήσετε μόνο το PNG της πρώτης σελίδας.  
- **Προεπισκόπηση παρτίδας:** Επανάληψη σε έναν φάκελο PDF, εφαρμόζοντας την ίδια λογική προεπισκόπησης σε κάθε αρχείο.  
- **Υψηλής ανάλυσης μικρογραφίες:** Αυξήστε το DPI στο `PreviewOptions` σε 300 για καθαρές μικρογραφίες κατάλληλες για εκτύπωση.

## Συνηθισμένα προβλήματα και λύσεις

| Πρόβλημα | Αιτία | Λύση |
|----------|-------|------|
| Σφάλματα έλλειψης μνήμης σε μεγάλα PDF | Φόρτωση ολόκληρου εγγράφου ταυτόχρονα | Βεβαιωθείτε ότι χρησιμοποιείτε το API προεπισκόπησης με ροή (προεπιλογή) και αποφύγετε την κλήση `Document.getPages().size()` χωρίς ανάγκη. |
| Κενές εικόνες για κρυπτογραφημένα PDF | Έλλειψη κωδικού πρόσβασης στο `LoadOptions` | Πάντα παρέχετε τον σωστό κωδικό πρόσβασης κατά τη δημιουργία του `Document`. |
| Μικρογραφίες χαμηλής ποιότητας | Προεπιλεγμένο DPI (72) είναι πολύ χαμηλό για το UI σας | Ορίστε `PreviewOptions.setDpi(150)` ή υψηλότερο πριν καλέσετε το `preview`. |

## Συχνές ερωτήσεις

**Ε: Μπορώ να δημιουργήσω προεπισκοπήσεις για μεγάλα PDF (εκατοντάδες σελίδες);**  
Α: Ναι. Η βιβλιοθήκη μεταδίδει τις σελίδες μία τη φορά, έτσι η κατανάλωση μνήμης παραμένει χαμηλή ακόμη και για πολύ μεγάλα αρχεία.

**Ε: Πώς αλλάζω τη μορφή εικόνας της προεπισκόπησης;**  
Α: Μπορείτε να ορίσετε PNG, JPEG ή BMP όταν διαμορφώνετε τις επιλογές προεπισκόπησης στην API.

**Ε: Είναι δυνατόν να δημιουργήσετε προεπισκοπήσεις για κρυπτογραφημένα έγγραφα;**  
Α: Απόλυτα. Παρέχετε τον κωδικό πρόσβασης στις επιλογές φόρτωσης και η δημιουργία προεπισκοπήσεων θα λειτουργήσει όπως αναμένεται.

**Ε: Απαιτείται ειδικό μοντέλο για το “merge images java”;**  
Α: Όχι. Η βασική βιβλιοθήκη GroupDocs.Merger περιλαμβάνει δυνατότητες συγχώνευσης εικόνων έτοιμες για χρήση.

**Ε: Πού μπορώ να βρω την πλήρη λίστα μορφών που υποστηρίζονται από το “list supported formats java”;**  
Α: Χρησιμοποιήστε το tutorial “retrieve supported file types” παραπάνω, το οποίο καλεί τη μέθοδο API που επιστρέφει την πλήρη λίστα των πάνω από 50 μορφών.

## Διαθέσιμα tutorials

### [Πώς να δημιουργήσετε προεπισκοπήσεις σελίδων εγγράφου χρησιμοποιώντας το GroupDocs.Merger για Java](./generate-document-page-previews-groupdocs-merger-java/)
Μάθετε πώς να δημιουργείτε προεπισκοπήσεις σελίδων εγγράφου με το GroupDocs.Merger για Java. Βελτιώστε τις εφαρμογές σας δημιουργώντας αποδοτικά οπτικές αναπαραστάσεις εγγράφων.

### [Πώς να συγχωνεύσετε εικόνες PNG χρησιμοποιώντας το GroupDocs.Merger για Java: Οδηγός βήμα‑βήμα](./merge-png-images-groupdocs-merger-java/)
Μάθετε πώς να συγχωνεύσετε εικόνες PNG άψογα χρησιμοποιώντας το GroupDocs.Merger για Java. Αυτός ο οδηγός καλύπτει τη ρύθμιση, την υλοποίηση και πρακτικές εφαρμογές με σαφή παραδείγματα.

### [Πώς να ανακτήσετε τους υποστηριζόμενους τύπους αρχείων χρησιμοποιώντας το GroupDocs.Merger για Java](./retrieve-supported-file-types-groupdocs-merger-java/)
Μάθετε πώς να χρησιμοποιήσετε το GroupDocs.Merger για Java για την ανάκτηση των υποστηριζόμενων τύπων αρχείων. Αυτός ο οδηγός παρέχει βήμα‑βήμα οδηγίες και βέλτιστες πρακτικές.

### [Ανάκτηση πληροφοριών εγγράφου με το GroupDocs.Merger για Java: Οδηγός βήμα‑βήμα](./groupdocs-merger-java-retrieve-document-info-guide/)
Μάθετε πώς να χρησιμοποιήσετε το GroupDocs.Merger για Java για την αποτελεσματική ανάκτηση μεταδεδομένων εγγράφου, συμπεριλαμβανομένου του αριθμού σελίδων και των λεπτομερειών συγγραφέα. Βελτιώστε τις Java εφαρμογές σας σήμερα!

## Πρόσθετοι πόροι

- [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)
- [GroupDocs.Merger for Java API Reference](https://reference.groupdocs.com/merger/java/)
- [Download GroupDocs.Merger for Java](https://releases.groupdocs.com/merger/java/)
- [GroupDocs.Merger Forum](https://forum.groupdocs.com/c/merger)
- [Free Support](https://forum.groupdocs.com/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)

## Σχετικά tutorials

- [Πώς να φορτώσετε PDF από URL χρησιμοποιώντας το GroupDocs.Merger για Java: Οδηγός ολοκληρωμένος](/merger/java/document-loading/load-pdf-url-groupdocs-merger-java/)
- [Batch Process Documents - Φόρτωση αρχείων με κωδικό πρόσβασης με το GroupDocs.Merger για Java](/merger/java/document-loading/load-password-protected-docs-groupdocs-java/)
- [Πώς να ανακτήσετε τους υποστηριζόμενους τύπους αρχείων χρησιμοποιώντας το GroupDocs.Merger για Java](/merger/java/document-information/retrieve-supported-file-types-groupdocs-merger-java/)

---

**Τελευταία ενημέρωση:** 2026-10-27  
**Δοκιμάστηκε με:** GroupDocs.Merger 23.12 for Java  
**Συγγραφέας:** GroupDocs