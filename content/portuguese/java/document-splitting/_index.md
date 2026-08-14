---
date: 2026-05-22
description: Aprenda como criar arquivos PDF de página única e dividir PDFs usando
  GroupDocs.Merger para Java. Inclui guias passo a passo para split pdf java e mais.
keywords:
- create single page pdf
- docx to pdf java
- split pdf java
- pdf split by range
- split pdf odd even
schemas:
- author: GroupDocs
  dateModified: '2026-05-22'
  description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  headline: Create Single Page PDF with GroupDocs.Merger Java
  type: TechArticle
- description: Learn how to create single page PDF files and split PDFs using GroupDocs.Merger
    for Java. Includes step-by-step guides for split pdf java and more.
  name: Create Single Page PDF with GroupDocs.Merger Java
  steps:
  - name: Initialize the Merger
    text: The `Merger` class is GroupDocs.Merger's core component that loads a source
      document and provides split operations. Create an instance by passing the file
      path or an input stream.
  - name: Define the split criteria
    text: Choose the exact page number or range you need. For a single‑page extraction,
      you’ll specify a range like `1‑1`. When you need to **split pdf by range**,
      you can pass multiple ranges such as `1‑5, 6‑10`.
  - name: Execute the split
    text: Call the appropriate `split` method. For example, `merger.split(new int[]{1})`
      extracts the first page, while `merger.splitByRange(new int[][]{{1,5},{6,10}})`
      handles multiple ranges in one call.
  - name: Save the result
    text: Write each output to a file path or return it as a `java.io.InputStream`.
      This makes it easy to integrate with web APIs or store the result in cloud storage.
      > **Pro tip:** When working with large PDFs, call `merger.setOptimizeResources(true)`
      before splitting to reduce memory consumption.
  type: HowTo
- questions:
  - answer: Yes. Load the document with the password parameter, then perform any split
      operation as usual.
    question: Can I split a password‑protected PDF?
  - answer: Provide a page list containing only odd numbers (e.g., 1,3,5…) to the
      `split` method.
    question: How do I split only the odd pages of a PDF?
  - answer: Absolutely. After loading the DOCX, call `saveAsPdf` on each split segment.
    question: Is it possible to split a DOCX directly into PDFs?
  - answer: PDF, DOCX, PPTX, TXT, HTML, and many image formats (PNG, JPEG, etc.).
    question: What formats does GroupDocs.Merger support for splitting?
  - answer: No. A single GroupDocs.Merger license covers all supported formats.
    question: Do I need a separate license for each file type?
  type: FAQPage
title: Criar PDF de página única com GroupDocs.Merger Java
type: docs
url: /pt/java/document-splitting/
weight: 12
---

# Criar PDF de página única com GroupDocs.Merger Java

Se você precisa **criar PDF de página única** a partir de documentos maiores ou simplesmente dividir PDFs em partes mais manejáveis, você está no lugar certo. Este guia percorre os cenários de divisão mais comuns — arquivos de várias páginas, intervalos de páginas, páginas ímpares/par, divisão de DOCX e até divisões baseadas em texto — usando a poderosa biblioteca GroupDocs.Merger para Java. Ao final deste tutorial, você saberá exatamente como integrar essas técnicas em suas próprias aplicações, melhorar o desempenho no manuseio de documentos e manter sua base de código limpa e fácil de manter.

## Respostas rápidas
- **O que significa “criar PDF de página única”?** Significa extrair uma página de um documento fonte e salvá‑la como um arquivo PDF independente.  
- **Qual biblioteca realiza a tarefa?** GroupDocs.Merger for Java fornece uma API fluente para todas as operações de divisão.  
- **Preciso de uma licença?** Uma licença temporária funciona para desenvolvimento; uma licença completa é necessária para produção.  
- **Posso dividir PDFs em páginas ímpares e pares?** Sim — GroupDocs.Merger permite filtrar páginas por números ímpares/par.  
- **A divisão de DOCX é suportada?** Absolutamente; você pode dividir arquivos DOCX página por página ou por intervalos personalizados.  

## O que é “criar PDF de página única”?
Criar um PDF de página única envolve pegar um documento fonte de várias páginas (PDF, DOCX, PPTX, etc.) e extrair apenas uma página para seu próprio arquivo PDF. Isso é útil para gerar faturas, certificados ou imagens de pré‑visualização onde apenas uma página específica é necessária.

