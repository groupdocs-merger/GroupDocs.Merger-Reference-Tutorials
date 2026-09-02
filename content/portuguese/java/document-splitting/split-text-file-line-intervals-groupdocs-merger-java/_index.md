---
date: '2026-07-25'
description: Aprenda a dividir um arquivo por linhas usando GroupDocs.Merger for Java
  – um guia passo a passo para divisão eficiente de documentos em projetos Java.
keywords:
- split file by lines
- split large text file
- split file into parts
- split text file java
- java document splitting
lastmod: '2026-07-25'
og_description: Divida o arquivo por linhas usando GroupDocs.Merger for Java. Este
  guia mostra como dividir rapidamente arquivos de texto grandes em partes, com exemplos
  de código e dicas de boas práticas.
og_image_alt: 'Developer guide: split file by lines in Java using GroupDocs.Merger'
og_title: Divida o arquivo por linhas com GroupDocs.Merger for Java – Rápido e Fácil
schemas:
- author: GroupDocs
  dateModified: '2026-07-25'
  description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  headline: How to Split File by Lines with GroupDocs.Merger for Java
  type: TechArticle
- description: Learn how to split file by lines using GroupDocs.Merger for Java –
    a step‑by‑step guide for efficient document splitting in Java projects.
  name: How to Split File by Lines with GroupDocs.Merger for Java
  steps:
  - name: Define Source and Output Paths
    text: First, tell the library where your original file lives and where the split
      fragments should be written.
  - name: Configure the Split Options
    text: 'Create a `TextSplitOptions` instance that describes the line intervals
      you want. The `new int[] { 3, 6 }` array tells the API to cut after line 3 and
      line 6, producing two parts: lines 1‑3 and lines 4‑6. **Definition:** `TextSplitOptions`
      is a configuration object that holds the line‑interval array '
  - name: Initialise the Merger and Execute the Split
    text: Finally, instantiate `Merger` with the source file and call `split()` with
      the options you just built. **Definition:** `Merger` is the core class in GroupDocs.Merger
      that orchestrates document manipulation operations such as splitting, merging,
      and extracting pages. When the `split()` call finishes,
  type: HowTo
- questions:
  - answer: Currently, GroupDocs.Merger for Java focuses on line intervals. However,
      you can preprocess your text to match the desired character count per line before
      using this feature.
    question: Can I split files based on character count instead of line numbers?
  - answer: There is no hard limit in the library; performance may degrade if you
      request thousands of tiny splits because each split incurs I/O overhead.
    question: Is there a limit to how many intervals I can specify for splitting?
  - answer: Wrap the splitting logic in a try‑catch block and log `MergerException`
      details. The API provides clear messages that pinpoint the failure point.
    question: How do I handle errors during file splitting?
  - answer: Yes, because CSV and TSV are plain‑text files, the same line‑interval
      logic applies. Treat them as `.txt` files when calling the API.
    question: Does the library support other text‑based formats such as CSV or TSV?
  - answer: Absolutely. Iterate over `Files.list(Paths.get("folder"))`, apply the
      same `TextSplitOptions` to each file, and collect the generated parts.
    question: Can I automate splitting for multiple files in a folder?
  type: FAQPage
tags:
- split file by lines
- GroupDocs.Merger
- Java document processing
- text file splitting
- java tutorial
title: Como dividir um arquivo por linhas com GroupDocs.Merger for Java
type: docs
url: /pt/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Como Dividir Arquivo por Linhas com GroupDocs.Merger para Java

Se você precisa **dividir arquivo por linhas** — por exemplo, para dividir um enorme arquivo de log em pedaços menores, alimentar lotes de dados em um pipeline ou transformar um relatório longo em arquivos de capítulos separados — este tutorial mostra exatamente como fazer isso com GroupDocs.Merger para Java. Você verá por que a biblioteca economiza tempo, obterá uma implementação pronta para uso e aprenderá dicas práticas que mantêm sua aplicação rápida e confiável.

