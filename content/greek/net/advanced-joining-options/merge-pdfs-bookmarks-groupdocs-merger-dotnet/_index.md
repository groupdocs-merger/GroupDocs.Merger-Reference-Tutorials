---
date: '2026-08-20'
description: Μάθετε πώς να συγχωνεύσετε PDF με σελιδοδείκτες χρησιμοποιώντας το GroupDocs.Merger
  for .NET, συμπεριλαμβανομένης της εγκατάστασης, παραδειγμάτων κώδικα και βέλτιστων
  πρακτικών για τη συνένωση εγγράφων PDF.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Μάθετε πώς να συγχωνεύσετε PDF με σελιδοδείκτες χρησιμοποιώντας το
  GroupDocs.Merger for .NET. Ακολουθήστε κώδικα βήμα‑βήμα για τη συνένωση εγγράφων
  PDF διατηρώντας την πλοήγηση.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Πώς να συγχωνεύσετε PDF με σελιδοδείκτες χρησιμοποιώντας το GroupDocs.Merger
  for .NET
schemas:
- author: GroupDocs
  dateModified: '2026-08-20'
  description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  headline: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to merge pdfs with bookmarks using GroupDocs.Merger for .NET,
    including setup, code examples, and best practices for combining PDF documents.
  name: How to merge pdfs with bookmarks using GroupDocs.Merger for .NET
  steps:
  - name: define directory paths
    text: Set up source and output folders so the code can locate the PDFs you want
      to merge. csharp string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY"; string
      outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
  - name: load the primary PDF
    text: '`Merger` represents the main document you’ll append others to. csharp using
      (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
      { // Code to merge additional files will be here. }'
  - name: configure bookmark‑preserving options
    text: '`PdfJoinOptions` controls how the merge behaves; the `UseBookmarks` flag
      tells the engine to keep existing bookmarks. csharp var pdfJoinOptions = new
      PdfJoinOptions { UseBookmarks = true };'
  - name: add additional PDFs
    text: Call `Join` for each extra file. The library automatically merges their
      bookmark trees under the main document’s outline. csharp merger.Join(Path.Combine(documentDirectory,
      "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
  - name: save the merged PDF
    text: Specify the output path and format; the library writes a single PDF that
      retains all bookmark entries. csharp string outputFile = Path.Combine(outputDirectory,
      "merged.pdf"); merger.Save(outputFile);
  type: HowTo
- questions:
  - answer: GroupDocs.Merger is a .NET library that lets you merge, split, rotate,
      and otherwise manipulate PDF and other document formats programmatically.
    question: What is GroupDocs.Merger?
  - answer: Yes – call `Join` repeatedly or pass a collection of file paths to merge
      any number of PDFs in one operation.
    question: Can I merge more than two PDF files at a time?
  - answer: Obtain a permanent license from the GroupDocs purchase page; the trial
      license works only for evaluation and expires after 30 days.
    question: How do I handle licensing for production use?
  - answer: Ensure `PdfJoinOptions.UseBookmarks` is set to `true` and that each source
      PDF actually contains bookmarks before merging.
    question: My merged PDF shows no bookmarks—what went wrong?
  - answer: Absolutely – it supports .NET Core 3.1+, .NET 5/6, and the full .NET Framework
      4.6.1+.
    question: Is the library compatible with .NET Core and .NET Framework?
  type: FAQPage
tags:
- merge pdf
- GroupDocs.Merger
- .NET PDF processing
title: Πώς να συγχωνεύσετε PDF με σελιδοδείκτες χρησιμοποιώντας το GroupDocs.Merger
  for .NET
type: docs
url: /el/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Πώς να συγχωνεύσετε pdfs με σελιδοδείκτες χρησιμοποιώντας το GroupDocs.Merger για .NET

Η συγχώνευση πολλαπλών αρχείων PDF ενώ διατηρούνται οι αρχικοί σελιδοδείκτες μπορεί να σας εξοικονομήσει ώρες χειροκίνητης επαναοργάνωσης. Σε αυτό το tutorial θα μάθετε πώς να **συγχωνεύετε pdfs με σελιδοδείκτες** χρησιμοποιώντας το GroupDocs.Merger για .NET, από τη ρύθμιση του έργου μέχρι ένα πλήρες, έτοιμο για παραγωγή δείγμα κώδικα.

## Γρήγορες απαντήσεις
- **Ποια βιβλιοθήκη υποστηρίζει συγχωνεύσεις που διατηρούν σελιδοδείκτες;** GroupDocs.Merger for .NET.  
- **Μπορώ να συγχωνεύσω περισσότερα από δύο PDF ταυτόχρονα;** Ναι – προσθέστε όσα αρχεία προέλευσης χρειάζεστε.  
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται μόνιμη άδεια για παραγωγή.  
- **Υποστηρίζεται το .NET Core;** Απόλυτα – η βιβλιοθήκη λειτουργεί με .NET Core, .NET 5/6 και το πλήρες .NET Framework.  
- **Ποιο είναι το μέγιστο μέγεθος αρχείου που μπορεί να διαχειριστεί;** Έως 2 GB ανά έγγραφο, επεξεργαζόμενο χωρίς να φορτώνεται ολόκληρο το αρχείο στη μνήμη.

## Τι είναι η συγχώνευση pdfs με σελιδοδείκτες;
**Τι είναι η συγχώνευση pdfs με σελιδοδείκτες;** Η **συγχώνευση pdfs με σελιδοδείκτες** σημαίνει τη λήψη πολλαπλών εγγράφων PDF και τη συνένωσή τους σε ένα ενιαίο αρχείο ενώ διατηρείται η ιεραρχία σελιδοδεικτών κάθε πηγής. Το αποτέλεσμα PDF διατηρεί την αρχική δομή πλοήγησης, επιτρέποντας στους αναγνώστες να μεταβούν απευθείας στις ενότητες που προέρχονται από κάθε μεμονωμένο αρχείο, κάτι που είναι ουσιώδες για μεγάλες εκθέσεις ή συνενωμένα εγχειρίδια.

## Γιατί να συγχωνεύετε pdfs με σελιδοδείκτες;
Η διατήρηση των σελιδοδεικτών κατά τη συγχώνευση PDF βελτιώνει την πλοήγηση σε ενοποιημένα έγγραφα, επιτρέποντας στους χρήστες να εντοπίζουν γρήγορα συγκεκριμένα κεφάλαια ή ενότητες χωρίς να κάνουν κύλιση σε όλο το αρχείο. Το GroupDocs.Merger διατηρεί την αρχική ιεραρχία περιγράμματος, μειώνει την ανάγκη χειροκίνητης επαναοργάνωσης και υποστηρίζει μεγάλα αρχεία έως 2 GB χρησιμοποιώντας ελάχιστη μνήμη, καθιστώντας το ιδανικό για επιχειρησιακές ροές εργασίας μεγάλης κλίμακας.

## Προαπαιτούμενα
- **.NET Core SDK** (3.1 ή νεότερο) ή **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** ή οποιοδήποτε IDE που υποστηρίζει ανάπτυξη .NET.  
- Βασικές γνώσεις C# και εξοικείωση με file I/O.  

## Ρύθμιση του GroupDocs.Merger για .NET

### Εγκατάσταση
Προσθέστε τη βιβλιοθήκη στο έργο σας με μία από τις παρακάτω εντολές:

**.NET CLI:**  
```  
```bash
dotnet add package GroupDocs.Merger
```  
```  

**Package Manager:**  
```  
```powershell
Install-Package GroupDocs.Merger
```  
```  

**Διεπαφή χρήστη NuGet Package Manager:**  
- Αναζητήστε “GroupDocs.Merger” και εγκαταστήστε την πιο πρόσφατη έκδοση.

### Απόκτηση άδειας
- **Δωρεάν δοκιμή:** Κατεβάστε από τη σελίδα [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) .
- **Προσωρινή άδεια:** Λάβετε μία μέσω της [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/) .
- **Πλήρης άδεια:** Αγοράστε στη [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy) .

### Βασική αρχικοποίηση
Η κλάση `Merger` είναι το σημείο εισόδου για όλες τις λειτουργίες συγχώνευσης.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Αυτό το namespace σας δίνει πρόσβαση στο πλήρες σύνολο λειτουργιών χειρισμού PDF.

## Πώς να συγχωνεύσετε pdfs με σελιδοδείκτες σε .NET

Φορτώστε το κύριο PDF, διαμορφώστε τη διαχείριση σελιδοδεικτών, προσθέστε επιπλέον αρχεία και αποθηκεύστε το αποτέλεσμα – όλα σε λίγες σύντομες γραμμές κώδικα.

**Άμεση απάντηση (40‑70 λέξεις):** Δημιουργήστε μια παρουσία `Merger` με το πρώτο PDF, ενεργοποιήστε `PdfJoinOptions.UseBookmarks`, προσθέστε κάθε επόμενο PDF μέσω `Join`, και καλέστε `Save` για να γράψετε το συνδυασμένο αρχείο. Αυτή η προσέγγιση διατηρεί κάθε αρχική ιεραρχία σελιδοδεικτών και εκτελείται σε μία μόνο διέλευση, ελαχιστοποιώντας τη χρήση μνήμης.

### Βήμα 1: ορισμός διαδρομών φακέλων
Ρυθμίστε τους φακέλους προέλευσης και εξόδου ώστε ο κώδικας να μπορεί να εντοπίσει τα PDF που θέλετε να συγχωνεύσετε.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Βήμα 2: φόρτωση του κύριου PDF
`Merger` αντιπροσωπεύει το κύριο έγγραφο στο οποίο θα προσαρτήσετε τα άλλα.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // Code to merge additional files will be here.
   }
   ```  
```  

### Βήμα 3: διαμόρφωση επιλογών διατήρησης σελιδοδεικτών
`PdfJoinOptions` ελέγχει τη συμπεριφορά της συγχώνευσης· η σημαία `UseBookmarks` λέει στη μηχανή να διατηρήσει τους υπάρχοντες σελιδοδείκτες.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Βήμα 4: προσθήκη επιπλέον PDF
Καλέστε `Join` για κάθε επιπλέον αρχείο. Η βιβλιοθήκη συγχωνεύει αυτόματα τα δέντρα σελιδοδεικτών τους κάτω από το περίγραμμα του κύριου εγγράφου.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Βήμα 5: αποθήκευση του συγχωνευμένου PDF
Καθορίστε τη διαδρομή εξόδου και τη μορφή· η βιβλιοθήκη γράφει ένα ενιαίο PDF που διατηρεί όλες τις καταχωρήσεις σελιδοδεικτών.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Συχνά προβλήματα και λύσεις
- **Λείπουν σελιδοδείκτες:** Επαληθεύστε ότι `UseBookmarks = true` στο `PdfJoinOptions`.  
- **Σφάλματα διαδρομής:** Χρησιμοποιήστε `Path.Combine` και ελέγξτε την ύπαρξη του αρχείου πριν τη συγχώνευση.  
- **Τα μεγάλα αρχεία προκαλούν αυξήσεις μνήμης:** Επεξεργαστείτε τα PDF διαδοχικά και απελευθερώστε το αντικείμενο `Merger` μετά από κάθε αποθήκευση.

## Πρακτικές εφαρμογές
1. **Συνένωση οικονομικών εκθέσεων** – διατηρήστε τις τριμηνιαίες ενότητες άμεσα προσβάσιμες μέσω σελιδοδεικτών.  
2. **Πακέτα εκπαιδευτικού υλικού** – συγχωνεύστε PDF διαλέξεων διατηρώντας την πλοήγηση κεφαλαίων για τους φοιτητές.  
3. **Πακέτα τεκμηρίωσης έργου** – συνδυάστε προδιαγραφές σχεδίασης, σχέδια δοκιμών και σημειώσεις έκδοσης σε ένα ενιαίο, αναζητήσιμο αρχείο.

## Σκέψεις απόδοσης
- Επεξεργαστείτε ένα αρχείο τη φορά όταν συγχωνεύετε πάνω από 20 PDF για να διατηρήσετε χαμηλή χρήση RAM.  
- Χρησιμοποιήστε το πιο πρόσφατο .NET runtime (π.χ., .NET 6) για βέλτιστη JIT μεταγλώττιση και αποδοτικότητα garbage‑collection.  
- Για PDF μεγαλύτερα από 500 MB, ενεργοποιήστε τη λειτουργία streaming μέσω `MergerSettings` για να αποφύγετε τη φόρτωση ολόκληρου του εγγράφου στη μνήμη.

## Συχνές ερωτήσεις

**Ε: Τι είναι το GroupDocs.Merger;**  
Α: Το GroupDocs.Merger είναι μια βιβλιοθήκη .NET που σας επιτρέπει να συγχωνεύετε, χωρίζετε, περιστρέφετε και γενικά να χειρίζεστε προγραμματιστικά PDF και άλλες μορφές εγγράφων.

**Ε: Μπορώ να συγχωνεύσω περισσότερα από δύο αρχεία PDF ταυτόχρονα;**  
Α: Ναι – καλέστε το `Join` επανειλημμένα ή περάστε μια συλλογή διαδρομών αρχείων για να συγχωνεύσετε οποιονδήποτε αριθμό PDF σε μία λειτουργία.

**Ε: Πώς διαχειρίζομαι την άδεια για παραγωγική χρήση;**  
Α: Αποκτήστε μόνιμη άδεια από τη σελίδα αγοράς του GroupDocs· η δοκιμαστική άδεια λειτουργεί μόνο για αξιολόγηση και λήγει μετά από 30 ημέρες.

**Ε: Το συγχωνευμένο PDF μου δεν εμφανίζει σελιδοδείκτες—τι πήγε στραβά;**  
Α: Βεβαιωθείτε ότι το `PdfJoinOptions.UseBookmarks` είναι ορισμένο σε `true` και ότι κάθε PDF προέλευσης περιέχει πραγματικά σελιδοδείκτες πριν τη συγχώνευση.

**Ε: Είναι η βιβλιοθήκη συμβατή με .NET Core και .NET Framework;**  
Α: Απόλυτα – υποστηρίζει .NET Core 3.1+, .NET 5/6 και το πλήρες .NET Framework 4.6.1+.

## Πόροι
- [Τεκμηρίωση](https://docs.groupdocs.com/merger/net/)  
- [Αναφορά API](https://reference.groupdocs.com/merger/net/)  
- [Λήψη GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Αγορά Άδειας](https://purchase.groupdocs.com/buy)  
- [Δωρεάν Έκδοση Δοκιμής](https://releases.groupdocs.com/merger/net/)  
- [Προσωρινή Άδεια](https://purchase.groupdocs.com/temporary-license/)  
- [Φόρουμ Υποστήριξης](https://forum.groupdocs.com/c/merger/)  

---

**Τελευταία ενημέρωση:** 2026-08-20  
**Δοκιμάστηκε με:** GroupDocs.Merger 23.11 for .NET  
**Συγγραφέας:** GroupDocs

## Σχετικά Μαθήματα

- [Πώς να Συγχωνεύσετε Συγκεκριμένες Σελίδες PDF με το GroupDocs.Merger για .NET: Ένας Πλήρης Οδηγός](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Πώς να Ενώνετε Έγγραφα Χάρη στο GroupDocs.Merger για .NET: Ένας Πλήρης Οδηγός](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Προσθήκη Συνημμένων σε PDF Χρησιμοποιώντας το GroupDocs.Merger για .NET: Οδηγός Βήμα-Βήμα](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)