## Por que usar GroupDocs.Merger para Java?
GroupDocs.Merger para Java oferece uma API única e consistente que manipula muitos formatos de documento ao mesmo tempo em que oferece alto desempenho e baixo uso de memória. Ela simplifica o desenvolvimento ao abstrair o manuseio complexo de arquivos, permitindo que você se concentre na lógica de negócios em vez de detalhes de processamento de baixo nível.

- **API Unificada** – Funciona com PDF, DOCX, PPTX, imagens e muitos outros formatos.  
- **Alto desempenho** – Otimizado para arquivos grandes e operações em lote; pode processar documentos de até 2 GB sem carregar o arquivo inteiro na memória.  
- **Controle granular** – Divida por intervalo de páginas, páginas ímpares/par ou delimitadores personalizados.  
- **Amigável a streams** – A saída pode ser salva em um arquivo ou retornada como stream para serviços web.

## Pré-requisitos
- Java 8 ou superior.  
- GroupDocs.Merger para Java adicionado ao seu projeto (Maven/Gradle).  
- Um arquivo de licença GroupDocs válido (temporário ou completo).

## Como criar PDF de página única?
Criar um PDF de página única com GroupDocs.Merger envolve carregar o arquivo fonte, especificar a página ou intervalo exato, invocar a operação de divisão e, finalmente, persistir o resultado. Esse fluxo de trabalho garante que o documento original permaneça intacto enquanto a página extraída é salva como um arquivo PDF independente.

A classe `Merger` é o componente central que carrega documentos fonte e fornece funcionalidade de divisão.

### Etapa 1: Inicializar o Merger
A classe `Merger` é o componente central do GroupDocs.Merger que carrega um documento fonte e fornece operações de divisão. Crie uma instância passando o caminho do arquivo ou um stream de entrada.

### Etapa 2: Definir os critérios de divisão
Escolha o número exato da página ou intervalo que você precisa. Para uma extração de página única, você especificará um intervalo como `1‑1`. Quando precisar **dividir pdf por intervalo**, pode passar múltiplos intervalos como `1‑5, 6‑10`.

### Etapa 3: Executar a divisão
Chame o método `split` apropriado. Por exemplo, `merger.split(new int[]{1})` extrai a primeira página, enquanto `merger.splitByRange(new int[][]{{1,5},{6,10}})` trata de múltiplos intervalos em uma única chamada.

### Etapa 4: Salvar o resultado
Grave cada saída em um caminho de arquivo ou retorne-a como um `java.io.InputStream`. Isso facilita a integração com APIs web ou o armazenamento do resultado em nuvem.

> **Dica profissional:** Ao trabalhar com PDFs grandes, chame `merger.setOptimizeResources(true)` antes de dividir para reduzir o consumo de memória.

## Como dividir arquivos PDF java em várias páginas
A classe `Merger` fornece a API principal para carregar e manipular arquivos PDF. Para dividir um PDF em arquivos de página única separados, basta carregar o documento com a instância Merger e chamar o método split sem parâmetros. A biblioteca cria automaticamente um novo PDF para cada página, preservando o conteúdo e os metadados originais, o que é ideal para processamento em lote de faturas ou relatórios.

## Como dividir PDFs em páginas ímpares e pares
A classe `Merger` é o componente central que executa operações de divisão em documentos. Quando você precisa apenas de páginas ímpares ou pares de um PDF, forneça uma lista dos números de página desejados para a função split. O Merger gerará um novo documento contendo apenas essas páginas, permitindo criar rapidamente arquivos separados para conteúdo de páginas ímpares ou pares.

## Como dividir arquivos docx (como dividir docx)
A classe `Merger` também funciona com arquivos DOCX. Use `splitByPage` para gerar um DOCX (ou PDF) por página, ou combine com `saveAsPdf` se precisar de saída em PDF. Isso cobre o fluxo de trabalho de conversão **docx to pdf java** em uma única etapa.

## Como dividir documentos em arquivos de várias páginas
A classe `Merger` lida com paginação e criação de arquivos para operações de divisão. Se você preferir dividir um documento grande em blocos de tamanho fixo, especifique o número de páginas por arquivo de saída. O Merger iterará sobre a fonte, criando novos PDFs contendo a quantidade de páginas definida, o que simplifica arquivamento, distribuição e processamento paralelo de documentos extensos.

