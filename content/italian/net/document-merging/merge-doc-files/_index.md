---
title: Unisci file DOC con GroupDocs.Merger per .NET
linktitle: Unisci file DOC con GroupDocs.Merger per .NET
second_title: API GroupDocs.Merger .NET
description: Scopri come unire i file DOC a livello di codice utilizzando GroupDocs.Merger per .NET. Segui la nostra guida passo passo per combinare facilmente più documenti in uno solo.
type: docs
weight: 10
url: /it/net/document-merging/merge-doc-files/
---
## introduzione
In questo tutorial esploreremo come unire file DOC utilizzando GroupDocs.Merger per .NET. GroupDocs.Merger per .NET è una potente API che consente agli sviluppatori di combinare, dividere e manipolare vari formati di documenti a livello di codice. Sfruttando questa API, puoi unire senza problemi più file DOC in un unico documento. Forniremo istruzioni dettagliate per guidarti attraverso il processo di unione dei file DOC utilizzando GroupDocs.Merger per .NET.
## Prerequisiti
Prima di iniziare, assicurati di avere configurati i seguenti prerequisiti:
1. Visual Studio: installa Visual Studio nel tuo computer di sviluppo.
2.  GroupDocs.Merger per .NET: ottenere la libreria GroupDocs.Merger per .NET. Puoi scaricarlo da[sito web](https://releases.groupdocs.com/merger/net/).
3. Conoscenza di C#: Conoscenza di base del linguaggio di programmazione C#.
## Importa spazi dei nomi
Per iniziare a lavorare con GroupDocs.Merger per .NET, importa gli spazi dei nomi necessari nel tuo progetto C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Passaggio 1: impostare la directory di output
Inizia specificando la directory di output in cui verrà salvato il file DOC unito:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.doc");
```
 Sostituire`"Your Output Directory"` con il percorso della cartella di output desiderata.
## Passaggio 2: caricare i file DOC di origine
Successivamente, carica i file DOC di origine che desideri unire utilizzando GroupDocs.Merger:
```csharp
using (var merger = new Merger("Your Sample Document File"))
{
    // Aggiungi un altro file DOC da unire
    merger.Join("Your Sample Document File 2");
    // Unisci i file DOC e salva il risultato
    merger.Save(outputFile);
}
```
In questo frammento di codice:
- `"Your Sample Document File"` E`"Your Sample Document File 2"` rappresentano i percorsi dei file DOC che desideri unire.
- `merger.Join(...)` viene utilizzato per aggiungere un altro file DOC all'operazione di unione.
- `merger.Save(outputFile)` combina i file DOC caricati e salva il documento unito nel file di output specificato (`merged.doc`).
 Assicurati di sostituire`"Your Sample Document File"` E`"Your Sample Document File 2"` con i percorsi effettivi dei tuoi file DOC.
## Conclusione
In questo tutorial, abbiamo trattato il processo di unione dei file DOC utilizzando GroupDocs.Merger per .NET. Seguendo i passaggi sopra descritti, è possibile combinare in modo efficace più file DOC in un singolo documento a livello di codice. GroupDocs.Merger per .NET fornisce un modo semplice ed efficiente per manipolare i formati di documenti all'interno delle applicazioni .NET.

## Domande frequenti
### GroupDocs.Merger per .NET può gestire altri formati di documenti oltre a DOC?
Sì, GroupDocs.Merger per .NET supporta l'unione di vari formati di documenti come DOCX, PDF, XLSX, PPTX e altri.
### GroupDocs.Merger per .NET è compatibile con .NET Core?
Sì, GroupDocs.Merger per .NET è compatibile con .NET Core e .NET Framework.
### GroupDocs.Merger per .NET richiede una licenza per uso commerciale?
 Sì, per l'uso commerciale è necessaria una licenza valida. È possibile ottenere una licenza da[GroupDocs](https://purchase.groupdocs.com/buy).
### Posso provare GroupDocs.Merger per .NET gratuitamente?
 Sì, puoi esplorare GroupDocs.Merger per .NET con una prova gratuita disponibile[Qui](https://releases.groupdocs.com/).
### Dove posso ottenere supporto tecnico per GroupDocs.Merger per .NET?
 Per assistenza tecnica e supporto comunitario, visitare il[Forum di GroupDocs](https://forum.groupdocs.com/c/merger/32).