## Respostas Rápidas
- **O que significa “split file by lines”?** Ele cria arquivos de texto separados que cada um contém um intervalo definido de números de linha do documento original.  
- **Qual biblioteca realiza a divisão?** GroupDocs.Merger para Java fornece uma API simples para divisão por intervalos de linhas.  
- **Preciso de licença?** Um teste gratuito funciona para testes; uma licença permanente é necessária para uso em produção.  
- **Posso dividir por contagem de caracteres em vez disso?** Não diretamente — use uma etapa de pré‑processamento para remodelar o arquivo antes de dividir.  
- **Qual versão do Java é suportada?** Qualquer runtime Java 8+ é compatível.

## O que é “split file by lines”?
**Split file by lines** significa pegar um único documento de texto e dividi-lo em vários arquivos, cada um contendo um intervalo específico de linhas consecutivas (por exemplo, linhas 1‑3, 4‑6, etc.). Essa abordagem é ideal quando você deseja processar dados em paralelo, reduzir a pressão de memória ou simplesmente tornar arquivos longos mais fáceis de navegar.

## Por que Usar GroupDocs.Merger para Java?
GroupDocs.Merger abstrai o I/O de arquivos de baixo nível, permitindo que você se concentre na lógica de negócios. Ele manipula eficientemente arquivos de até 2 GB sem carregar todo o documento na memória, suporta **70+** formatos de entrada e saída, e fornece uma API fluente que se integra perfeitamente com builds Maven ou Gradle. Usar esta biblioteca reduz o tempo de desenvolvimento em até **80 %** comparado com loops de I/O feitos manualmente.

## Pré-requisitos
- **Java Development Kit (JDK) 8 ou superior** – certifique-se de que `java` e `javac` estejam no seu PATH.  
- **GroupDocs.Merger para Java** – adicione a biblioteca via Maven, Gradle ou download direto.  
- **Conhecimento básico de Java** – você deve estar confortável com classes, métodos e tratamento de exceções.

## Configurando GroupDocs.Merger para Java
Adicione a biblioteca ao seu projeto usando um dos métodos abaixo.

