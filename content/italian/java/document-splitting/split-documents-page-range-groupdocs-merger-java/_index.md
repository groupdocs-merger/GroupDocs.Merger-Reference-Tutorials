---
date: '2026-02-06'
description: Scopri come estrarre pagine specifiche e dividere i documenti per intervallo
  di pagine usando GroupDocs.Merger per Java, inclusi i filtri per pagine dispari/pari.
keywords:
- GroupDocs.Merger for Java
- split documents by page range
- document management
title: Estrai pagine specifiche con GroupDocs.Merger per Java
type: docs
url: /it/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Estrai Pagine Specifiche con GroupDocs.Merger per Java

Estrai in modo efficiente **pagine specifiche** da PDF di grandi dimensioni, file Word o presentazioni senza copia‑incolla manuale. In questo tutorial vedrai come dividere un documento per intervallo di pagine, applicare filtri come pagine dispari/pari e generare file a pagina singola — tutto con **GroupDocs.Merger per Java**.

## Risposte Rapide
- **Cosa significa “estrarre pagine specifiche”?** Significa creare nuovi documenti che contengono solo le pagine selezionate dal file di origine.  
- **Quali formati sono supportati?** PDF, DOCX, PPTX e molti altri formati popolari.  
- **Posso filtrare per pagine dispari o pari?** Sì, usando l'opzione `RangeMode` (ad es., `OddPages`).  
- **È necessaria una licenza?** Una prova gratuita è sufficiente per la valutazione; è richiesta una licenza permanente per la produzione.  
- **È adatto a documenti di grandi dimensioni?** Sì — dividi sezioni di documenti grandi per mantenere basso l'uso della memoria.

## Cos'è l'estrazione di pagine specifiche?
L'estrazione di pagine specifiche è il processo di prendere un sottoinsieme di pagine da un documento di origine e salvarle come un nuovo file indipendente. È utile per creare report mirati, condividere clausole di contratti o preparare dispense di presentazioni.

## Perché usare GroupDocs.Merger per Java per dividere PDF e documenti Word?
- **API Unificata** – Funziona con PDF, Word, PowerPoint e altro, così non hai bisogno di strumenti separati.  
- **Fine‑grained control** – Choose exact page ranges, odd/even filters, or single‑page splits.  
- **Performance‑focused** – Gestisce file di grandi dimensioni in modo efficiente trasmettendo le pagine in streaming invece di caricare l'intero documento in memoria.  

## Prerequisiti
- **GroupDocs.Merger per Java** (ultima versione)  
- **JDK 8+**  
- Un IDE come IntelliJ IDEA o Eclipse  
- Maven o Gradle per la gestione delle dipendenze  

## Configurazione di GroupDocs.Merger per Java
Aggiungi la libreria al tuo progetto usando lo strumento di build preferito.

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

