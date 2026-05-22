---
date: '2026-02-06'
description: Aprenda como dividir um arquivo de texto por linhas usando o GroupDocs.Merger
  para Java. Um guia passo a passo para divisão eficiente de documentos em projetos
  Java.
keywords:
- split text file line intervals Java
- document splitting GroupDocs.Merger
- Java document manipulation
title: Como dividir um arquivo por linhas com GroupDocs.Merger para Java
type: docs
url: /pt/java/document-splitting/split-text-file-line-intervals-groupdocs-merger-java/
weight: 1
---

# Como dividir um arquivo por linhas usando GroupDocs.Merger para Java

Dividir um grande arquivo de texto em partes menores e mais manejáveis **por linhas** é uma necessidade comum quando você ‑ por exemplo ‑ processa logs, importa dados em lote ou reorganiza relatórios extensos. Neste tutorial você aprenderá exatamente como **dividir um arquivo por linhas** com GroupDocs.Merger para Java, verá por que essa abordagem economiza tempo e obterá um exemplo de código pronto‑para‑executar.

## Respostas rápidas
- **O que significa “split file by lines”?** Ele cria arquivos de texto separados que cada um contém um intervalo definido de números de linha do documento original.  
- **Qual biblioteca realiza a divisão?** GroupDocs.Merger para Java fornece uma API simples para divisão por intervalos de linhas.  
- **Preciso de uma licença?** Um teste gratuito funciona para testes; uma licença permanente é necessária para uso em produção.  
- **Posso dividir por contagem de caracteres em vez disso?** Não diretamente—use uma etapa de pré‑processamento para remodelar o arquivo antes da divisão.  
- **Qual versão do Java é suportada?** Qualquer runtime Java 8+ é compatível.

## O que é “split file by lines”?
Dividir um arquivo por linhas significa pegar um único documento de texto e quebrá‑lo em vários arquivos, cada um contendo um intervalo específico de linhas consecutivas (por exemplo, linhas 1‑3, 4‑6, etc.). Essa técnica é ideal para processamento em lote, análise paralela ou simplesmente melhorar a legibilidade.

## Por que usar GroupDocs.Merger para Java?
GroupDocs.Merger abstrai o trabalho de I/O de arquivos de baixo nível, permitindo que você se concentre na lógica de negócios. Ele lida com arquivos grandes de forma eficiente, suporta muitos formatos de documento e oferece uma API limpa e fluente que se integra bem com builds Maven ou Gradle.

## Pré‑requisitos
- **Java Development Kit (JDK) 8 ou superior** – certifique‑se de que `java` e `javac` estejam no seu PATH.  
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

**Gradle** – inclua a seguinte linha em `build.gradle`:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Download direto** – você também pode obter o JAR na página oficial de lançamentos: [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/).

### Aquisição de Licença
Comece com um teste gratuito para explorar a API. Para cargas de trabalho de produção, obtenha uma licença temporária ou completa no portal da GroupDocs.

## Como dividir um arquivo de texto por linhas (Implementação Java)

A seguir está um guia conciso, passo a passo. Cada etapa é explicada em linguagem simples antes do bloco de código, para que você saiba exatamente o que está acontecendo.

