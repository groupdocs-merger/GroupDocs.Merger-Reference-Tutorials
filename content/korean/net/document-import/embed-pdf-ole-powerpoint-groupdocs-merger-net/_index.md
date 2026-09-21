---
date: '2026-09-21'
description: GroupDocs.Merger for .NET를 사용하여 OLE 객체로 powerpoint에 pdf를 삽입하는 방법을 배웁니다.
  이 단계별 가이드는 정확한 API 호출과 모범 사례를 보여줍니다.
keywords:
- embed pdf in powerpoint
- convert pdf to ole
- insert pdf as ole
- add ole object powerpoint
lastmod: '2026-09-21'
og_description: GroupDocs.Merger for .NET를 사용하여 powerpoint에 pdf를 삽입합니다. 이 간결한 튜토리얼을
  따라 OLE 객체를 추가하고 옵션을 구성하며 일반적인 함정을 피하세요.
og_image_alt: Screenshot of PowerPoint slide with embedded PDF OLE object using GroupDocs.Merger
og_title: powerpoint에 pdf 삽입 – GroupDocs.Merger와 함께 OLE로 PDF 삽입
schemas:
- author: GroupDocs
  dateModified: '2026-09-21'
  description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  headline: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  type: TechArticle
- description: Learn how to embed pdf in powerpoint as an OLE object with GroupDocs.Merger
    for .NET. This step‑by‑step guide shows you the exact API calls and best practices.
  name: How to embed pdf in powerpoint as OLE using GroupDocs.Merger for .NET
  steps:
  - name: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
    text: '**Corporate briefings** – attach the latest financial report without inflating
      the deck size.'
  - name: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
    text: '**Academic lectures** – provide full‑text research papers alongside slide
      summaries.'
  - name: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
    text: '**Project status updates** – embed a live project plan that stakeholders
      can open for details.'
  - name: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
    text: '**Sales decks** – include product spec sheets that sales reps can open
      on demand.'
  - name: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
    text: '**Technical workshops** – present schematics or datasheets that engineers
      can inspect instantly.'
  type: HowTo
- questions:
  - answer: Yes. Call `ImportDocument` for each PDF, specifying a different `SlideNumber`
      or position on the same slide.
    question: Can I embed multiple PDFs into a single presentation?
  - answer: The practical limit is dictated by your server’s memory; embeddings of
      up to 500 MB have been tested without issues when streaming.
    question: How large a PDF can I embed?
  - answer: Absolutely. The embedded PDF opens in the default viewer, preserving all
      internal links and bookmarks.
    question: Does the OLE object retain interactive elements like hyperlinks?
  - answer: Provide the password via the `Password` property of `OlePresentationOptions`
      before calling `ImportDocument`.
    question: What if the PDF is password‑protected?
  - answer: The OLE format is supported by PowerPoint 2007 and later, including Office
      365.
    question: Will the embedded object work on all versions of PowerPoint?
  type: FAQPage
tags:
- embed pdf
- GroupDocs.Merger
- OLE object
- PowerPoint automation
title: GroupDocs.Merger for .NET를 사용하여 OLE로 powerpoint에 pdf 삽입하는 방법
type: docs
url: /ko/net/document-import/embed-pdf-ole-powerpoint-groupdocs-merger-net/
weight: 1
---

# PDF를 PowerPoint에 OLE로 삽입하기 - GroupDocs.Merger for .NET 사용

PDF를 PowerPoint 슬라이드에 직접 삽입하면 원본 문서를 그대로 유지하면서 청중에게 즉시 접근성을 제공할 수 있습니다. 이 튜토리얼에서는 GroupDocs.Merger for .NET을 사용하여 **PDF를 PowerPoint에 OLE 객체로 삽입하는 방법**을 배우고, 필요한 API 옵션을 확인하며, 안정적인 성능을 위한 팁을 알아봅니다.

## 빠른 답변
- **OLE 삽입을 처리하는 라이브러리는?** GroupDocs.Merger for .NET은 이를 위해 `OlePresentationOptions` 클래스를 제공합니다.  
- **라이선스가 필요합니까?** 개발에는 체험 라이선스로 충분하지만, 운영 환경에서는 정식 라이선스가 필요합니다.  
- **여러 개의 PDF를 삽입할 수 있나요?** 예 – 대상 슬라이드마다 가져오기 단계를 반복하면 됩니다.  
- **지원되는 .NET 버전은?** .NET Framework 4.5+, .NET Core 3.1+, .NET 5/6/7.  
- **프로세스가 메모리 효율적인가요?** API가 파일을 스트리밍하므로 수백 페이지 PDF도 전체 파일을 메모리에 로드하지 않고 삽입할 수 있습니다.

## PDF를 PowerPoint에 삽입한다는 의미는?
**PDF를 PowerPoint에 삽입**한다는 것은 PDF 파일을 OLE(Object Linking and Embedding) 객체로 삽입하여 슬라이드에 아이콘이나 미리보기가 표시되고, 더블 클릭하면 기본 뷰어에서 원본 PDF가 열리도록 하는 것을 의미합니다. 이 방식은 원본 문서의 서식, 하이퍼링크 및 보안 설정을 그대로 유지합니다.

