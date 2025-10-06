---
title: Mesclando arquivos XLS
linktitle: Mesclando arquivos XLS
second_title: API GroupDocs.Merger .NET
description: Aprenda como mesclar arquivos Excel em .NET usando GroupDocs.Merger para uma manipulação perfeita de documentos. Siga nosso tutorial passo a passo.
weight: 11
url: /pt/net/spreadsheet-merging/merging-xls-files/
type: docs
---
# Mesclando arquivos XLS

## Introdução
Neste tutorial, exploraremos como mesclar arquivos XLS (Excel). GroupDocs.Merger é uma poderosa API de manipulação de documentos que permite aos desenvolvedores mesclar, dividir, reorganizar e manipular documentos sem esforço em seus aplicativos .NET. Especificamente, vamos nos concentrar na fusão de arquivos XLS passo a passo usando os métodos intuitivos do GroupDocs.Merger.
## Pré-requisitos
Antes de começarmos, certifique-se de ter os seguintes pré-requisitos configurados:
- Visual Studio: instale o Visual Studio em sua máquina.
-  GroupDocs.Merger for .NET: Baixe e instale GroupDocs.Merger for .NET em[aqui](https://releases.groupdocs.com/merger/net/).
- .NET Framework: certifique-se de ter o .NET framework instalado.
- Arquivos XLS de amostra: prepare os arquivos XLS que deseja mesclar.

## Importar namespaces
Comece importando os namespaces necessários para usar GroupDocs.Merger em seu projeto:
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## Etapa 1: inicializar o diretório de saída
Primeiro, especifique o diretório onde deseja salvar o arquivo XLS mesclado:
```csharp
string outputFolder = "Your Output Directory";
string outputFile = Path.Combine(outputFolder, "merged.xls");
```
## Etapa 2: carregar e mesclar arquivos XLS
Agora, vamos carregar e mesclar os arquivos XLS usando GroupDocs.Merger:
```csharp
// Carregue o arquivo XLS de origem
using (var merger = new Merger("Your Sample File"))
{
    // Adicione outro arquivo XLS para mesclar
    merger.Join("Your Sample File");
    
    // Mesclar arquivos XLS e salvar o resultado
    merger.Save(outputFile);
}
```
## Etapa 3: Exibir local de saída
Por fim, exiba uma mensagem indicando a conclusão e a localização do arquivo XLS mesclado:
```csharp
Console.WriteLine("\nXLS files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## Conclusão
Neste tutorial, aprendemos como mesclar arquivos XLS. Seguindo as etapas fornecidas, você pode combinar com eficiência vários arquivos Excel de forma programática em seus aplicativos .NET.

## Perguntas frequentes
### O GroupDocs.Merger é compatível com outros formatos de documento?
Sim, GroupDocs.Merger oferece suporte a vários formatos de documento, como PDF, DOCX, XLSX, PPTX e muito mais.
### Posso dividir documentos usando GroupDocs.Merger?
Absolutamente! GroupDocs.Merger permite dividir documentos com base em seus requisitos.
### Onde posso encontrar mais recursos e suporte para GroupDocs.Merger?
Você pode explorar a documentação e fazer perguntas no site[Fórum GroupDocs](https://forum.groupdocs.com/c/merger/32).
### Existe um teste gratuito disponível para GroupDocs.Merger?
 Sim, você pode começar com um[teste grátis](https://releases.groupdocs.com/) para avaliar a funcionalidade.
### Como posso adquirir uma licença para GroupDocs.Merger?
 Visite a[página de compra](https://purchase.groupdocs.com/buy) para adquirir uma licença adaptada às suas necessidades.