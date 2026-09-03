---
date: '2026-08-20'
description: GroupDocs.Merger for .NET를 사용하여 북마크가 포함된 PDF를 병합하는 방법을 배우세요. setup, code
  examples, best practices를 포함하여 PDF 문서를 결합합니다.
keywords:
- merge pdfs with bookmarks
- merge pdf with bookmarks
- combine pdf documents c#
lastmod: '2026-08-20'
og_description: GroupDocs.Merger for .NET를 사용하여 북마크가 포함된 PDF를 병합하는 방법을 배우세요. navigation을
  보존하면서 PDF 문서를 결합하기 위해 step‑by‑step code를 따라하세요.
og_image_alt: Guide showing PDF merge with bookmarks in .NET using GroupDocs.Merger
og_title: GroupDocs.Merger for .NET를 사용하여 북마크가 포함된 PDF를 병합하는 방법
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
title: GroupDocs.Merger for .NET를 사용하여 북마크가 포함된 PDF를 병합하는 방법
type: docs
url: /ko/net/advanced-joining-options/merge-pdfs-bookmarks-groupdocs-merger-dotnet/
weight: 1
---

# GroupDocs.Merger for .NET를 사용하여 북마크가 포함된 PDF 병합 방법

여러 PDF 파일을 원본 북마크를 그대로 유지하면서 병합하면 수동으로 재구성하는 데 드는 시간을 크게 절약할 수 있습니다. 이 튜토리얼에서는 프로젝트 설정부터 완전한 프로덕션 수준 코드 샘플까지 **북마크가 포함된 PDF 병합** 방법을 GroupDocs.Merger for .NET을 사용해 배웁니다.

## 빠른 답변
- **북마크를 보존하면서 병합을 지원하는 라이브러리는?** GroupDocs.Merger for .NET.  
- **두 개 이상의 PDF를 한 번에 병합할 수 있나요?** 예 – 필요한 만큼 많은 소스 파일을 추가하면 됩니다.  
- **개발용 라이선스가 필요합니까?** 무료 체험판으로 테스트할 수 있으며, 프로덕션에서는 영구 라이선스가 필요합니다.  
- **.NET Core를 지원하나요?** 물론 – 라이브러리는 .NET Core, .NET 5/6 및 전체 .NET Framework와 함께 작동합니다.  
- **처리 가능한 최대 파일 크기는?** 문서당 최대 2 GB까지 전체 파일을 메모리로 로드하지 않고 처리할 수 있습니다.

## 북마크가 포함된 PDF 병합이란?
**북마크가 포함된 PDF 병합**은 여러 PDF 문서를 하나의 파일로 결합하면서 각 소스 문서의 북마크 계층 구조를 그대로 유지하는 것을 의미합니다. 결과 PDF는 원래의 탐색 구조를 보존하여 독자가 각 개별 파일에서 유래한 섹션으로 바로 이동할 수 있게 하며, 대형 보고서나 매뉴얼을 컴파일할 때 필수적입니다.

## 왜 북마크가 포함된 PDF를 병합해야 할까요?
PDF를 병합할 때 북마크를 보존하면 통합 문서 내 탐색이 개선되어 사용자가 전체 파일을 스크롤하지 않고도 특정 챕터나 섹션을 빠르게 찾을 수 있습니다. GroupDocs.Merger는 원래의 아웃라인 계층을 유지하고, 수동 재구성 작업을 줄이며, 최소 메모리 사용으로 2 GB까지의 대용량 파일을 지원해 엔터프라이즈 규모 워크플로에 이상적입니다.

## 사전 요구 사항
- **.NET Core SDK** (3.1 이상) 또는 **.NET Framework** (4.6.1 이상).  
- **Visual Studio 2022** 또는 .NET 개발을 지원하는 기타 IDE.  
- 기본 C# 지식 및 파일 I/O에 대한 이해.  

## GroupDocs.Merger for .NET 설정

### 설치
다음 명령 중 하나를 사용해 프로젝트에 라이브러리를 추가합니다.

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
- “GroupDocs.Merger”를 검색하고 최신 버전을 설치합니다.