### Etapa 1: Definir caminhos de origem e saída
Primeiro, informe à biblioteca onde seu arquivo original está localizado e onde os fragmentos divididos devem ser gravados.
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/sample.txt";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/SplitToLineRanges-" + Paths.get(filePath).getFileName().toString();
```

### Etapa 2: Configurar as opções de divisão
Crie uma instância `TextSplitOptions` que descreva os intervalos de linhas que você deseja. O array `new int[] { 3, 6 }` indica à API para cortar após a linha 3 e a linha 6, produzindo duas partes: linhas 1‑3 e linhas 4‑6.
```java
TextSplitOptions splitOptions = new TextSplitOptions(filePathOut, TextSplitMode.Interval, new int[] { 3, 6 });
```

### Etapa 3: Inicializar o Merger e executar a divisão
Finalmente, instancie `Merger` com o arquivo de origem e chame `split()` com as opções que você acabou de criar.
```java
Merger merger = new Merger(filePath);
merger.split(splitOptions);
```

É isso! Após a chamada ser concluída, você encontrará dois novos arquivos em `YOUR_OUTPUT_DIRECTORY`, cada um contendo os intervalos de linhas especificados.

## Aplicações práticas (Por que isso importa)
1. **Pipelines de processamento de dados** – Divida arquivos de log massivos em blocos menores para análise paralela.  
2. **Gerenciamento de documentos** – Transforme um único relatório em arquivos por capítulo para distribuição mais fácil.  
3. **Segmentação de conteúdo** – Prepare seções de um artigo extenso para plataformas de publicação direcionadas.

## Dicas de desempenho
- **I/O em fluxo** – Prefira `Files.newBufferedReader` ao lidar com arquivos muito grandes para manter o uso de memória baixo.  
- **Fechar recursos** – Embora o GroupDocs.Merger cuide da maior parte da limpeza, fechar explicitamente quaisquer streams personalizados evita vazamentos.  
- **Monitorar memória** – Dividir arquivos de tamanho gigabyte pode ser intensivo em memória; aloque heap suficiente (`-Xmx2g` ou superior) se necessário.

## Problemas comuns e soluções

| Problema | Por que acontece | Correção |
|----------|------------------|----------|
| `OutOfMemoryError` | Arquivo de origem grande excede o heap. | Aumente o heap da JVM ou divida usando intervalos menores. |
| `FileNotFoundException` | Caminho incorreto ou permissões ausentes. | Verifique se `filePath` e `filePathOut` são absolutos e graváveis. |
| Arquivos de saída vazios | O array de intervalos não cobre todo o documento. | Garanta que o último intervalo termine no ou além da contagem total de linhas. |

## Seção de Perguntas Frequentes

**Q: Posso dividir arquivos com base na contagem de caracteres em vez de números de linha?**  
A: Atualmente, o GroupDocs.Merger para Java foca em intervalos de linhas. No entanto, você pode pré‑processar seu texto para corresponder à contagem desejada de caracteres por linha antes de usar esse recurso.

**Q: Existe um limite para quantos intervalos eu posso especificar para a divisão?**  
A: Não há um limite específico na própria biblioteca; porém, o desempenho pode degradar com um número excessivo de divisões devido ao aumento dos requisitos de processamento.

**Q: Como lidar com erros durante a divisão de arquivos?**  
A: Implemente blocos try‑catch ao redor do seu código para capturar e gerenciar exceções de forma eficaz. O GroupDocs.Merger fornece mensagens de erro detalhadas que podem ajudar a solucionar problemas.

**Q: A biblioteca suporta outros formatos baseados em texto, como CSV ou TSV?**  
A: Sim, porque CSV e TSV são arquivos de texto simples, a mesma lógica de intervalo de linhas se aplica. Basta tratá‑los como arquivos `.txt` na API.

**Q: Posso automatizar a divisão para múltiplos arquivos em uma pasta?**  
A: Absolutamente. Envolva a lógica acima em um loop que itere sobre `Files.list(Paths.get("folder"))` e aplique o mesmo `TextSplitOptions` a cada arquivo.

## Recursos
- **Documentação:** [GroupDocs.Merger for Java Documentation](https://docs.groupdocs.com/merger/java/)  
- **Referência da API:** [GroupDocs API Reference](https://reference.groupdocs.com/merger/java/)  
- **Download:** [Latest Releases](https://releases.groupdocs.com/merger/java/)  
- **Compra e Licenciamento:** [Buy GroupDocs](https://purchase.groupdocs.com/buy)  
- **Teste gratuito:** [GroupDocs Free Trial](https://releases.groupdocs.com/merger/java/)  
- **Licença temporária:** [Obtain Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- **Fórum de suporte:** [GroupDocs Support](https://forum.groupdocs.com/c/merger)

---

**Última atualização:** 2026-02-06  
**Testado com:** GroupDocs.Merger 23.12 for Java  
**Autor:** GroupDocs