---
date: '2025-12-19'
description: GroupDocs.Merger for Java를 사용하여 워드 문서에 PDF를 삽입하고 워드 파일에 PDF를 추가하는 방법을
  배우세요. 원활한 OLE 삽입을 위한 단계별 튜토리얼.
keywords:
- embed OLE objects in Word documents
- GroupDocs Merger for Java tutorial
- import OLE objects using Java
title: GroupDocs.Merger for Java를 사용하여 PDF를 Word에 삽입하는 방법 – 종합 가이드
type: docs
url: /ko/java/document-import/embed-ole-objects-word-documents-groupdocs-java/
weight: 1
---

# GroupDocs.Merger for Java를 사용하여 Word에 PDF 삽입하는 방법

PDF를 Word 문서에 직접 삽입하면 협업이 크게 향상됩니다. 독자는 파일 간 전환이 필요하지 않기 때문입니다. 이 가이드에서는 GroupDocs.Merger for Java를 사용하여 **Word에 PDF를 삽입하는 방법**을 알아보고, **PDF를 Word에 추가**하는 워크플로우에 대한 실용적인 팁을 확인합니다. 라이브러리 설정부터 OLE 객체의 크기와 위치를 맞춤 설정하는 방법까지 모두 안내합니다.

## 빠른 답변
- **필요한 라이브러리는?** GroupDocs.Merger for Java (latest version)  
- **모든 파일 유형을 삽입할 수 있나요?** Yes – PDFs, images, spreadsheets, etc., as OLE objects  
- **라이선스가 필요합니까?** A free trial works for development; a commercial license is required for production  
- **어떤 Java IDE가 가장 적합합니까?** IntelliJ IDEA, Eclipse, or any IDE that supports Maven/Gradle  
- **구현에 얼마나 걸립니까?** Roughly 10‑15 minutes for a basic embed  

## Word에 PDF를 삽입하는 것이란?
PDF를 삽입하면 Word 파일 안에 OLE(Object Linking and Embedding) 객체가 생성됩니다. PDF는 완전한 기능을 유지하며—사용자는 아이콘을 더블 클릭하여 PDF 뷰어에서 열 수 있고, Word 문서는 자체 포함된 상태를 유지합니다.

## GroupDocs.Merger를 사용하여 Word에 PDF를 추가하는 이유는?
- **단일 소스 문서화:** 계약서, 매뉴얼, 보고서를 외부 링크 없이 함께 보관합니다.  
- **향상된 접근성:** 독자는 Word 환경을 떠나지 않고 PDF를 볼 수 있습니다.  
- **자동화 친화적:** 배치 보고서나 법률 패키지를 프로그래밍 방식으로 생성하는 데 최적입니다.

## 사전 요구 사항
- **라이브러리 및 종속성:** Maven 또는 Gradle을 통해 GroupDocs.Merger 라이브러리를 포함합니다.  
- **개발 환경:** IntelliJ IDEA, Eclipse 또는 기타 Java IDE.  
- **기본 지식:** Java 및 문서 조작 개념에 익숙함.  

## GroupDocs.Merger for Java 설정
OLE 객체를 삽입하려면 먼저 라이브러리를 프로젝트에 추가합니다.

### Maven
다음 의존성을 `pom.xml` 파일에 추가하세요:
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

### Gradle
다음 내용을 `build.gradle` 파일에 포함하세요:
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

