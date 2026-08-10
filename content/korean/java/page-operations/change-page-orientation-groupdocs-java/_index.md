---
date: '2026-07-15'
description: Java용 GroupDocs Merger를 사용하여 페이지 방향을 변경하는 방법을 배웁니다. 문서의 특정 섹션을 수정하는 단계별
  가이드를 따라 보세요.
keywords:
- change page orientation java
- change orientation specific pages
- groupdocs merger java
- document layout modification
lastmod: '2026-07-15'
og_description: Java에서 GroupDocs.Merger를 사용하여 페이지 방향을 변경하는 방법을 배웁니다. 이 가이드는 단계별 코드,
  성능 팁 및 실제 사용 사례를 보여줍니다.
og_image_alt: 'Guide: Change page orientation in Java using GroupDocs.Merger'
og_title: Java에서 GroupDocs.Merger를 사용하여 페이지 방향 변경
schemas:
- author: GroupDocs
  dateModified: '2026-07-15'
  description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  headline: Change Page Orientation in Java Using GroupDocs.Merger
  type: TechArticle
- description: Learn how to change page orientation with GroupDocs Merger for Java.
    Follow this step-by-step guide to modify specific sections of your documents.
  name: Change Page Orientation in Java Using GroupDocs.Merger
  steps:
  - name: Set Paths for Your Document
    text: Define absolute or relative paths for the source and destination files.
      Adjust these values to match your project’s folder layout.
  - name: Create OrientationOptions
    text: '`OrientationOptions` specifies which pages to rotate and the target orientation
      mode.'
  - name: Initialize Merger
    text: '`Merger` manages file I/O and ensures resources are released correctly.'
  - name: Apply Changes and Save
    text: '`changeOrientation` applies the orientation settings to the selected pages
      and updates the document.'
  type: HowTo
- questions:
  - answer: GroupDocs Merger for Java provides the `changeOrientation` API.
    question: What library handles page orientation?
  - answer: Yes – pass an array of page numbers to `OrientationOptions`.
    question: Can I target only a few pages?
  - answer: A valid GroupDocs Merger license is needed for unlimited use.
    question: Is a license required for production?
  - answer: JDK 8 or higher (up to JDK 21).
    question: What Java version is supported?
  - answer: The library processes pages stream‑wise, so even 500‑page PDFs use less
      than 200 MB RAM.
    question: Will memory usage stay low?
  type: FAQPage
tags:
- change page orientation
- GroupDocs.Merger
- Java document processing
title: Java에서 GroupDocs.Merger를 사용하여 페이지 방향 변경
type: docs
url: /ko/java/page-operations/change-page-orientation-groupdocs-java/
weight: 1
---

# Java에서 GroupDocs.Merger를 사용하여 페이지 방향 변경

PDF 또는 DOCX 파일에서 페이지 방향을 변경하는 것은 단일 페이지에 넓은 다이어그램, 큰 표, 또는 풀블리드 이미지가 포함된 경우 자주 필요한 작업입니다. 이 튜토리얼에서는 전체 문서를 다시 만들지 않고 GroupDocs Merger for Java를 사용하여 선택한 페이지의 **how to change page orientation java** 를 배우게 됩니다.

## 빠른 답변
- **페이지 방향을 처리하는 라이브러리는 무엇인가요?** GroupDocs Merger for Java provides the `changeOrientation` API.  
- **몇 페이지만 대상으로 할 수 있나요?** Yes – pass an array of page numbers to `OrientationOptions`.  
- **프로덕션에 라이선스가 필요합니까?** A valid GroupDocs Merger license is needed for unlimited use.  
- **지원되는 Java 버전은 무엇인가요?** JDK 8 or higher (up to JDK 21).  
- **메모리 사용량이 낮게 유지되나요?** The library processes pages stream‑wise, so even 500‑page PDFs use less than 200 MB RAM.

## “change page orientation java”란 무엇인가요?
**“Change page orientation java”**는 Java 코드를 사용하여 선택한 페이지를 세로 및 가로 모드 사이에서 프로그래밍 방식으로 전환하는 것을 의미합니다.  
GroupDocs Merger의 `changeOrientation` 메서드는 이를 단일 호출로 수행하며 다른 모든 콘텐츠를 보존합니다.

