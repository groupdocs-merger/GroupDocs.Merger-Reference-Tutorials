---
date: 2026-08-31
description: Aprenda a extrair páginas específicas de PDF usando o GroupDocs.Merger
  para .NET. Guias passo a passo cobrem cenários de extração de Word, PDF e DOCX.
keywords:
- extract specific pages pdf
- how to extract pages
- extract pages from word
- extract pages from docx
- extract pages from pdf
lastmod: 2026-08-31
og_description: Aprenda a extrair páginas específicas de PDF usando o GroupDocs.Merger
  para .NET. Guias detalhados ajudam a extrair páginas de arquivos PDF, Word e DOCX
  de forma eficiente.
og_image_alt: Guide showing how to extract specific pages from PDF documents using
  GroupDocs.Merger for .NET
og_title: Como extrair páginas específicas de PDF com GroupDocs.Merger
schemas:
- author: GroupDocs
  dateModified: '2026-08-31'
  description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  headline: How to extract specific pages pdf with GroupDocs.Merger
  type: TechArticle
- description: Learn how to extract specific pages pdf using GroupDocs.Merger for
    .NET. Step-by-step guides cover Word, PDF, and DOCX extraction scenarios.
  name: How to extract specific pages pdf with GroupDocs.Merger
  steps:
  - name: create a merger instance
    text: The `Merger` class is the entry point for loading and manipulating documents.
      Instantiate the `Merger` class by passing the path of the source file. This
      object represents the document you will work with.
  - name: specify pages to extract
    text: Provide a list of page indexes (1‑based) or a range string such as `"1-3,5"`
      to tell the library which pages to keep.
  - name: save the extracted document
    text: Call `Save` on the `Document` object, supplying the output path and desired
      format (e.g., `SaveFormat.Pdf`). `SaveFormat` is an enumeration that specifies
      the output file type, such as PDF. The operation writes a new file containing
      only the selected pages.
  type: HowTo
- questions:
  - answer: Yes – the same `Extract` call works for DOCX, and you can save the result
      directly as PDF using `SaveFormat.Pdf`.
    question: Can I extract pages from a Word document as PDF?
  - answer: Absolutely. Provide a comma‑separated list like `"2,4,7"` or a mixed range
      `"1-2,5,8-10"`.
    question: Is it possible to extract non‑consecutive pages?
  - answer: Yes. Supply the password when opening the document; the API will decrypt
      it automatically.
    question: Does the library support encrypted PDFs?
  - answer: Images are preserved exactly as they appear on the selected pages; no
      extra conversion steps are needed.
    question: How does GroupDocs.Merger handle images inside PDFs?
  - answer: .NET Framework 4.6+, .NET Core 3.1+, and .NET 5/6/7 are fully supported.
    question: What .NET versions are officially supported?
  type: FAQPage
tags:
- document extraction
- GroupDocs.Merger
- .NET
- PDF processing
title: Como extrair páginas específicas de PDF com GroupDocs.Merger
type: docs
url: /pt/net/document-extraction/
weight: 9
---

# Como extrair páginas específicas de PDF com GroupDocs.Merger

Extrair páginas específicas de PDF é uma necessidade comum quando você precisa reutilizar, compartilhar ou arquivar apenas uma parte de um documento maior. Com o GroupDocs.Merger para .NET, você pode programaticamente retirar páginas individuais, intervalos de páginas ou seleções personalizadas de arquivos PDF, Word e DOCX sem edição manual. Este tutorial orienta você pelos conceitos, pré‑requisitos e fluxo de trabalho passo a passo para integrar a extração de páginas em qualquer aplicação .NET.

## Respostas rápidas
- **O que significa “extrair páginas específicas de PDF”?** Significa selecionar páginas individuais ou intervalos de um PDF (ou outro formato suportado) e salvá‑las como um novo documento menor.  
- **Quais formatos são suportados?** O GroupDocs.Merger lida com mais de 50 formatos de entrada e saída, incluindo PDF, DOCX, PPTX e imagens.  
- **Preciso de uma licença?** Uma licença temporária funciona para testes; uma licença completa é necessária para uso em produção.  
- **Posso processar arquivos grandes?** Sim – a biblioteca processa arquivos com centenas de páginas usando streaming, mantendo o uso de memória baixo.  
- **O .NET Core é suportado?** Absolutamente – a API funciona com .NET Framework 4.6+, .NET Core 3.1+, e .NET 6/7.

## O que é extrair páginas específicas de PDF?
`extrair páginas específicas de PDF` refere‑se à operação de pegar uma ou mais páginas de um PDF existente (ou documento suportado) e criar um novo PDF que contenha apenas essas páginas. Isso permite que você compartilhe apenas as seções relevantes mantendo o arquivo original intacto.

## Por que extrair páginas específicas de PDF com GroupDocs.Merger?
O GroupDocs.Merger processa até **mais de 50 formatos de arquivo** e pode extrair páginas de documentos com **mais de 500 páginas** em menos de **2 segundos** em um CPU típico de servidor. A API funciona sem exigir Microsoft Office ou Adobe Acrobat instalados, o que reduz a complexidade de implantação e os custos de licenciamento.

