---
date: '2026-08-20'
description: Aprenda como mesclar PDFs com marcadores usando GroupDocs.Merger para
  .NET, incluindo configuração, exemplos de código e boas práticas para combinar documentos
  PDF.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: Aprenda como mesclar PDFs com marcadores usando GroupDocs.Merger para
  .NET. Siga o código passo a passo para combinar documentos PDF preservando a navegação.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: Como mesclar PDFs com marcadores usando GroupDocs.Merger para .NET
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
title: Como mesclar PDFs com marcadores usando GroupDocs.Merger para .NET
type: docs
url: /pt/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# Como mesclar PDFs com marcadores usando GroupDocs.Merger para .NET

Mesclar vários arquivos PDF mantendo seus marcadores originais intactos pode economizar horas de reorganização manual. Neste tutorial você aprenderá a **mesclar PDFs com marcadores** usando GroupDocs.Merger para .NET, desde a configuração do projeto até um exemplo de código completo e pronto para produção.

## Respostas rápidas
- **Qual biblioteca suporta mesclagens que preservam marcadores?** GroupDocs.Merger para .NET.  
- **Posso mesclar mais de dois PDFs de uma vez?** Sim – adicione quantos arquivos de origem precisar.  
- **Preciso de licença para desenvolvimento?** Um teste gratuito funciona para testes; uma licença permanente é necessária para produção.  
- **O .NET Core é suportado?** Absolutamente – a biblioteca funciona com .NET Core, .NET 5/6 e o .NET Framework completo.  
- **Qual é o maior tamanho de arquivo que pode manipular?** Até 2 GB por documento, processado sem carregar o arquivo inteiro na memória.

## O que é mesclar PDFs com marcadores?
**Mesclar PDFs com marcadores** significa pegar vários documentos PDF e combiná‑los em um único arquivo mantendo a hierarquia de marcadores de cada documento de origem intacta. O PDF resultante retém a estrutura de navegação original, permitindo que os leitores pulem diretamente para as seções que se originaram de cada arquivo individual, o que é essencial para relatórios extensos ou manuais compilados.

## Por que mesclar PDFs com marcadores?
Preservar marcadores ao mesclar PDFs melhora a navegação em documentos consolidados, permitindo que os usuários localizem rapidamente capítulos ou seções específicas sem percorrer todo o arquivo. GroupDocs.Merger mantém a hierarquia de contorno original, reduz o esforço de reorganização manual e suporta arquivos grandes de até 2 GB usando memória mínima, tornando‑a ideal para fluxos de trabalho em escala empresarial.

## Pré‑requisitos
- **.NET Core SDK** (3.1 ou posterior) ou **.NET Framework** (4.6.1+).  
- **Visual Studio 2022** ou qualquer IDE que suporte desenvolvimento .NET.  
- Conhecimento básico de C# e familiaridade com I/O de arquivos.  

## Configurando GroupDocs.Merger para .NET

### Instalação
Adicione a biblioteca ao seu projeto com um dos seguintes comandos:

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

**NuGet Package Manager UI:**  
- Pesquise por “GroupDocs.Merger” e instale a versão mais recente.

### Aquisição de licença
- **Teste gratuito:** Baixe na página de [GroupDocs Releases](https://releases.groupdocs.com/merger/net/).  
- **Licença temporária:** Obtenha uma via [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/).  
- **Licença completa:** Compre na [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy).

### Inicialização básica
A classe `Merger` é o ponto de entrada para todas as operações de mesclagem.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
Este namespace fornece acesso ao conjunto completo de recursos de manipulação de PDF.

## Como mesclar PDFs com marcadores em .NET

Carregue seu PDF principal, configure o tratamento de marcadores, adicione arquivos adicionais e salve o resultado – tudo em poucas linhas concisas de código.

**Resposta direta (40‑70 palavras):**  
Crie uma instância `Merger` com o primeiro PDF, habilite `PdfJoinOptions.UseBookmarks`, adicione cada PDF subsequente via `Join` e chame `Save` para gravar o arquivo combinado. Essa abordagem preserva toda a hierarquia de marcadores original e executa em uma única passagem, minimizando o consumo de memória.

### Etapa 1: definir caminhos de diretórios
Configure pastas de origem e de saída para que o código possa localizar os PDFs que você deseja mesclar.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### Etapa 2: carregar o PDF principal
`Merger` representa o documento principal ao qual você anexará os demais.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // O código para mesclar arquivos adicionais ficará aqui.
   }
   ```  
```  

### Etapa 3: configurar opções que preservam marcadores
`PdfJoinOptions` controla como a mesclagem se comporta; a flag `UseBookmarks` indica ao mecanismo que deve manter os marcadores existentes.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### Etapa 4: adicionar PDFs adicionais
Chame `Join` para cada arquivo extra. A biblioteca mescla automaticamente as árvores de marcadores sob o contorno do documento principal.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### Etapa 5: salvar o PDF mesclado
Especifique o caminho de saída e o formato; a biblioteca grava um único PDF que retém todas as entradas de marcadores.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## Problemas comuns e soluções
- **Marcadores ausentes:** Verifique `UseBookmarks = true` em `PdfJoinOptions`.  
- **Erros de caminho:** Use `Path.Combine` e verifique a existência dos arquivos antes de mesclar.  
- **Arquivos grandes causam picos de memória:** Processe PDFs sequencialmente e descarte o objeto `Merger` após cada salvamento.

## Aplicações práticas
1. **Consolidação de relatórios financeiros** – mantenha as seções trimestrais instantaneamente acessíveis via marcadores.  
2. **Pacotes de material de curso** – mescle PDFs de aulas preservando a navegação por capítulos para os estudantes.  
3. **Pacotes de documentação de projetos** – combine especificações de design, planos de teste e notas de release em um único arquivo pesquisável.

## Considerações de desempenho
- Processe um arquivo de cada vez ao mesclar mais de 20 PDFs para manter o uso de RAM baixo.  
- Use a runtime .NET mais recente (por exemplo, .NET 6) para compilação JIT e eficiência de coleta de lixo otimizadas.  
- Para PDFs maiores que 500 MB, habilite o modo de streaming via `MergerSettings` para evitar carregar todo o documento na memória.

## Perguntas frequentes

**Q: O que é GroupDocs.Merger?**  
A: GroupDocs.Merger é uma biblioteca .NET que permite mesclar, dividir, girar e manipular programaticamente PDFs e outros formatos de documento.

**Q: Posso mesclar mais de dois arquivos PDF ao mesmo tempo?**  
A: Sim – chame `Join` repetidamente ou passe uma coleção de caminhos de arquivos para mesclar qualquer número de PDFs em uma única operação.

**Q: Como devo lidar com licenciamento para uso em produção?**  
A: Obtenha uma licença permanente na página de compra da GroupDocs; a licença de teste funciona apenas para avaliação e expira após 30 dias.

**Q: Meu PDF mesclado não mostra marcadores — o que deu errado?**  
A: Certifique‑se de que `PdfJoinOptions.UseBookmarks` está definido como `true` e que cada PDF de origem realmente contém marcadores antes da mesclagem.

**Q: A biblioteca é compatível com .NET Core e .NET Framework?**  
A: Absolutamente – ela suporta .NET Core 3.1+, .NET 5/6 e o .NET Framework completo 4.6.1+.

## Recursos
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**Última atualização:** 2026-08-20  
**Testado com:** GroupDocs.Merger 23.11 for .NET  
**Autor:** GroupDocs

## Tutoriais relacionados

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)