**Maven** – cole esta dependência no seu `pom.xml`:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle** – inclua a linha a seguir em `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Download Direto** – você também pode obter o JAR na página oficial de lançamentos: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Aquisição de Licença
Comece com um teste gratuito para explorar a API. Para cargas de trabalho de produção, obtenha uma licença temporária ou completa no portal da GroupDocs.

## Como Dividir Arquivo de Texto por Linhas (Implementação Java)

A seguir está um guia conciso, passo a passo. Cada etapa é explicada em linguagem simples antes do placeholder que indica onde o código real está, para que você saiba exatamente o que está acontecendo.

### Etapa 1: Definir Caminhos de Origem e Saída
Primeiro, informe à biblioteca onde seu arquivo original está e onde os fragmentos divididos devem ser gravados.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Etapa 2: Configurar as Opções de Divisão
Crie uma instância de `TextSplitOptions` que descreve os intervalos de linhas que você deseja. O array `new int[] { 3, 6 }` indica à API cortar após a linha 3 e a linha 6, produzindo duas partes: linhas 1‑3 e linhas 4‑6.  
**Definição:** `TextSplitOptions` é um objeto de configuração que contém o array de intervalos de linhas e regras opcionais de nomeação de saída.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Etapa 3: Inicializar o Merger e Executar a Divisão
Finalmente, instancie `Merger` com o arquivo de origem e chame `split()` com as opções que você acabou de criar.  
**Definição:** `Merger` é a classe central no GroupDocs.Merger que orquestra operações de manipulação de documentos, como divisão, mesclagem e extração de páginas.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

Quando a chamada `split()` terminar, você encontrará dois novos arquivos em `YOUR_OUTPUT_DIRECTORY`, cada um contendo os intervalos de linhas especificados.

## Aplicações Práticas (Por que Isso Importa)
1. **Pipelines de Processamento de Dados** – Divida arquivos de log massivos em pedaços menores para análise paralela, reduzindo drasticamente o tempo total de processamento.  
2. **Gerenciamento de Documentos** – Transforme um único relatório em arquivos por capítulo, facilitando a distribuição para diferentes equipes.  
3. **Segmentação de Conteúdo** – Prepare seções de um artigo extenso para plataformas de publicação específicas, melhorando SEO e legibilidade.

## Dicas de Performance
- **Otimizar I/O** – Prefira `Files.newBufferedReader` ao lidar com arquivos muito grandes para manter o uso de memória baixo.  
- **Fechar Recursos** – Embora o GroupDocs.Merger trate da maior parte da limpeza, fechar explicitamente quaisquer streams personalizados evita vazamentos.  
- **Monitorar Memória** – Dividir arquivos de tamanho gigabyte pode ser intensivo em memória; aloque heap suficiente (`-Xmx2g` ou superior) se necessário.  
- **Processamento em Lote** – Ao dividir muitos arquivos, reutilize uma única instância de `Merger` para reduzir a sobrecarga de criação de objetos.

## Problemas Comuns e Soluções
| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| `OutOfMemoryError` | Arquivo fonte grande excede o heap. | Aumente o heap da JVM ou divida usando intervalos menores. |
| `FileNotFoundException` | Caminho incorreto ou permissões ausentes. | Verifique se `filePath` e `filePathOut` são absolutos e graváveis. |
| Arquivos de saída vazios | O array de intervalos não cobre todo o documento. | Certifique-se de que o último intervalo termine no ou além da contagem total de linhas. |

## Perguntas Frequentes

**Q: Posso dividir arquivos com base na contagem de caracteres em vez de números de linha?**  
A: Atualmente, o GroupDocs.Merger para Java foca em intervalos de linhas. No entanto, você pode pré-processar seu texto para corresponder à contagem de caracteres desejada por linha antes de usar este recurso.

**Q: Existe um limite para quantos intervalos eu posso especificar para a divisão?**  
A: Não há um limite rígido na biblioteca; o desempenho pode degradar se você solicitar milhares de divisões pequenas, pois cada divisão gera sobrecarga de I/O.

**Q: Como lidar com erros durante a divisão de arquivos?**  
A: Envolva a lógica de divisão em um bloco try‑catch e registre os detalhes de `MergerException`. A API fornece mensagens claras que apontam o ponto de falha.

**Q: A biblioteca suporta outros formatos baseados em texto, como CSV ou TSV?**  
A: Sim, porque CSV e TSV são arquivos de texto simples, a mesma lógica de intervalo de linhas se aplica. Trate-os como arquivos `.txt` ao chamar a API.

**Q: Posso automatizar a divisão para vários arquivos em uma pasta?**  
A: Absolutamente. Itere sobre `Files.list(Paths.get("folder"))`, aplique o mesmo `TextSplitOptions` a cada arquivo e colete as partes geradas.

## Recursos Adicionais
- [Lançamentos do GroupDocs.Merger para Java](https://releases.groupdocs.com/merger/java/)
- [Documentação do GroupDocs.Merger para Java](https://docs.groupdocs.com/merger/java/)
- [Referência da API GroupDocs](https://reference.groupdocs.com/merger/java/)
- [Últimos Lançamentos](https://releases.groupdocs.com/merger/java/)
- [Comprar GroupDocs](https://purchase.groupdocs.com/buy)
- [Teste Gratuito do GroupDocs](https://releases.groupdocs.com/merger/java/)
- [Obter Licença Temporária](https://purchase.groupdocs.com/temporary-license/)
- [Suporte GroupDocs](https://forum.groupdocs.com/c/merger)

---

**Última Atualização:** 2026-07-25  
**Testado Com:** GroupDocs.Merger 23.12 para Java  
**Autor:** GroupDocs

## Tutoriais Relacionados

- [Como Dividir um Arquivo de Texto em Documentos de Linhas Separadas Usando GroupDocs.Merger para Java](/merger/java/text-operations/split-text-file-lines-groupdocs-merger-java/)
- [split pdf java: Divisão de Documentos com GroupDocs.Merger](/merger/java/document-splitting/master-document-splitting-groupdocs-merger-java/)
- [Carregar Documento Local Java Usando GroupDocs.Merger – Guia](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)