## Pré-requisitos
- .NET 6 SDK (ou .NET Core 3.1 / .NET Framework 4.6+) instalado na sua máquina de desenvolvimento.  
- Um pacote NuGet válido do GroupDocs.Merger para .NET (`GroupDocs.Merger`) adicionado ao seu projeto.  
- (Opcional) Um arquivo de licença temporária ou completa se você planeja executar o código além do período de avaliação.

## Como extrair páginas específicas de PDF em C# com GroupDocs.Merger

Carregue o documento fonte, especifique as páginas necessárias e salve o resultado. A biblioteca abstrai todos os detalhes específicos de formato, de modo que o mesmo código funciona para PDF, DOCX, PPTX e muito mais.

Carregue seu arquivo fonte e chame o método `Extract` com os números de página desejados. O método `Extract` cria um novo documento contendo apenas as páginas especificadas. O método retorna um novo objeto `Document` que você pode salvar imediatamente. Um objeto `Document` representa a representação em memória do arquivo resultante.

### Etapa 1: criar uma instância de Merger
A classe `Merger` é o ponto de entrada para carregar e manipular documentos. Instancie a classe `Merger` passando o caminho do arquivo fonte. Esse objeto representa o documento com o qual você trabalhará.

### Etapa 2: especificar páginas a extrair
Forneça uma lista de índices de página (baseado em 1) ou uma string de intervalo como `"1-3,5"` para indicar à biblioteca quais páginas manter.

### Etapa 3: salvar o documento extraído
Chame `Save` no objeto `Document`, fornecendo o caminho de saída e o formato desejado (por exemplo, `SaveFormat.Pdf`). `SaveFormat` é uma enumeração que especifica o tipo de arquivo de saída, como PDF. A operação grava um novo arquivo contendo apenas as páginas selecionadas.

## Problemas comuns e soluções
- **As páginas estão deslocadas em uma unidade:** O GroupDocs.Merger usa numeração de páginas baseada em 1. Certifique‑se de que sua lista comece em 1, não em 0.  
- **Arquivos protegidos por senha:** Passe a senha para o construtor `Merger` ou use o objeto `LoadOptions`. `LoadOptions` fornece configurações que controlam como um documento é carregado, por exemplo, habilitando o cache de memória.  
- **Arquivos grandes causam timeouts:** Habilite streaming definindo `LoadOptions.UseMemoryCache = true` para manter o uso de memória baixo.

## Perguntas frequentes

**Q: Posso extrair páginas de um documento Word como PDF?**  
A: Sim – a mesma chamada `Extract` funciona para DOCX, e você pode salvar o resultado diretamente como PDF usando `SaveFormat.Pdf`.

**Q: É possível extrair páginas não consecutivas?**  
A: Absolutamente. Forneça uma lista separada por vírgulas como `"2,4,7"` ou um intervalo misto `"1-2,5,8-10"`.

**Q: A biblioteca suporta PDFs criptografados?**  
A: Sim. Forneça a senha ao abrir o documento; a API o descriptografará automaticamente.

**Q: Como o GroupDocs.Merger lida com imagens dentro de PDFs?**  
A: As imagens são preservadas exatamente como aparecem nas páginas selecionadas; não são necessárias etapas extras de conversão.

**Q: Quais versões do .NET são oficialmente suportadas?**  
A: .NET Framework 4.6+, .NET Core 3.1+, e .NET 5/6/7 são totalmente suportados.

## Tutoriais disponíveis

### [Extrair páginas específicas de documentos com GroupDocs.Merger para .NET](./extract-pages-groupdocs-merger-net/)
Aprenda a extrair páginas específicas de forma eficiente usando o GroupDocs.Merger para .NET. Ideal para gerenciar Word, PDF e muito mais em ambientes profissionais.

### [Como extrair páginas específicas de um documento usando GroupDocs.Merger para .NET em C#](./extract-pages-groupdocs-merger-dotnet-csharp/)
Aprenda a extrair páginas específicas de documentos usando o GroupDocs.Merger para .NET com este guia abrangente. Otimize suas tarefas de gerenciamento de documentos sem esforço.

## Recursos adicionais

- [Documentação do GroupDocs.Merger para .net](https://docs.groupdocs.com/merger/net/)
- [Referência da API do GroupDocs.Merger para .net](https://reference.groupdocs.com/merger/net/)
- [Download do GroupDocs.Merger para .net](https://releases.groupdocs.com/merger/net/)
- [Fórum do GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Suporte gratuito](https://forum.groupdocs.com/)
- [Licença temporária](https://purchase.groupdocs.com/temporary-license/)

---

**Última atualização:** 2026-08-31  
**Testado com:** GroupDocs.Merger 23.9 para .NET  
**Autor:** GroupDocs

## Tutoriais relacionados

- [Como mesclar páginas PDF específicas com GroupDocs.Merger para .NET: Um guia abrangente](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [Como mesclar páginas específicas de vários documentos usando GroupDocs.Merger para .NET](/merger/net/page-operations/groupdocs-merger-dotnet-specific-pages-merge/)
- [Rotacionar páginas PDF em .NET usando GroupDocs.Merger: Um guia passo a passo](/merger/net/page-operations/rotate-pdf-pages-groupdocs-merger-dotnet/)