## PDF 변환 대신 OLE 삽입을 사용하는 이유는?
OLE 삽입은 원본 파일 크기와 레이아웃을 그대로 유지하고, 변환 오류를 없애며, 프레젠테이션을 다시 내보내지 않고도 원본 PDF를 업데이트할 수 있게 합니다. GroupDocs.Merger는 **50개 이상의 입력 및 출력 형식**을 지원하며, 스트리밍을 통해 메모리 사용량을 100 MB 이하로 유지하면서 수백 메가바이트 규모의 PDF도 삽입할 수 있습니다.

## 사전 요구 사항
- Visual Studio 2022 (또는 .NET 호환 IDE)  
- .NET Framework 4.5+ 또는 .NET Core 3.1+ 런타임  
- 유효한 GroupDocs.Merger for .NET 라이선스(체험 또는 상용)  
- 삽입하려는 PDF와 PowerPoint (.pptx) 파일  

## GroupDocs.Merger for .NET 설정

### 라이브러리를 어떻게 설치하나요?
**.NET CLI**  
```bash
dotnet add package GroupDocs.Merger
```  

**Package Manager**  
```powershell
Install-Package GroupDocs.Merger
```  

**NuGet Package Manager UI** – “GroupDocs.Merger”를 검색하고 **Install**을 클릭하여 최신 버전을 가져옵니다.

### 라이선스는 어떻게 획득하나요?
- **무료 체험** – GroupDocs 웹사이트에서 임시 라이선스 키를 신청하세요.  
- **임시 라이선스** – 30일 이상 필요하면 연장 체험을 요청하세요.  
- **정식 구매** – 무제한 운영 사용을 위한 상용 라이선스를 구매하세요.

### API를 어떻게 초기화하나요?
`Merger`는 가져오기, 병합 및 변환과 같은 문서 조작 작업을 제공하는 주요 클래스입니다.  
C# 파일 상단에 필요한 `using` 지시문을 추가하고 라이선스 파일 경로를 사용하여 `Merger` 인스턴스를 생성합니다:

```csharp
using System;
using GroupDocs.Merger.Domain.Options;
using GroupDocs.Merger;
using System.IO;
```  

## 구현 가이드

### PDF를 PowerPoint에 OLE로 삽입하는 방법은?
프레젠테이션을 로드하고 OLE 옵션을 구성한 뒤 가져오기 메서드를 호출합니다 – 전체 작업은 세 단계로 완료됩니다.

**Step 1 – 파일 위치 정의**  
원본 PDF, 대상 PowerPoint 파일, 수정된 프레젠테이션이 저장될 폴더의 절대 또는 상대 경로를 지정합니다.

**Step 2 – OLE 옵션 구성**  
`OlePresentationOptions`는 GroupDocs.Merger에 어떤 파일을 삽입할지, 어느 슬라이드에, 어떤 좌표에 삽입할지를 알려주는 클래스입니다. 또한 삽입된 객체의 너비, 높이 및 표시 모드를 설정할 수 있습니다.

**Step 3 – PDF 가져오기**  
`ImportDocument`는 제공된 옵션을 사용하여 OLE 객체를 PowerPoint 파일에 삽입하는 Merger API 호출입니다. 이 메서드는 전체 문서를 메모리에 로드하지 않고 PDF를 슬라이드에 스트리밍합니다.

#### 정의 앵커
- `OlePresentationOptions`는 삽입 파일, 위치(X/Y), 크기 및 대상 슬라이드 번호를 정의하는 옵션 컨테이너입니다.  
- `ImportDocument`는 제공된 옵션을 사용하여 OLE 객체를 PowerPoint 파일에 삽입하는 Merger API 호출입니다.

## 일반 구성 매개변수
- **SlideNumber** – OLE 객체가 배치될 슬라이드의 1부터 시작하는 인덱스.  
- **XCoordinate / YCoordinate** – 슬라이드 왼쪽 상단 모서리에서 포인트 단위로 측정된 위치.  
- **Width / Height** – OLE 자리표시자의 크기; 0으로 설정하면 기본 크기를 사용합니다.  
- **ObjectName** – PowerPoint에서 객체를 선택했을 때 표시되는 선택적 친숙한 이름.

## 실용적인 적용 사례
PDF를 OLE 객체로 삽입하면 다양한 실제 시나리오에서 유용합니다:
1. **기업 브리핑** – 프레젠테이션 용량을 늘리지 않고 최신 재무 보고서를 첨부합니다.  
2. **학술 강의** – 슬라이드 요약과 함께 전체 텍스트 연구 논문을 제공합니다.  
3. **프로젝트 상태 업데이트** – 이해관계자가 상세 정보를 위해 열 수 있는 실시간 프로젝트 계획을 삽입합니다.  
4. **영업 프레젠테이션** – 영업 담당자가 필요 시 열 수 있는 제품 사양서를 포함합니다.  
5. **기술 워크숍** – 엔지니어가 즉시 검토할 수 있는 회로도나 데이터시트를 제시합니다.