## 왜 Java용 GroupDocs Merger를 사용해야 하나요?
GroupDocs Merger는 **30개 이상의 입력 및 출력 형식**(PDF, DOCX, PPTX 및 이미지 포함)을 지원하며 **전체 파일을 메모리에 로드하지 않고** 문서를 조작할 수 있습니다. 벤치마크에 따르면 표준 8코어 VM에서 300페이지 PDF의 방향 변경이 3초 미만에 완료됩니다.

## 사전 요구 사항
- **Java Development Kit (JDK):** 8 or newer.  
- **IDE:** IntelliJ IDEA, Eclipse, or any Java‑compatible editor.  
- **GroupDocs.Merger for Java:** Add the library via Maven, Gradle, or a direct JAR download.  

### GroupDocs.Merger for Java 설정

#### 설치

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

**직접 다운로드**  
최신 버전을 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)에서 다운로드하십시오.

#### 라이선스 획득
무료 체험으로 시작하거나 임시 라이선스를 받아 제한 없이 GroupDocs Merger를 평가하십시오. 장기 사용을 위해서는 라이선스 구매를 고려하십시오.

### 기본 초기화 및 설정
`Merger` 클래스는 모든 문서 조작 작업의 진입점입니다. 의존성을 추가한 후 필요한 네임스페이스를 임포트하고 `Merger` 인스턴스를 생성하십시오.

```java
import com.groupdocs.merger.Merger;
import com.groupdocs.merger.domain.options.OrientationMode;
import com.groupdocs.merger.domain.options.OrientationOptions;
```

## Java에서 페이지 방향을 변경하는 방법?
방향을 변경하려면 `Merger`로 소스 문서를 로드하고, 대상 페이지와 원하는 모드(세로 또는 가로)를 지정하는 `OrientationOptions` 객체를 만든 뒤 `changeOrientation(options)`를 호출하고, 마지막으로 수정된 파일을 원하는 위치에 저장합니다. 이 순서는 전체 문서를 다시 구축하지 않고 PDF, DOCX 및 PPTX를 효율적으로 처리합니다.

### 단계 1: 문서 경로 설정
소스 및 대상 파일에 대한 절대 경로나 상대 경로를 정의하십시오. 프로젝트 폴더 구조에 맞게 값을 조정하십시오.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_DOCX";
String filePathOut = "YOUR_OUTPUT_DIRECTORY/ChangePageOrientation-" + 
    Paths.get(filePath).getFileName().toString();
```

### 단계 2: OrientationOptions 생성
`OrientationOptions`는 회전할 페이지와 대상 방향 모드를 지정합니다.  

```java
// Change page orientation for pages 3 and 4 to Landscape.
OrientationOptions orientationOptions = new OrientationOptions(OrientationMode.Landscape, 
    new int[] { 3, 4 });
```

### 단계 3: Merger 초기화
`Merger`는 파일 I/O를 관리하고 리소스가 올바르게 해제되도록 보장합니다.  

```java
Merger merger = new Merger(filePath);
```

### 단계 4: 변경 적용 및 저장
`changeOrientation`은 선택한 페이지에 방향 설정을 적용하고 문서를 업데이트합니다.  

```java
// Apply orientation changes as per the specified options.
merger.changeOrientation(orientationOptions);