**Download Diretto**: Puoi anche scaricare la libreria direttamente da [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Acquisizione della Licenza
Puoi acquisire una licenza attraverso:
- **Free Trial** – Prova tutte le funzionalità senza limitazioni.  
- **Temporary License** – Periodo di valutazione esteso.  
- **Purchase** – Licenza permanente per la produzione.

**Inizializzazione di Base e Configurazione**  
Per inizializzare GroupDocs.Merger, crea un'istanza di `Merger` con il percorso del tuo documento:
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Come estrarre pagine specifiche usando GroupDocs.Merger per Java
Questa sezione ti guida nella divisione di un documento per intervallo di pagine applicando un filtro per pagine dispari.

### Passo 1: Definisci i Percorsi di Input e Output
Imposta il file di origine e il modello di destinazione per i file divisi:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Passo 2: Configura le Opzioni di Divisione (Intervallo & Filtro)
Crea un oggetto `SplitOptions` che indica alla libreria quali pagine estrarre e quale filtro applicare:
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```
- **filePathOut** – Modello di nome file di destinazione.  
- **3 e 7** – Numeri di pagina di inizio e fine (inclusivi).  
- **RangeMode.OddPages** – Mantiene solo le pagine dispari all'interno dell'intervallo, estraendo effettivamente **pagine specifiche**.

### Passo 3: Esegui l'Operazione di Divisione
Esegui la divisione usando le opzioni configurate:
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Suggerimenti per la Risoluzione dei Problemi
- Verifica che i percorsi dei file siano corretti e accessibili.  
- Assicurati che i numeri di pagina siano entro il conteggio totale delle pagine del documento; altrimenti verrà generata un'eccezione.  

## Come dividere un PDF in pagine singole (split pdf single pages)
Se ti serve ogni pagina come PDF individuale, imposta semplicemente `RangeMode` a `AllPages` e specifica un intervallo che copra l'intero documento. La stessa classe `SplitOptions` gestisce questo scenario.

## Come dividere un documento grande in modo efficiente (split large document)
Quando si lavora con file molto grandi, considera di dividerli in intervalli più piccoli (ad es., 1‑100, 101‑200) per ridurre la pressione sulla memoria. Chiudi l'istanza `Merger` dopo ogni operazione per liberare le risorse.

## Come dividere le pagine dispari di un PDF (split pdf odd pages)
L'esempio sopra dimostra già il filtro `OddPages`. Sostituisci `RangeMode.OddPages` con `RangeMode.EvenPages` per estrarre le pagine pari invece.

## Applicazioni Pratiche
1. **Segmentazione dei Documenti** – Dividi i contratti in PDF a livello di clausola per una revisione più semplice.  
2. **Gestione dei Report** – Estrai un capitolo o un'appendice specifica da un lungo rapporto annuale.  
3. **Preparazione di Presentazioni** – Isola diapositive individuali per riunioni mirate.  

Puoi anche integrare questa logica con database o sistemi di gestione dei contenuti per automatizzare i flussi di lavoro.

## Considerazioni sulle Prestazioni
- **Gestione della Memoria** – Chiama `merger.close()` (o utilizza try‑with‑resources) dopo l'elaborazione per rilasciare i handle dei file.  
- **Intervalli Selettivi** – Richiedi solo le pagine di cui hai realmente bisogno; questo minimizza l'I/O e l'uso della CPU.  

## Conclusione
Ora disponi di un metodo chiaro, passo‑per‑passo, per **estrarre pagine specifiche** da qualsiasi tipo di documento supportato usando GroupDocs.Merger per Java. Questa funzionalità semplifica i tuoi flussi di lavoro documentali e ti consente di fornire esattamente il contenuto di cui i tuoi utenti hanno bisogno.

### Prossimi Passi
- Sperimenta con diversi valori di `RangeMode` (ad es., `EvenPages`, `AllPages`).  
- Combina la divisione con la funzionalità di **merge** per riordinare o concatenare le pagine estratte.  
- Esplora l'API completa per documenti protetti da password, filigrane e altro.  

## Domande Frequenti
**Q: Cos'è GroupDocs.Merger per Java?**  
A: Una libreria robusta che consente di unire, dividere e riordinare pagine su molti formati di documento.

**Q: Posso usare GroupDocs.Merger con altri linguaggi di programmazione?**  
A: Sì, esistono funzionalità simili per .NET e C++.

**Q: Come gestisco le eccezioni durante l'elaborazione dei documenti?**  
A: Avvolgi le chiamate in blocchi `try‑catch` e ispeziona `MergerException` per informazioni dettagliate sull'errore.

**Q: È possibile dividere i documenti senza filtrare per pagine dispari/parI?**  
A: Assolutamente — imposta `RangeMode.AllPages` o ometti il parametro di filtro per dividere per numeri di pagina esatti.

**Q: Quali sono i requisiti di sistema per usare GroupDocs.Merger?**  
A: Java 8 o superiore e un IDE compatibile; nessuna dipendenza nativa aggiuntiva.

## Risorse
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download the Library](https://releases.groupdocs.com/merger/java/)
- [Purchase License](https://purchase.groupdocs.com/buy)
- [Free Trial and Temporary License](https://releases.groupdocs.com/merger/java/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Ultimo Aggiornamento:** 2026-02-06  
**Testato Con:** ultima versione di GroupDocs.Merger (Java)  
**Autore:** GroupDocs