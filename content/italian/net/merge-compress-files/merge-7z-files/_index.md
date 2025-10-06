---
title: Come unire file 7z
linktitle: Come unire file 7z
second_title: API GroupDocs.Merger .NET
description: Unisci facilmente file 7z utilizzando GroupDocs.Merger per .NET. Segui la nostra guida passo passo per combinare più archivi in uno solo senza problemi.
weight: 10
url: /it/net/merge-compress-files/merge-7z-files/
type: docs
---
# Come unire file 7z

## introduzione
L'unione di file 7z può essere eseguita in modo efficiente utilizzando GroupDocs.Merger per .NET, una potente libreria per la manipolazione dei documenti. Questo tutorial ti guiderà attraverso il processo passo dopo passo, permettendoti di unire facilmente i tuoi file 7z.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio installato nel sistema.
-  GroupDocs.Merger per la libreria .NET installata. Puoi scaricarlo da[Qui](https://releases.groupdocs.com/merger/net/).
- Conoscenza di base della programmazione C#.

## Importa spazi dei nomi
Innanzitutto, includi gli spazi dei nomi necessari nel codice C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Passaggio 1: caricare il file 7Z di origine
Inizia specificando la directory di output e il nome del file per il file 7z unito:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Passaggio 2: unisci i file 7Z
Carica il file 7Z di origine e aggiungi un altro file 7Z che desideri unire:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Passaggio 3: salva il file 7Z unito
Esegui l'operazione di unione e salva il file 7Z unito risultante:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusione
In questo tutorial, abbiamo esplorato come unire file 7z utilizzando GroupDocs.Merger per .NET. Seguendo questi semplici passaggi, puoi combinare in modo efficiente più file 7z in un unico archivio unificato.

## Domande frequenti
### Posso unire più di due file 7z utilizzando GroupDocs.Merger?
 Sì, puoi unire insieme un numero qualsiasi di file 7z utilizzando questa libreria. Aggiungi semplicemente ciascun file utilizzando il file`Join` metodo.
### GroupDocs.Merger per .NET è compatibile con altri formati di archivio?
Sì, GroupDocs.Merger supporta l'unione di vari formati di documenti, inclusi archivi come ZIP, 7z e RAR.
### Dove posso trovare ulteriore supporto o assistenza con GroupDocs.Merger?
 Per ulteriore assistenza, visitare il[Forum GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### Posso provare GroupDocs.Merger per .NET prima dell'acquisto?
 Sì, puoi esplorare le funzionalità di GroupDocs.Merger scaricando il file[versione di prova gratuita](https://releases.groupdocs.com/).
### Come posso ottenere una licenza temporanea per GroupDocs.Merger?
 Se hai bisogno di una licenza temporanea, visita[Qui](https://purchase.groupdocs.com/temporary-license/).