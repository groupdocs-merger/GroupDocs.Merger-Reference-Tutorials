---
title: XLSB 파일을 병합하는 방법
linktitle: XLSB 파일을 병합하는 방법
second_title: GroupDocs.Merger .NET API
description: XLSB 파일을 병합하는 방법을 알아보세요. 이 단계별 가이드는 문서 조작 작업을 단순화합니다.
weight: 12
url: /ko/net/spreadsheet-merging/how-to-merge-xlsb-files/
---

# XLSB 파일을 병합하는 방법

## 소개
이 튜토리얼에서는 XLSB(Excel Binary Workbook) 파일을 병합하는 방법을 살펴보겠습니다. .NET용 GroupDocs.Merger는 개발자가 .NET 응용 프로그램 내에서 다양한 문서 형식을 원활하게 병합, 분할 및 조작할 수 있게 해주는 강력한 문서 조작 API입니다. 특히 이 다용도 라이브러리를 사용하여 XLSB 파일을 병합하는 데 중점을 둘 것입니다.
## 전제 조건
튜토리얼을 시작하기 전에 다음 전제 조건이 설정되어 있는지 확인하세요.
- 시스템에 Visual Studio가 설치되어 있습니다.
- C# 프로그래밍에 대한 기본 지식.
- .NET용 GroupDocs.Merger 라이브러리가 다운로드되어 프로젝트에서 참조됩니다.
  

## 네임스페이스 가져오기
코딩을 시작하기 전에 필요한 네임스페이스를 C# 프로젝트로 가져옵니다.
```csharp
using System; 
using GroupDocs.Merger;
using System.IO;
```
## 1단계: 출력 디렉터리 설정
```csharp
string outputFolder = "Your Output Directory";
```
## 2단계: 출력 파일 경로 정의
```csharp
string outputFile = Path.Combine(outputFolder, "merged.xlsb");
```
## 3단계: 소스 XLSB 파일 로드
```csharp
// 소스 XLSB 파일 로드
using (var merger = new GroupDocs.Merger.Merger("Your Sample File"))
{
    // 병합할 다른 XLSB 파일 추가
    merger.Join("Your Sample File");
    // XLSB 파일 병합 및 결과 저장
    merger.Save(outputFile);
}
```
## 4단계: 병합 완료 메시지 표시
```csharp
Console.WriteLine("\nXLSB files merge completed successfully. \nCheck output in {0}", outputFolder);
```

## 결론
다음 단계를 따르면 XLSB 파일을 쉽게 병합할 수 있습니다. 이 API는 문서 조작 작업을 단순화하고 .NET 애플리케이션에 대한 원활한 통합을 제공합니다.

## FAQ
### GroupDocs.Merger는 XLSB 외에 다른 파일 형식을 처리할 수 있습니까?
예, GroupDocs.Merger는 DOCX, PDF, XLSX, PPTX 등을 포함한 광범위한 문서 형식을 지원합니다.
### GroupDocs.Merger에 대한 추가 문서는 어디서 찾을 수 있나요?
 방문하다[선적 서류 비치](https://tutorials.groupdocs.com/merger/net/) 자세한 사용 지침 및 API 참조를 확인하세요.
### GroupDocs.Merger에 대한 무료 평가판이 있습니까?
 예, 액세스할 수 있습니다[무료 시험판](https://releases.groupdocs.com/)GroupDocs.Merger의 기능을 살펴보세요.
### GroupDocs.Merger에 대한 기술 지원을 받으려면 어떻게 해야 합니까?
 가입하다[GroupDocs 포럼](https://forum.groupdocs.com/c/merger/32) 질문을 하고 커뮤니티와 상호작용할 수 있습니다.
### GroupDocs.Merger 라이센스는 어디서 구입할 수 있나요?
 에서 라이센스를 구입할 수 있습니다.[구매 페이지](https://purchase.groupdocs.com/buy).