---
date: '2026-07-25'
description: Aprenda como dividir páginas de documentos Word usando GroupDocs.Merger
  para Java, com exemplos passo a passo para PDF, DOCX e PPTX, além de filtros de
  páginas ímpares/par.
keywords:
- split word document pages
- how to split pdf
- split pdf by range
- GroupDocs.Merger Java
- document page extraction
lastmod: '2026-07-25'
og_description: Aprenda como dividir páginas de documentos Word usando GroupDocs.Merger
  para Java, com exemplos passo a passo para PDF, DOCX e PPTX, além de filtros de
  páginas ímpares/par.
og_image_alt: Guide to split word document pages using GroupDocs.Merger for Java
og_title: Divida páginas de documentos Word com GroupDocs.Merger para Java
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  headline: Split Word Document Pages with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split word document pages using GroupDocs.Merger for Java,
    with step‑by‑step examples for PDF, DOCX, and PPTX, plus odd/even page filters.
  name: Split Word Document Pages with GroupDocs.Merger for Java
  steps:
  - name: Define Input and Output Paths
    text: 'Set the source file and the destination pattern for the split files:'
  - name: Configure Split Options (Range & Filter)
    text: 'The `SplitOptions` class tells the library which pages to extract and which
      filter to apply. `RangeMode` is an enumeration that specifies which pages to
      include, such as odd, even, or all pages. The `filePathOut` property defines
      the naming pattern, while `startPage` and `endPage` set the inclusive '
  - name: Perform the Split Operation
    text: 'Execute the split using the configured options:'
  type: HowTo
- questions:
  - answer: GroupDocs.Merger for Java is a robust library that enables merging, splitting,
      and reordering pages across many document formats, including PDF, DOCX, and
      PPTX.
    question: What is GroupDocs.Merger for Java?
  - answer: Yes, similar capabilities exist for .NET and C++.
    question: Can I use GroupDocs.Merger with other programming languages?
  - answer: '`MergerException` is the exception type thrown by GroupDocs.Merger when
      a processing error occurs. Wrap calls in `try‑catch` blocks and inspect `MergerException`
      for detailed error information.'
    question: How do I handle exceptions during document processing?
  - answer: Absolutely—set `RangeMode.AllPages` or omit the filter parameter to split
      by exact page numbers.
    question: Is it possible to split documents without filtering by odd/even pages?
  - answer: Java 8 or higher and a compatible IDE; no additional native dependencies
      are required.
    question: What are the system requirements for using GroupDocs.Merger?
  type: FAQPage
tags:
- split word document pages
- GroupDocs.Merger
- Java document processing
- PDF splitting
- page range extraction
title: Divida páginas de documentos Word com GroupDocs.Merger para Java
type: docs
url: /pt/java/document-splitting/split-documents-page-range-groupdocs-merger-java/
weight: 1
---

# Dividir Páginas de Documentos Word com GroupDocs.Merger para Java

Neste tutorial você aprenderá como **dividir páginas de documentos Word** — e outros formatos como PDF e PPTX — usando o GroupDocs.Merger para Java. Seja para extrair uma cláusula de contrato, gerar folhetos a partir de uma apresentação ou dividir um relatório extenso em partes manejáveis, a API permite especificar intervalos de páginas exatos, filtros ímpares/par, ou saídas de página única com apenas algumas linhas de código.

## Respostas Rápidas
- **O que significa “extrair páginas específicas”?** Significa criar novos documentos que contêm apenas as páginas que você seleciona do arquivo de origem.  
- **Quais formatos são suportados?** PDF, DOCX, PPTX e muitos outros formatos populares.  
- **Posso filtrar por páginas ímpares ou pares?** Sim, usando a opção `RangeMode` (por exemplo, `OddPages`).  
- **Preciso de uma licença?** Um teste gratuito funciona para avaliação; uma licença permanente é necessária para produção.  
- **É adequado para documentos grandes?** Sim — divida seções de documentos grandes para manter o uso de memória baixo.

## O que é extrair páginas específicas?
Extrair páginas específicas significa pegar um subconjunto selecionado de páginas de um documento original e criar um novo arquivo independente que contém apenas essas páginas. Essa técnica é valiosa para gerar relatórios focados, compartilhar cláusulas individuais de contrato ou distribuir slides específicos de uma apresentação sem expor o documento fonte completo.

