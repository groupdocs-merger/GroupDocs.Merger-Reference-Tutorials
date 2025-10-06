---
title: Unione di file XLS
linktitle: Unione di file XLS
second_title: API GroupDocs.Merger .NET
description: Scopri come unire file Excel in .NET utilizzando GroupDocs.Merger per una manipolazione fluida dei documenti. Segui il nostro tutorial passo dopo passo.
weight: 11
url: /it/net/spreadsheet-merging/merging-xls-files/
type: docs
---
# Unione di file XLS

## introduzione
In questo tutorial esploreremo come unire file XLS (Excel). GroupDocs.Merger è una potente API per la manipolazione dei documenti che consente agli sviluppatori di unire, dividere, riorganizzare e manipolare i documenti senza sforzo all'interno delle loro applicazioni .NET. Nello specifico, ci concentreremo sull'unione dei file XLS passo dopo passo utilizzando i metodi intuitivi di GroupDocs.Merger.
## Prerequisiti
Prima di iniziare, assicurati di aver configurato i seguenti prerequisiti:
- Visual Studio: installa Visual Studio sul tuo computer.
-  GroupDocs.Merger per .NET: scarica e installa GroupDocs.Merger per .NET da[Qui](https://releases.groupdocs.com/merger/net/).
- .NET Framework: assicurati di avere installato .NET Framework.
- File XLS di esempio: prepara i file XLS che desideri unire.

## Importa spazi dei nomi
Inizia importando gli spazi dei nomi necessari per utilizzare GroupDocs.Merger nel tuo progetto:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Passaggio 1: inizializzare la directory di output
Innanzitutto, specifica la directory in cui desideri salvare il file XLS unito:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Passaggio 2: carica e unisci file XLS
Ora carichiamo e uniamo i file XLS utilizzando GroupDocs.Merger:
```csharp
// Carica il file XLS di origine
using (var merger = new Merger("Your Sample File"))
{
    // Aggiungi un altro file XLS da unire
    merger.Join("Your Sample File");
    
    // Unisci file XLS e salva il risultato
    merger.Save(outputFile);
}
```
## Passaggio 3: Visualizza la posizione di output
Infine, visualizza un messaggio che indica il completamento e la posizione del file XLS unito:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusione
In questo tutorial, abbiamo imparato come unire file XLS. Seguendo i passaggi forniti, è possibile combinare in modo efficiente più file Excel a livello di codice all'interno delle applicazioni .NET.

## Domande frequenti
### GroupDocs.Merger è compatibile con altri formati di documenti?
Sì, GroupDocs.Merger supporta vari formati di documenti come PDF, DOCX, XLSX, PPTX e altri.
### Posso dividere i documenti utilizzando GroupDocs.Merger?
Assolutamente! GroupDocs.Merger ti consente di dividere i documenti in base alle tue esigenze.
### Dove posso trovare ulteriori risorse e supporto per GroupDocs.Merger?
È possibile esplorare la documentazione e porre domande su[Forum di GroupDocs](https://forum.groupdocs.com/c/merger/32).
### È disponibile una prova gratuita per GroupDocs.Merger?
 Sì, puoi iniziare con a[prova gratuita](https://releases.groupdocs.com/) per valutarne la funzionalità.
### Come posso acquistare una licenza per GroupDocs.Merger?
 Visitare il[pagina di acquisto](https://purchase.groupdocs.com/buy) per acquisire una licenza su misura per le tue esigenze.