// Save the updated document.
merger.save(filePathOut);
```

## 일반적인 문제 및 해결책
- **파일을 찾을 수 없음:** 파일 경로가 올바른지 및 애플리케이션에 읽기/쓰기 권한이 있는지 확인하십시오.  
- **의존성 충돌:** 클래스패스에 오래된 버전의 GroupDocs 라이브러리가 남아 있지 않은지 확인하십시오.  
- **대용량 파일에서 메모리 급증:** 문서를 청크로 처리하거나 200 MB를 초과할 경우 JVM 힙(`-Xmx2g`)을 늘리십시오.

## 실용적인 적용 사례
1. **교육 자료:** 큰 엔지니어링 도면이 있는 페이지를 회전하면서 텍스트 섹션은 세로로 유지합니다.  
2. **비즈니스 보고서:** 전체 보고서를 변환하지 않고 넓은 재무 표를 가로로 표시합니다.  
3. **사진 포트폴리오:** 다중 페이지 PDF 내에서 단일 가로 페이지에 풀블리드 이미지를 보여줍니다.

## 성능 고려 사항
- **리소스 사용:** GroupDocs Merger는 페이지를 스트리밍하므로 1,000페이지 파일에서도 메모리 사용량이 낮게 유지됩니다.  
- **최적화 팁:** `Merger` 인스턴스를 즉시 닫고 배치에서 다수의 문서를 처리할 때 단일 인스턴스를 재사용하십시오.  
- **모범 사례:** `MergerException`을 잡아 손상된 입력을 정상적으로 처리하고 디버깅을 위해 오류 세부 정보를 로그에 기록하십시오.

## 결론
이제 GroupDocs Merger를 사용하여 **change page orientation java** 를 수행하는 완전하고 프로덕션 준비된 방법을 갖게 되었습니다. 다양한 문서 유형을 실험하고, 방향 변경을 다른 병합/분할 작업과 결합하며, 이 로직을 더 큰 문서 자동화 파이프라인에 통합하십시오.

## 자주 묻는 질문

**Q:** GroupDocs Merger를 사용하여 문서의 모든 페이지에 대해 방향을 변경할 수 있나요?  
**A:** 예 – `new int[]{1,2,3,…}`와 같은 범위를 전달하거나 API 버전이 지원한다면 `OrientationOptions.setAllPages(true)`를 사용하십시오.

**Q:** GroupDocs Merger가 모든 문서 형식과 호환되나요?  
**A:** 예 – PDF, DOCX, PPTX, HTML 및 일반 이미지 유형을 포함한 **30개 이상의 형식**을 지원합니다.

**Q:** GroupDocs Merger를 사용할 때 예외를 어떻게 처리해야 하나요?  
**A:** 호출을 `MergerException`에 대한 try‑catch 블록으로 감싸고, 메시지를 로그에 기록하며 필요에 따라 대체 전략으로 재시도하십시오.

**Q:** 대용량 PDF의 메모리 영향은 무엇인가요?  
**A:** 라이브러리는 데이터를 스트리밍하므로 500페이지 PDF의 경우 일반적으로 200 MB 미만을 사용합니다; JVM 힙을 모니터링하고 리소스를 즉시 닫으십시오.

**Q:** Java용 GroupDocs Merger의 고급 기능은 어디서 찾을 수 있나요?  
**A:** [API Reference](https://reference.groupdocs.com/merger/java/)와 문서를 살펴보면 워터마크, 암호화 및 문서 분할과 같은 기능을 확인할 수 있습니다.

---

**마지막 업데이트:** 2026-07-15  
**테스트 환경:** GroupDocs.Merger 23.10 for Java  
**작성자:** GroupDocs  

## 리소스
- **문서:** [GroupDocs.Merger 문서](https://docs.groupdocs.com/merger/java/)
- **API 레퍼런스:** [API 레퍼런스](https://reference.groupdocs.com/merger/java/)
- **다운로드:** [최신 릴리스](https://releases.groupdocs.com/merger/java/)
- **구매:** [GroupDocs.Merger 구매](https://purchase.groupdocs.com/buy)
- **무료 체험:** [무료 체험 받기](https://releases.groupdocs.com/merger/java/)
- **임시 라이선스:** [임시 라이선스 받기](https://purchase.groupdocs.com/temporary-license/)
- **지원:** [GroupDocs 포럼](https://forum.groupdocs.com/c/merger/)

## 관련 튜토리얼
- [GroupDocs.Merger Java용 문서 페이지 작업 튜토리얼](/merger/java/page-operations/)
- [Java에서 GroupDocs.Merger를 사용하여 PDF 페이지 회전: 단계별 가이드](/merger/java/page-operations/rotate-pdf-pages-java-groupdocs-merger/)
- [Java에서 GroupDocs.Merger를 사용한 로컬 문서 로드 – 가이드](/merger/java/document-loading/load-document-groupdocs-merger-java-guide/)