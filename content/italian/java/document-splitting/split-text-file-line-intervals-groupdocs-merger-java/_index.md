---
date: '2026-02-06'
description: Scopri come dividere un file di testo per righe usando GroupDocs.Merger
  per Java. Una guida passo passo per una divisione efficiente dei documenti nei progetti
  Java.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Come dividere un file per righe con GroupDocs.Merger per Java
type: docs
url: /it/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Come dividere un file per righe usando GroupDocs.Merger per Java

Dividere un grande file di testo in pezzi più piccoli e gestibili **per righe** è una necessità comune quando, ad esempio, si elaborano log, si importano dati in batch o si riorganizzano report lunghi. In questo tutorial imparerai esattamente come **dividere un file per righe** con GroupDocs.Merger per Java, scoprirai perché questo approccio fa risparmiare tempo e otterrai un esempio di codice pronto all'uso.

## Risposte rapide
- **Cosa significa “split file by lines”?** Crea file di testo separati che contengono ciascuno un intervallo definito di numeri di riga dal documento originale.  
- **Quale libreria gestisce la divisione?** GroupDocs.Merger per Java fornisce una semplice API per la divisione per intervalli di righe.  
- **Ho bisogno di una licenza?** Una prova gratuita è sufficiente per i test; è necessaria una licenza permanente per l'uso in produzione.  
- **Posso dividere per conteggio di caratteri invece?** Non direttamente—usa un passaggio di pre‑elaborazione per riformattare il file prima della divisione.  
- **Quale versione di Java è supportata?** Qualsiasi runtime Java 8+ è compatibile.

## Cos'è “split file by lines”?
Dividere un file per righe significa prendere un unico documento di testo e suddividerlo in più file, ognuno contenente un intervallo specifico di righe consecutive (ad esempio, righe 1‑3, 4‑6, ecc.). Questa tecnica è ideale per l'elaborazione batch, l'analisi parallela o semplicemente per migliorare la leggibilità.

## Perché usare GroupDocs.Merger per Java?
GroupDocs.Merger astrae il lavoro di I/O a basso livello, permettendoti di concentrarti sulla logica di business. Gestisce file di grandi dimensioni in modo efficiente, supporta molti formati di documento e offre un'API pulita e fluida che si integra perfettamente con build Maven o Gradle.

## Prerequisiti
- **Java Development Kit (JDK) 8 o superiore** – assicurati che `java` e `javac` siano nel tuo PATH.  
- **GroupDocs.Merger per Java** – aggiungi la libreria tramite Maven, Gradle o un download diretto.  
- **Conoscenza di base di Java** – dovresti sentirti a tuo agio con classi, metodi e gestione delle eccezioni.

## Configurare GroupDocs.Merger per Java
Aggiungi la libreria al tuo progetto usando uno dei metodi seguenti.

**Maven** – incolla questa dipendenza nel tuo `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – includi la seguente riga in `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Download diretto** – puoi anche scaricare il JAR dalla pagina di rilascio ufficiale: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della licenza
Inizia con una prova gratuita per esplorare l'API. Per carichi di lavoro in produzione, ottieni una licenza temporanea o completa dal portale GroupDocs.

## Come dividere un file di testo per righe (implementazione Java)

Di seguito trovi una guida concisa, passo‑per‑passo. Ogni passo è spiegato in linguaggio semplice prima del blocco di codice, così sai esattamente cosa sta succedendo.

### Passo 1: Definire i percorsi di origine e destinazione
Innanzitutto, indica alla libreria dove si trova il tuo file originale e dove devono essere scritti i frammenti divisi.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Passo 2: Configurare le opzioni di divisione
Crea un'istanza di `TextSplitOptions` che descrive gli intervalli di righe desiderati. L'array `new int[] { 3, 6 }` indica all'API di tagliare dopo la riga 3 e la riga 6, producendo due parti: righe 1‑3 e righe 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Passo 3: Inizializzare il Merger ed eseguire la divisione
Infine, istanzia `Merger` con il file di origine e chiama `split()` con le opzioni appena create.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Fatto! Dopo il completamento della chiamata, troverai due nuovi file in `YOUR_OUTPUT_DIRECTORY`, ognuno contenente gli intervalli di righe specificati.

## Applicazioni pratiche (Perché è importante)
1. **Pipeline di elaborazione dati** – Suddividi file di log massivi in blocchi più piccoli per l'analisi parallela.  
2. **Gestione documenti** – Trasforma un unico report in file a livello di capitolo per una distribuzione più semplice.  
3. **Segmentazione dei contenuti** – Prepara sezioni di un articolo lungo per piattaforme di pubblicazione mirate.

## Suggerimenti sulle prestazioni
- **Ottimizzare I/O** – Preferisci `Files.newBufferedReader` quando lavori con file molto grandi per mantenere basso l'uso di memoria.  
- **Chiudere le risorse** – Sebbene GroupDocs.Merger gestisca la maggior parte della pulizia, chiudere esplicitamente eventuali stream personalizzati evita perdite.  
- **Monitorare la memoria** – Dividere file di dimensioni gigabyte può richiedere molta memoria; assegna un heap sufficiente (`-Xmx2g` o superiore) se necessario.

## Problemi comuni e soluzioni

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| `OutOfMemoryError` | Il file di origine è troppo grande e supera l'heap. | Aumenta l'heap JVM o dividi usando intervalli più piccoli. |
| `FileNotFoundException` | Percorso errato o permessi mancanti. | Verifica che `filePath` e `filePathOut` siano assoluti e scrivibili. |
| Empty output files | L'array di intervalli non copre l'intero documento. | Assicurati che l'ultimo intervallo termini al numero totale di righe o oltre. |

## Sezione FAQ

**Q: Posso dividere i file in base al conteggio dei caratteri invece che al numero di righe?**  
A: Attualmente, GroupDocs.Merger per Java si concentra sugli intervalli di righe. Tuttavia, puoi pre‑elaborare il tuo testo per ottenere il conteggio di caratteri desiderato per riga prima di usare questa funzionalità.

**Q: Esiste un limite al numero di intervalli che posso specificare per la divisione?**  
A: Non c'è un limite specifico nella libreria; tuttavia, le prestazioni potrebbero degradarsi con un numero eccessivo di divisioni a causa dell'aumento dei requisiti di elaborazione.

**Q: Come gestisco gli errori durante la divisione dei file?**  
A: Implementa blocchi try‑catch attorno al tuo codice per catturare e gestire le eccezioni in modo efficace. GroupDocs.Merger fornisce messaggi di errore dettagliati che possono aiutare a risolvere i problemi.

**Q: La libreria supporta altri formati basati su testo come CSV o TSV?**  
A: Sì, poiché CSV e TSV sono file di testo semplice, la stessa logica di intervallo di righe si applica. Trattali semplicemente come file `.txt` nell'API.

**Q: Posso automatizzare la divisione per più file in una cartella?**  
A: Assolutamente. Avvolgi la logica sopra in un ciclo che itera su `Files.list(Paths.get("folder"))` e applica le stesse `TextSplitOptions` a ciascun file.

## Risorse
- **Documentazione:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **Riferimento API:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Acquisto e licenze:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Prova gratuita:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Licenza temporanea:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Forum di supporto:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Ultimo aggiornamento:** 2026-02-06  
**Testato con:** GroupDocs.Merger 23.12 for Java  
**Autore:** GroupDocs