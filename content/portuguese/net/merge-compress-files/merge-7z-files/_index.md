---
title: Como mesclar arquivos 7z
linktitle: Como mesclar arquivos 7z
second_title: API GroupDocs.Merger .NET
description: Mescle arquivos 7z sem esforço usando GroupDocs.Merger for .NET. Siga nosso guia passo a passo para combinar vários arquivos em um perfeitamente.
type: docs
weight: 10
url: /pt/net/merge-compress-files/merge-7z-files/
---
## Introdução
mesclagem de arquivos 7z pode ser feita com eficiência usando GroupDocs.Merger for .NET, uma poderosa biblioteca de manipulação de documentos. Este tutorial irá guiá-lo através do processo passo a passo, permitindo que você mescle seus arquivos 7z com facilidade.
## Pré-requisitos
Antes de começar, certifique-se de ter o seguinte:
- Visual Studio instalado em seu sistema.
-  Biblioteca GroupDocs.Merger para .NET instalada. Você pode baixá-lo em[aqui](https://releases.groupdocs.com/merger/net/).
- Compreensão básica de programação C#.

## Importar namespaces
Primeiro, inclua os namespaces necessários em seu código C#:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Etapa 1: Carregar arquivo fonte 7Z
Comece especificando o diretório de saída e o nome do arquivo 7z mesclado:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.7z");
```
## Etapa 2: mesclar arquivos 7Z
Carregue o arquivo 7Z de origem e adicione outro arquivo 7Z que deseja mesclar:
```csharp
using (var merger = new Merger("Your Sample File"))
{
    merger.Join("Your Sample File");
    merger.Save(outputFile);
}
```
## Etapa 3: salvar o arquivo 7Z mesclado
Execute a operação de mesclagem e salve o arquivo 7Z mesclado resultante:
```csharp
Console.WriteLine("\n7Z files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusão
Neste tutorial, exploramos como mesclar arquivos 7z usando GroupDocs.Merger for .NET. Seguindo essas etapas simples, você pode combinar com eficiência vários arquivos 7z em um arquivo único e unificado.

## Perguntas frequentes
### Posso mesclar mais de dois arquivos 7z usando GroupDocs.Merger?
 Sim, você pode mesclar qualquer número de arquivos 7z usando esta biblioteca. Basta adicionar cada arquivo usando o`Join` método.
### O GroupDocs.Merger for .NET é compatível com outros formatos de arquivo?
Sim, GroupDocs.Merger suporta a fusão de vários formatos de documentos, incluindo arquivos como ZIP, 7z e RAR.
### Onde posso encontrar suporte ou assistência adicional com GroupDocs.Merger?
 Para obter mais assistência, visite o[Fórum GroupDocs.Merger](https://forum.groupdocs.com/c/merger/32).
### Posso experimentar o GroupDocs.Merger for .NET antes de comprar?
 Sim, você pode explorar as funcionalidades do GroupDocs.Merger baixando o[versão de teste gratuita](https://releases.groupdocs.com/).
### Como posso obter uma licença temporária para GroupDocs.Merger?
 Se você precisar de uma licença temporária, visite[aqui](https://purchase.groupdocs.com/temporary-license/).