### 직접 다운로드
또는 [GroupDocs.Merger for Java releases page](https://releases.groupdocs.com/merger/java/)에서 최신 버전을 다운로드하세요.

**라이선스 획득:** 무료 체험으로 시작하거나 구매 전 기능을 평가하기 위해 임시 라이선스를 얻을 수 있습니다. 자세한 내용은 [Purchase GroupDocs](https://purchase.groupdocs.com/buy)를 방문하세요.

## 기본 초기화
OLE 객체를 다루기 위해 필요한 클래스를 가져옵니다:
```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OleWordProcessingOptions;
```

## PDF를 Word에 삽입하는 단계별 가이드

### 단계 1: 파일 경로 및 대상 페이지 정의
소스 Word 문서, 삽입하려는 PDF, OLE 객체가 표시될 위치를 설정합니다.
```java
String sourceFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.docx"; // Source Word document path
String embeddedFilePath = "YOUR_DOCUMENT_DIRECTORY/sample.pdf"; // File to be embedded as an OLE object
String outputFilePath = new File("YOUR_OUTPUT_DIRECTORY",
    "ImportDocumentToWordProcessing-" + Paths.get(sourceFilePath).getFileName().toString()).getPath();
int pageNumber = 2; // Page number where the OLE object will be inserted
```

- **`sourceFilePath`** – 기존 Word 파일의 경로.  
- **`embeddedFilePath`** – **Word에 PDF를 추가**하려는 PDF 파일.  
- **`outputFilePath`** – 새 문서를 저장할 위치.  
- **`pageNumber`** – OLE 객체가 삽입될 페이지 번호.  

### 단계 2: OleWordProcessingOptions 구성
삽입된 PDF의 크기를 설정하여 외관을 맞춤화합니다.
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Set width of the embedded object (in points)
oleWordsOptions.setHeight(300); // Set height of the embedded object (in points)
```

- **`setWidth()` / `setHeight()`** – Word 문서 내에서 PDF 아이콘이 표시되는 크기를 제어합니다.  

### 단계 3: Merger 초기화 및 OLE 객체 가져오기
소스 문서에 대한 `Merger` 인스턴스를 생성하고, OLE 객체를 가져온 뒤 결과를 저장합니다.
```java
Merger merger = new Merger(sourceFilePath);
{
    merger.importDocument(oleWordsOptions); // Embed the OLE object into the Word document
    merger.save(outputFilePath); // Save changes to a new output file
}
```

- **`importDocument()`** – `OleWordProcessingOptions`를 받아 PDF를 OLE 객체로 삽입합니다.  
- **`save()`** – 수정된 문서를 `outputFilePath`에 기록합니다.  

### 단계 4: (선택) 추가 객체에 대한 구성 재적용
추가 PDF를 삽입해야 하면 새로운 파일 경로와 페이지 번호로 **Step 1‑3**을 반복합니다. 동일한 `OleWordProcessingOptions` 클래스를 사용해 각 객체를 개별적으로 제어할 수 있습니다.

## OleWordProcessingOptions 구성 (고급)
객체 정렬이나 캡션 추가와 같이 배치를 더 세밀하게 조정할 수 있습니다. 아래 코드 스니펫은 명확성을 위해 기본 구성을 다시 보여줍니다:
```java
OleWordProcessingOptions oleWordsOptions = new OleWordProcessingOptions(embeddedFilePath, pageNumber);
oleWordsOptions.setWidth(300); // Width of the embedded object
oleWordsOptions.setHeight(300); // Height of the embedded object
```

## 실용적인 적용 사례
PDF 삽입은 다양한 실제 시나리오에서 유용합니다:

1. **Technical Manuals** – 상세 도면이나 참고 PDF를 가이드에 직접 삽입합니다.  
2. **Financial Reports** – 주요 보고서 흐름을 끊지 않고 보조 감사 PDF를 추가합니다.  
3. **Legal Contracts** – 검토 중에 쉽게 접근할 수 있도록 부록이나 전시물을 OLE 객체로 첨부합니다.  

## 성능 고려 사항
대용량 문서나 다수의 OLE 객체를 다룰 때는 다음 팁을 기억하세요:

- **불필요한 내용 제거** – 실제로 필요한 페이지만 삽입합니다.  
- **메모리 관리** – 큰 파일을 위해 Java의 `-Xmx` 플래그로 충분한 힙 공간을 할당합니다.  
- **업데이트 유지** – 최신 GroupDocs.Merger 릴리스에는 성능 최적화가 포함되는 경우가 많습니다.  

## 자주 묻는 질문

**Q: OLE 삽입이란?**  
A: 삽입을 통해 PDF와 같은 객체를 원본 기능을 유지하는 링크 형태로 Word 문서에 넣을 수 있습니다.

**Q: 하나의 문서에 여러 OLE 객체를 삽입할 수 있나요?**  
A: 예, 각각을 별도의 `OleWordProcessingOptions`로 구성하여 서로 다른 페이지와 크기로 설정할 수 있습니다.

**Q: 삽입 파일 크기에 제한이 있나요?**  
A: 제한은 주로 Word 자체의 제약에 따르지만, GroupDocs.Merger는 대용량 파일을 효율적으로 처리합니다.

**Q: 삽입 오류를 어떻게 해결하나요?**  
A: 파일 경로가 올바른지, JVM에 충분한 메모리가 있는지 확인하세요. 원본 PDF가 손상되지 않았는지도 점검합니다.

**Q: 삽입 후에 객체를 수정할 수 있나요?**  
A: Microsoft Word에서 Word 파일을 다시 열어 OLE 객체를 편집하거나, 업데이트된 옵션으로 Merger 코드를 다시 실행할 수 있습니다.

## 추가 자료
- [GroupDocs.Merger Documentation](https://docs.groupdocs.com/merger/java/)
- [API Reference](https://reference.groupdocs.com/merger/java/)
- [Download Latest Version](https://releases.groupdocs.com/merger/java/)
- [Purchase GroupDocs](https://purchase.groupdocs.com/buy)
- [Free Trial](https://releases.groupdocs.com/merger/java/)
- [Temporary License](https://purchase.groupdocs.com/temporary-license/)
- [Support Forum](https://forum.groupdocs.com/c/merger/)

---

**Last Updated:** 2025-12-19  
**Tested With:** GroupDocs.Merger for Java latest version  
**Author:** GroupDocs  

---