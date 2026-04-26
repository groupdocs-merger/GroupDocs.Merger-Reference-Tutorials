---
date: '2026-01-24'
description: GroupDocs.Merger for Java를 사용하여 페이지 미리보기를 생성함으로써 문서를 미리 보는 방법을 배우세요.
  이는 문서 썸네일 생성을 위해 페이지를 이미지로 빠르게 변환하는 방법입니다.
keywords:
- GroupDocs.Merger for Java
- document page previews
- Java document management
title: GroupDocs.Merger for Java를 사용하여 문서 미리보기하는 방법
type: docs
url: /ko/java/document-information/generate-document-page-previews-groupdocs-merger-java/
weight: 1
---

# GroupDocs.Merger for Java를 사용한 문서 미리보기 방법

Creating document page previews is a powerful way to **how to preview documents** quickly, giving users a visual snapshot without opening the full file. In this tutorial you’ll learn how to generate those previews using GroupDocs.Merger for Java, a library that makes it easy to **convert pages to images** and support **document thumbnail generation** in your applications.

## 빠른 답변
- **What does “preview documents” mean?** 각 페이지의 가벼운 이미지 표현을 생성하는 것입니다.  
- **Which format is used for previews?** 기본은 JPEG이며, 다른 형식도 지원됩니다.  
- **Do I need a license?** 개발에는 무료 체험판을 사용할 수 있으며, 프로덕션에는 유료 라이선스가 필요합니다.  
- **Can I customize the output path?** 예, 사용자 정의 `PageStreamFactory`를 구현하면 됩니다.  
- **What Java version is required?** JDK 8 이상.

## “how to preview documents”란 무엇인가요?
문서를 미리보기한다는 것은 각 페이지에 대한 시 있게 하는 것을 의미합니다. 이 기술은 문서 관리 시스템, 포털 및 파일을케이션에서 사용자 경험을 향상시킵니다.

## 왜 GroupDocs.Merger for Java를 사용해야 할까요?
- **Fast conversion** 전체 문서를 UI에서 열지 않고도 페이지를 이미지로 빠르게 변환합니다.  
- **아래 설치 방법 참고). 설치 for Java 설정
Add the library to your project using your preferred build tool.

**Maven:**  
```xml
<dependency>
    <groupId>com.groupdocs</groupId>
    <artifactId>groupdocs-merger</artifactId>
    <version>latest-version</version>
</dependency>
```

**Gradle:**  
```gradle
implementation 'com.groupdocs:groupdocs-merger:latest-version'
```