### 라이선스 획득
- **무료 체험:** [GroupDocs Releases](https://releases.groupdocs.com/merger/net/) 페이지에서 다운로드합니다.  
- **임시 라이선스:** [GroupDocs Temporary License Page](https://purchase.groupdocs.com/temporary-license/)에서 발급받습니다.  
- **정식 라이선스:** [GroupDocs Purchase Page](https://purchase.groupdocs.com/buy)에서 구매합니다.

### 기본 초기화
`Merger` 클래스는 모든 병합 작업의 진입점입니다.  
```  
```csharp
using GroupDocs.Merger;
```  
```  
이 네임스페이스를 통해 PDF 조작 기능 전체에 접근할 수 있습니다.

## .NET에서 북마크가 포함된 PDF를 병합하는 방법

주요 PDF를 로드하고, 북마크 처리를 구성한 뒤, 추가 파일을 추가하고 결과를 저장합니다 – 몇 줄의 간결한 코드만으로 가능합니다.

**직접적인 답변 (40‑70단어):**  
첫 번째 PDF로 `Merger` 인스턴스를 생성하고 `PdfJoinOptions.UseBookmarks`를 활성화한 뒤, `Join`을 사용해 각 추가 PDF를 연결하고 `Save`로 결합 파일을 저장합니다. 이 방식은 모든 원본 북마크 계층을 보존하고 단일 패스로 실행돼 메모리 사용을 최소화합니다.

### 1단계: 디렉터리 경로 정의
코드가 병합하려는 PDF를 찾을 수 있도록 소스 및 출력 폴더를 설정합니다.  
```  
```csharp
   string documentDirectory = @"YOUR_DOCUMENT_DIRECTORY";
   string outputDirectory = @"YOUR_OUTPUT_DIRECTORY/";
   ```  
```  

### 2단계: 주요 PDF 로드
`Merger`는 다른 파일을 추가할 메인 문서를 나타냅니다.  
```  
```csharp
   using (var merger = new Merger(Path.Combine(documentDirectory, "SAMPLE_PDF.pdf")))
   {
       // 추가 파일을 병합하는 코드는 여기 들어갑니다.
   }
   ```  
```  

### 3단계: 북마크 보존 옵션 구성
`PdfJoinOptions`는 병합 동작을 제어하며, `UseBookmarks` 플래그가 엔진에 기존 북마크를 유지하도록 지시합니다.  
```  
```csharp
   var pdfJoinOptions = new PdfJoinOptions { UseBookmarks = true };
   ```  
```  

### 4단계: 추가 PDF 추가
각 추가 파일에 대해 `Join`을 호출합니다. 라이브러리는 자동으로 해당 파일들의 북마크 트리를 메인 문서 아웃라인 아래에 병합합니다.  
```  
```csharp
   merger.Join(Path.Combine(documentDirectory, "SAMPLE_PDF_BOOKMARKS.pdf"), pdfJoinOptions);
   ```  
```  

### 5단계: 병합된 PDF 저장
출력 경로와 형식을 지정하면 라이브러리가 모든 북마크 항목을 유지한 채 단일 PDF를 작성합니다.  
```  
```csharp
   string outputFile = Path.Combine(outputDirectory, "merged.pdf");
   merger.Save(outputFile);
   ```  
```  

## 일반적인 문제와 해결책
- **북마크가 누락됨:** `PdfJoinOptions`에서 `UseBookmarks = true`인지 확인합니다.  
- **경로 오류:** `Path.Combine`을 사용하고 병합 전에 파일 존재 여부를 확인합니다.  
- **대용량 파일로 메모리 급증:** PDF를 순차적으로 처리하고 저장 후 `Merger` 객체를 해제합니다.

## 실용적인 적용 사례
1. **재무 보고서 통합** – 분기별 섹션을 북마크로 즉시 접근 가능하게 유지합니다.  
2. **강의 자료 패키지** – 학생들을 위해 챕터 탐색이 보존된 강의 PDF를 병합합니다.  
3. **프로젝트 문서 번들** – 설계 사양, 테스트 계획, 릴리스 노트를 하나의 검색 가능한 파일로 결합합니다.

## 성능 고려 사항
- 20개 이상의 PDF를 병합할 경우 RAM 사용량을 낮게 유지하려면 파일을 하나씩 처리합니다.  
- 최신 .NET 런타임(e.g., .NET 6)을 사용하면 JIT 컴파일 및 가비지 컬렉션 효율이 최적화됩니다.  
- 500 MB를 초과하는 PDF의 경우 `MergerSettings`를 통해 스트리밍 모드를 활성화해 전체 문서를 메모리에 로드하지 않도록 합니다.

## 자주 묻는 질문

**Q: GroupDocs.Merger란?**  
A: GroupDocs.Merger는 .NET 라이브러리로, PDF 및 기타 문서 형식을 프로그래밍 방식으로 병합, 분할, 회전 및 조작할 수 있습니다.

**Q: 한 번에 두 개 이상의 PDF 파일을 병합할 수 있나요?**  
A: 예 – `Join`을 반복 호출하거나 파일 경로 컬렉션을 전달해 원하는 수만큼 PDF를 한 번에 병합할 수 있습니다.

**Q: 프로덕션 사용을 위한 라이선스는 어떻게 처리하나요?**  
A: GroupDocs 구매 페이지에서 영구 라이선스를 획득합니다; 체험 라이선스는 평가용으로만 30일 후 만료됩니다.

**Q: 병합된 PDF에 북마크가 표시되지 않는데, 왜인가요?**  
A: `PdfJoinOptions.UseBookmarks`가 `true`로 설정되어 있는지, 각 소스 PDF에 실제 북마크가 포함되어 있는지 확인합니다.

**Q: 라이브러리가 .NET Core 및 .NET Framework와 호환되나요?**  
A: 물론 – .NET Core 3.1+, .NET 5/6 및 전체 .NET Framework 4.6.1+을 지원합니다.

## 리소스
- [Documentation](https://docs.groupdocs.com/merger/net/)  
- [API Reference](https://reference.groupdocs.com/merger/net/)  
- [Download GroupDocs.Merger](https://releases.groupdocs.com/merger/net/)  
- [Purchase License](https://purchase.groupdocs.com/buy)  
- [Free Trial Version](https://releases.groupdocs.com/merger/net/)  
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)  
- [Support Forum](https://forum.groupdocs.com/c/merger/)  

---

**Last Updated:** 2026-08-20  
**Tested With:** GroupDocs.Merger 23.11 for .NET  
**Author:** GroupDocs

## 관련 튜토리얼

- [How to Merge Specific PDF Pages with GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/format-specific-merging/merge-pdf-pages-groupdocs-merger-dotnet/)
- [How to Easily Join Documents Using GroupDocs.Merger for .NET: A Comprehensive Guide](/merger/net/document-joining/groupdocs-merger-net-document-joining-guide/)
- [Add Attachments to PDFs Using GroupDocs.Merger for .NET: A Step-by-Step Guide](/merger/net/document-import/add-attachments-pdf-groupdocs-merger-dotnet-tutorial/)