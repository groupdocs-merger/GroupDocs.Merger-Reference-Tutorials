---
title: Guida all'unione di file XLSM
linktitle: Guida all'unione di file XLSM
second_title: API GroupDocs.Merger .NET
description: Unisci file XLSM senza problemi con GroupDocs.Merger per .NET. Combina in modo efficiente le cartelle di lavoro di Excel a livello di codice. Migliora le tue capacità di manipolazione dei documenti.
weight: 13
url: /it/net/spreadsheet-merging/guide-merging-xlsm-files/
type: docs
---
# Guida all'unione di file XLSM

## introduzione
In questo tutorial esploreremo come unire file XLSM (Excel Macro-Enabled Workbook). GroupDocs.Merger è una potente libreria che consente agli sviluppatori di manipolare i formati di documenti, inclusa l'unione, la divisione e la modifica dei file a livello di codice.
## Prerequisiti
Prima di iniziare, assicurati di avere quanto segue:
-  GroupDocs.Merger per .NET: scarica e installa la libreria da[Qui](https://releases.groupdocs.com/merger/net/).
- Ambiente di sviluppo: imposta Visual Studio o qualsiasi ambiente di sviluppo .NET compatibile.
- File XLSM: prepara i file XLSM che desideri unire.

## Importa spazi dei nomi
Innanzitutto, includi gli spazi dei nomi necessari nel tuo progetto .NET:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Passaggio 1: definire la cartella di output e il nome del file
Inizia definendo la cartella di output e il nome del file XLSM unito:
```csharp
string outputFolder = "YourOutputDirectory";
string outputFile = Path.Combine(outputFolder, "merged.xlsm");
```
## Passaggio 2: carica e unisci file XLSM
Successivamente, carica i file XLSM di origine e uniscili in un unico file:
```csharp
// Carica il file XLSM di origine
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // Aggiungi un altro file XLSM da unire
    merger.Join("Your Sample File");
    // Unisci i file XLSM e salva il risultato
    merger.Save(outputFile);
}
```
## Passaggio 3: controlla il completamento dell'unione
Infine, avvisa l'utente del corretto completamento dell'unione e visualizza il percorso di output:
```csharp
Console.WriteLine("\nXLSM files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusione
Hai imparato come unire i file XLSM a livello di codice. Questa libreria semplifica le attività di manipolazione dei documenti, consentendo un'efficiente fusione dei file all'interno delle applicazioni .NET.

## Domande frequenti
### GroupDocs.Merger può gestire file XLSM di grandi dimensioni?
Sì, GroupDocs.Merger gestisce in modo efficiente file XLSM di grandi dimensioni senza problemi di prestazioni.
### GroupDocs.Merger supporta altri formati di file oltre a XLSM?
Sì, GroupDocs.Merger supporta vari formati di documenti come DOCX, PDF, PPTX e altri.
### GroupDocs.Merger è compatibile con le applicazioni .NET Core?
Sì, GroupDocs.Merger è compatibile sia con gli ambienti .NET Framework che .NET Core.
### Posso unire file XLSM crittografati utilizzando GroupDocs.Merger?
Sì, GroupDocs.Merger supporta l'unione di file XLSM crittografati con le credenziali corrette.
### GroupDocs.Merger fornisce funzionalità di elaborazione batch?
Sì, GroupDocs.Merger consente l'elaborazione batch per unire più file XLSM contemporaneamente.