**Direct Download:**  
또는 최신 버전을 [GroupDocs.Merger for Java releases](https://releases.groupdocs.com/merger/java/)에서 다운로드하십시오.

### 라이선스 획득
- **Free Trial:** 기능을 살펴보기 위해 무료 체험판을 다운로드하십시오.  
- **Temporary License:** 개발 중에 장기 사용을 위해 임시 라이선스를 획득하십시오.  
- **Purchase:** 전체 프로덕션 사용을 위해 [GroupDocs](https://purchase.groupdocs.com/buy)에서 라이선스를 구매하십시오.

라이브러리를 추가한 후, 미리보기를 원하는 문서 경로로 초기화합니다:
```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

## 문서 미리보기: 단계별 가이드

### 단계 1: Merger 초기화 및 PageStreamFactory 정의
`PageStreamFactory`는 라이브러리에게 각 미리보기 이미지를 어디에 쓸지 알려줍니다.

```java
String filePath = "YOUR_DOCUMENT_DIRECTORY/SAMPLE_XLSX";
Merger merger = new Merger(filePath);
```

```java
IPreviewOptions previewOption = new PreviewOptions(new PageStreamFactory() {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        return createStream(pageNumber);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        releasePageStream(pageNumber, pageStream);
    }
}, PreviewMode.JPEG);
```

### 단계 2: 미리보기 생성
방금 설정한 옵션을 사용하여 `generatePreview` 메서드를 호출합니다.

```java
merger.generatePreview(previewOption);
```

### 페이지를 이미지로 변환 – 커스텀 PageStreamFactory
파일 이름 지정이나 저장 위치에 대한 더 많은 제어가 필요하면 자체 팩토리를 구현하십시오:
```java
class CustomPageStreamFactory implements PageStreamFactory {
    @Override
    public OutputStream createPageStream(int pageNumber) {
        String filePath = "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
        return new FileOutputStream(filePath);
    }
    
    @Override
    public void closePageStream(int pageNumber, OutputStream pageStream) {
        try {
            if (pageStream != null) {
                pageStream.close();
            }
        } catch (Exception e) {
            throw new RuntimeException(e);
        }
    }
}
```

### 헬퍼 메서드 – 스트림 관리
이 유틸리티 메서드들은 코드를 깔끔하게 유지하고 예외를 깔끔하게 처리합니다.
```java
private static String getImagePath(int pageNumber) {
    return "YOUR_OUTPUT_DIRECTORY/image-" + pageNumber + ".jpg";
}

private static OutputStream createStream(int pageNumber) {
    try {
        String imageFilePath = getImagePath(pageNumber);
        return new FileOutputStream(imageFilePath);
    } catch (FileNotFoundException e) {
        throw new RuntimeException(e);
    }
}

private static void releasePageStream(int pageNumber, OutputStream pageStream) {
    try {
        if (pageStream != null) {
            pageStream.close();
        }
    } catch (Exception e) {
        throw new RuntimeException(e);
    }
}
```

## 문서 썸네일 생성 – 실용적인 적용 사례
미리보기를 생성하는 것은 특히 다음과 같은 경우에 유용합니다:

1. **Document Management Systems** – 사용자는 파일을 열지 않고도 훑어볼 수 있습니다.  
2. **Content Review Platforms** – 업로드 승인 전에 빠른 시각적 검사를 할 수 있습니다.  
3. **Educational Tools** – 학생들이 강의 슬라이드나 교과서 페이지를 한눈에 볼 수 있습니다.  

## 성능 고려 사항
- **Release streams promptly** 메모리를 해제하기 위해 스트림을 즉시 해제합니다.  
- **Avoid loading whole documents** 전체 문서를 메모리에 로드하지 말고, 라이브러리가 페이지 처리를 하도록 합니다.  
- **Use appropriate image quality** 설정을 사용하여 속도와 시각적 품질 사이의 균형을 맞춥니다.

## 자주 묻는 질문

**Q: GroupDocs.Merger for Java는 무엇에 사용되나요?**  
A: 문서를 효율적으로 병합, 분할 및 관리하는 데 사용되며, 미리보기 생성도 포함됩니다.

**Q: 스트림 작업 중 예외를 어떻게 처리하나요?**  
A: 헬퍼 메서드에 표시된 대로 스트림 생성 및 종료를 try‑catch 블록으로 감싸세요.

**Q: JPEG 외의 형식으로 미리보기를 생성할 수 있나요?**  
A: 예, 필요에 따라 `PreviewMode` 열거형을 PNG, BMP 등으로 변경하면 됩니다.

**Q: 문서 미리보기 생성 시 흔히 발생하는 문제는 무엇인가요?**  
A: 일반적인 문제는 잘못된 파일 경로와 스트림을 닫지 않아 메모리 누수가 발생하는 것입니다.

**Q: GroupDocs.Merger를 다른 시스템과 어떻게 통합할 수 있나요?**  
A: API를 사용하여 데이터베이스, 웹 서비스 또는 다른 Java 애플리케이션과 연결해 원활한 워크플로 자동화를 구현할 수 있습니다.

## 추가 자료
- [문서](https://docs.groupdocs.com/merger/java/)
- [API 레퍼런스](https://reference.groupdocs.com/merger/java/)
- [다운로드](https://releases.groupdocs.com/merger/java/)
- [구매](https://purchase.groupdocs.com/buy)
- [무료 체험](https://releases.groupdocs.com/merger/java/)
- [임시 라이선스](https://purchase.groupdocs.com/temporary-license/)
- [지원](https://forum.groupdocs.com/c/merger/)

---

**마지막 업데이트:** 2026-01-24  
**테스트 환경:** GroupDocs.Merger 최신 버전 (2025‑latest)  
**작성자:** GroupDocs