## Tutoriais disponíveis

### [Como dividir documentos em arquivos de várias páginas usando GroupDocs.Merger para Java](./split-documents-multi-page-files-java-groupdocs-merger/)
Learn how to efficiently split large documents into smaller, multi-page files using GroupDocs.Merger for Java. Optimize document management with ease.

### [Como dividir um arquivo de texto por intervalos de linhas usando GroupDocs.Merger para Java | Guia de divisão de documentos](./split-text-file-line-intervals-groupdocs-merger-java/)
Learn how to split text files into manageable sections using line intervals with GroupDocs.Merger for Java. A comprehensive guide for efficient document handling.

### [Divisão avançada de documentos por intervalo de páginas com GroupDocs.Merger para Java](./split-documents-page-range-groupdocs-merger-java/)
Learn how to split documents into specific page ranges using GroupDocs.Merger for Java. Streamline document management and apply filters like odd/even pages.

### [Divisão avançada de documentos com GroupDocs.Merger&#58; Um guia abrangente](./master-document-splitting-groupdocs-merger-java/)
Learn how to efficiently split documents into single pages using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

### [Divisão avançada de documentos Java com GroupDocs.Merger&#58; Divida páginas DOCX em arquivos e streams](./master-java-document-splitting-groupdocs-merger/)
Learn how to efficiently split DOCX documents into separate pages or streams using GroupDocs.Merger for Java. This guide covers setup, implementation, and practical applications.

## Recursos adicionais

- [Documentação do GroupDocs.Merger para Java](https://docs.groupdocs.com/merger/java/)
- [Referência da API do GroupDocs.Merger para Java](https://reference.groupdocs.com/merger/java/)
- [Baixar GroupDocs.Merger para Java](https://releases.groupdocs.com/merger/java/)
- [Fórum do GroupDocs.Merger](https://forum.groupdocs.com/c/merger)
- [Suporte gratuito](https://forum.groupdocs.com/)
- [Licença temporária](https://purchase.groupdocs.com/temporary-license/)

## Problemas comuns e soluções

| Problema | Solução |
|----------|---------|
| **Sobrecarga de memória em PDFs grandes** | Enable resource optimization: `merger.setOptimizeResources(true);` |
| **Números de página incorretos após a divisão** | Remember that page indexing starts at 1, not 0. |
| **Licença não encontrada** | Verify the path to your `GroupDocs.Merger.lic` file and ensure it’s included in the classpath. |
| **Divisão de DOCX resulta em páginas vazias** | Ensure the source DOCX has proper page breaks; otherwise, use `splitByParagraph` as a fallback. |

## Perguntas frequentes

**Q: Posso dividir um PDF protegido por senha?**  
A: Sim. Carregue o documento com o parâmetro de senha e, em seguida, execute qualquer operação de divisão normalmente.

**Q: Como dividir apenas as páginas ímpares de um PDF?**  
A: Forneça uma lista de páginas contendo apenas números ímpares (ex.: 1,3,5…) para o método `split`.

**Q: É possível dividir um DOCX diretamente em PDFs?**  
A: Absolutamente. Após carregar o DOCX, chame `saveAsPdf` em cada segmento dividido.

**Q: Quais formatos o GroupDocs.Merger suporta para divisão?**  
A: PDF, DOCX, PPTX, TXT, HTML e muitos formatos de imagem (PNG, JPEG, etc.).

**Q: Preciso de uma licença separada para cada tipo de arquivo?**  
A: Não. Uma única licença do GroupDocs.Merger cobre todos os formatos suportados.

---

**Última atualização:** 2026-05-22  
**Testado com:** GroupDocs.Merger 23.11 para Java  
**Autor:** GroupDocs

## Tutoriais relacionados

- [dividir pdf java: Divisão de documentos com GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Divisão avançada de documentos por intervalo de páginas com GroupDocs.Merger para Java](/merger/java/document-splitting/split-documents-page-range-groupdocs-merger-java/)
- [Mesclar PDFs de forma eficiente usando GroupDocs.Merger para Java: Um guia passo a passo](/merger/java/format-specific-merging/merge-pdfs-groupdocs-merger-java-tutorial/)