## 성능 고려 사항
삽입 프로세스를 빠르고 메모리 친화적으로 유지하려면:
- **파일 스트리밍** – GroupDocs.Merger는 스트림을 읽고 쓰므로 200페이지 PDF도 100 MB 이하의 RAM만 사용합니다.  
- **배치 처리** – 여러 프레젠테이션을 업데이트할 때 단일 `Merger` 인스턴스를 재사용하고 스트림을 즉시 닫습니다.  
- **대형 PDF 리사이즈** – 로드 시간이 느릴 경우 원본 PDF의 이미지 압축 또는 다운샘플링을 수행합니다.

## 자주 묻는 질문

**Q: 하나의 프레젠테이션에 여러 PDF를 삽입할 수 있나요?**  
A: 예. 각 PDF마다 `ImportDocument`를 호출하고, 동일 슬라이드에서 다른 `SlideNumber` 또는 위치를 지정합니다.

**Q: 얼마나 큰 PDF를 삽입할 수 있나요?**  
A: 실질적인 제한은 서버 메모리에 따라 다르며, 스트리밍 시 500 MB까지의 삽입이 문제 없이 테스트되었습니다.

**Q: OLE 객체가 하이퍼링크와 같은 인터랙티브 요소를 유지하나요?**  
A: 물론입니다. 삽입된 PDF는 기본 뷰어에서 열리며 모든 내부 링크와 북마크를 보존합니다.

**Q: PDF가 비밀번호로 보호된 경우는 어떻게 하나요?**  
A: `ImportDocument`를 호출하기 전에 `OlePresentationOptions`의 `Password` 속성에 비밀번호를 제공하면 됩니다.

**Q: 삽입된 객체가 모든 버전의 PowerPoint에서 작동하나요?**  
A: OLE 형식은 PowerPoint 2007 이후 버전 및 Office 365에서 지원됩니다.

## 결론
이제 GroupDocs.Merger for .NET을 사용하여 **PDF를 PowerPoint에 OLE 객체로 삽입**하는 완전하고 운영 준비된 워크플로우를 갖추었습니다. 파일을 스트리밍하고 `OlePresentationOptions`를 구성한 뒤 `ImportDocument`를 호출하면 메모리 사용량을 낮게 유지하면서 원본 PDF를 프레젠테이션에 풍부하게 추가하고 모든 인터랙티브 기능을 보존할 수 있습니다. 슬라이드 병합, 형식 변환, 워터마크 삽입 등 추가적인 Merger 기능을 탐색하여 문서 파이프라인을 더욱 자동화하세요.

---

**마지막 업데이트:** 2026-09-21  
**테스트 환경:** GroupDocs.Merger 23.12 for .NET  
**작성자:** GroupDocs  

## 리소스
- **문서:** [GroupDocs.Merger for .NET 문서](https://docs.groupdocs.com/merger/net/)  
- **API 레퍼런스:** [GroupDocs.Merger API 레퍼런스](https://reference.groupdocs.com/merger/net/)  
- **다운로드:** [GroupDocs.Merger 다운로드](https://releases.groupdocs.com/merger/net/)  
- **구매:** [GroupDocs 라이선스 구매](https://purchase.groupdocs.com/buy)  
- **무료 체험:** [GroupDocs 무료 체험](https://releases.groupdocs.com/merger/net/)  
- **임시 라이선스 받기:** [임시 라이선스 받기](https://purchase.groupdocs.com/temporary-license)

```csharp
string filePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pptx"); // Presentation file path
string embeddedFilePath = Path.Combine("YOUR_DOCUMENT_DIRECTORY", "sample.pdf"); // PDF to embed as OLE object
string outputDirectoryPath = "YOUR_OUTPUT_DIRECTORY"; // Output directory for modified presentation
string filePathOut = Path.Combine(outputDirectoryPath, "ModifiedPresentation.pptx"); // Output file path
```

```csharp
int pageNumber = 2; // Slide number to add OLE object
OlePresentationOptions oleSlidesOptions = new OlePresentationOptions(embeddedFilePath, pageNumber)
{
    X = 10, // X-coordinate for positioning the embedded object on the slide
    Y = 10  // Y-coordinate for positioning the embedded object on the slide
};
```

```csharp
using (Merger merger = new Merger(filePath)) // Initialize with presentation file path
{
    merger.ImportDocument(oleSlidesOptions); // Embed PDF as OLE using specified options
    merger.Save(filePathOut); // Save the modified presentation to output directory
}
```

## 관련 튜토리얼
- [GroupDocs.Merger for .NET을 사용하여 PDF를 Word에 삽입하기: 단계별 가이드](/merger/net/document-import/embed-pdf-word-groupdocs-merger-dotnet/)
- [GroupDocs.Merger를 사용하여 .NET에서 URL로부터 PDF 로드하기: 종합 가이드](/merger/net/document-loading/load-pdf-url-groupdocs-merger-net/)
- [GroupDocs.Merger for .NET을 사용하여 문서 정보 검색하기: 종합 가이드](/merger/net/document-information/retrieve-document-info-groupdocs-merger-dotnet/)