## Por que usar o GroupDocs.Merger para Java para dividir PDFs e documentos Word?
Carregue apenas as páginas que você precisa e deixe o GroupDocs.Merger fazer o trabalho pesado. A biblioteca suporta **mais de 50 formatos de entrada e saída**, pode processar arquivos de até **2 GB** sem carregar o documento inteiro na memória e fornece uma API consistente para PDF, DOCX, PPTX e mais — assim você evita lidar com várias ferramentas.

## Pré-requisitos
- **GroupDocs.Merger para Java** (versão mais recente)  
- **JDK 8+**  
- Uma IDE como IntelliJ IDEA ou Eclipse  
- Maven ou Gradle para gerenciamento de dependências  

## Configurando o GroupDocs.Merger para Java
Adicione a biblioteca ao seu projeto usando a ferramenta de build de sua preferência.

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

**Download Direto**: Você também pode baixar a biblioteca diretamente de [lançamentos do GroupDocs.Merger para Java](https://releases.groupdocs.com/merger/java/).

### Aquisição de Licença
- **Teste Gratuito** – Teste todos os recursos sem limitações.  
- **Licença Temporária** – Período de avaliação estendido.  
- **Compra** – Licença permanente para produção.

**Inicialização Básica e Configuração**  
A classe `Merger` é o ponto de entrada para todas as operações de divisão. Ela representa um documento na memória e fornece métodos para manipular páginas. Para inicializar o GroupDocs.Merger, crie uma instância de `Merger` com o caminho do seu documento:  
```java
import com.groupdocs.merger.Merger;

String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
Merger merger = new Merger(filePath);
```

## Como extrair páginas específicas usando o GroupDocs.Merger para Java
Para extrair páginas específicas, carregue o documento fonte com uma instância de `Merger`, configure um objeto `SplitOptions` com as páginas inicial e final desejadas e, opcionalmente, defina `RangeMode` (por exemplo, `OddPages` ou `EvenPages`). Em seguida, chame `merger.split(options)`, que cria novos arquivos contendo apenas as páginas selecionadas.

### Resposta Direta
Crie uma instância de `Merger`, configure um objeto `SplitOptions` com `RangeMode.OddPages` e as páginas inicial/final desejadas, então chame `merger.split(options)`. Esse fluxo de um passo extrai apenas as páginas ímpares dentro do intervalo especificado e grava-as no padrão de saída que você fornecer.

### Etapa 1: Definir Caminhos de Entrada e Saída
Defina o arquivo fonte e o padrão de destino para os arquivos divididos:  
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/Sample_Docx_10_Pages.docx";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToSinglePagesByRangeWithFilter-Output.docx";
```

### Etapa 2: Configurar Opções de Divisão (Intervalo e Filtro)
A classe `SplitOptions` informa à biblioteca quais páginas extrair e qual filtro aplicar. `RangeMode` é uma enumeração que especifica quais páginas incluir, como ímpares, pares ou todas as páginas. A propriedade `filePathOut` define o padrão de nomenclatura, enquanto `startPage` e `endPage` definem o intervalo inclusivo. `RangeMode.OddPages` mantém apenas as páginas ímpares dentro desse intervalo, efetivamente **extraindo páginas específicas**.  
```java
import com.groupdocs.merger.domain.options.SplitOptions;
import com.groupdocs.merger.domain.options.RangeMode;

SplitOptions splitOptions = new SplitOptions(filePathOut, 3, 7, RangeMode.OddPages);
```

### Etapa 3: Executar a Operação de Divisão
Execute a divisão usando as opções configuradas:  
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

#### Dicas de Solução de Problemas
- Verifique se os caminhos dos arquivos estão corretos e acessíveis.  
- Certifique-se de que os números das páginas estejam dentro do total de páginas do documento; caso contrário, uma exceção será lançada.  

## Como dividir PDF em páginas individuais (dividir pdf em páginas individuais)
Para dividir um PDF em páginas individuais, abra o arquivo com uma instância de `Merger` e defina `RangeMode.AllPages` em um objeto `SplitOptions`. Especifique um padrão de nomenclatura de saída e, em seguida, invoque `merger.split(options)`. A biblioteca gerará um arquivo PDF separado para cada página, preservando o conteúdo e a formatação originais.

## Como dividir documentos grandes de forma eficiente (dividir documento grande)
Ao processar documentos muito grandes, divida-os em intervalos de páginas menores (por exemplo, 1‑100, 101‑200) para reduzir o consumo de memória. Crie `SplitOptions` separadas para cada intervalo, execute `merger.split(options)` sequencialmente e feche a instância `Merger` após cada lote. Essa abordagem mantém o uso de CPU e I/O gerenciável.

## Como dividir PDF em páginas ímpares (dividir pdf páginas ímpares)
Para extrair apenas as páginas ímpares de um PDF, configure um objeto `SplitOptions` com `RangeMode.OddPages`. Defina o padrão de saída desejado e, opcionalmente, especifique um intervalo de páginas se não precisar do documento inteiro. Chame `merger.split(options)` e a biblioteca produzirá arquivos contendo apenas as páginas ímpares.

## Aplicações Práticas
1. **Segmentação de Documentos** – Divida contratos em PDFs por cláusula para revisão mais fácil.  
2. **Gerenciamento de Relatórios** – Extraia um capítulo ou apêndice específico de um extenso relatório anual.  
3. **Preparação de Apresentações** – Isole slides individuais para reuniões específicas.  

Você também pode integrar essa lógica com bancos de dados ou sistemas de gerenciamento de conteúdo para automatizar pipelines de fluxo de trabalho.

## Considerações de Desempenho
- **Gerenciamento de Memória** – Chame `merger.close()` (ou confie em try‑with‑resources) após o processamento para liberar os manipuladores de arquivos.  
- **Intervalos Seletivos** – Solicite apenas as páginas que realmente precisa; isso minimiza o uso de I/O e CPU.  

## Conclusão
Agora você tem um método claro, passo a passo, para **dividir páginas de documentos Word** (e outros formatos suportados) usando o GroupDocs.Merger para Java. Essa capacidade simplifica seus fluxos de trabalho de documentos e permite entregar exatamente o conteúdo que seus usuários precisam.

### Próximos Passos
- Experimente diferentes valores de `RangeMode` (por exemplo, `EvenPages`, `AllPages`).  
- Combine a divisão com a funcionalidade de **mesclagem** para reordenar ou concatenar páginas extraídas.  
- Explore a API completa para documentos protegidos por senha, marcas d'água e muito mais.  

## Perguntas Frequentes
**Q: O que é o GroupDocs.Merger para Java?**  
A: O GroupDocs.Merger para Java é uma biblioteca robusta que permite mesclar, dividir e reordenar páginas em diversos formatos de documento, incluindo PDF, DOCX e PPTX.

**Q: Posso usar o GroupDocs.Merger com outras linguagens de programação?**  
A: Sim, capacidades semelhantes existem para .NET e C++.

**Q: Como lidar com exceções durante o processamento de documentos?**  
A: `MergerException` é o tipo de exceção lançada pelo GroupDocs.Merger quando ocorre um erro de processamento. Envolva as chamadas em blocos `try‑catch` e inspecione `MergerException` para obter informações detalhadas sobre o erro.

**Q: É possível dividir documentos sem filtrar por páginas ímpares/par?**  
A: Absolutamente — defina `RangeMode.AllPages` ou omita o parâmetro de filtro para dividir por números de página exatos.

**Q: Quais são os requisitos de sistema para usar o GroupDocs.Merger?**  
A: Java 8 ou superior e uma IDE compatível; não são necessárias dependências nativas adicionais.

## Recursos
- [Documentação do GroupDocs.Merger](https://docs.groupdocs.com/merger/java/)
- [Referência da API](https://reference.groupdocs.com/merger/java/)
- [Baixar a Biblioteca](https://releases.groupdocs.com/merger/java/)
- [Comprar Licença](https://purchase.groupdocs.com/buy)
- [Teste Gratuito e Licença Temporária](https://releases.groupdocs.com/merger/java/)
- [Fórum de Suporte](https://forum.groupdocs.com/c/merger/)

---

**Última Atualização:** 2026-07-25  
**Testado com:** versão mais recente do GroupDocs.Merger (Java)  
**Autor:** GroupDocs

## Tutoriais Relacionados
- [Remover Páginas de Documentos Word de Forma Eficiente Usando o GroupDocs.Merger para Java](/merger/java/page-operations/remove-pages-groupdocs-merger-java-word-documents/)
- [Gerenciamento Mestre de Documentos - Mesclar Documentos Word com GroupDocs.Merger para Java](/merger/java/document-joining/groupdocs-merger-java-word-document-management/)
- [Como Dividir Documentos em Arquivos Multi‑Página Usando o GroupDocs.Merger para Java](/merger/java/document-splitting/split-documents-multi-page-files-java-groupdocs-merger/)