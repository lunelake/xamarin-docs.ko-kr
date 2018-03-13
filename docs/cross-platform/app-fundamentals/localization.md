---
title: "응용 프로그램 사용자 인터페이스 지역화"
ms.topic: article
ms.prod: xamarin
ms.assetid: CC6847B2-23FB-4EDE-9F7E-EF29DD46A5C5
ms.technology: xamarin-cross-platform
author: asb3993
ms.author: amburns
ms.date: 03/22/2017
ms.openlocfilehash: 510e8a6b0b2839a1a191538e7fb4e49bd005b450
ms.sourcegitcommit: 30055c534d9caf5dffcfdeafd6f08e666fb870a8
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2018
---
# <a name="localization"></a>지역화

이 가이드의 개념을 소개 *국제화* 및 *지역화* 이러한 개념을 사용 하 여 Xamarin 모바일 응용 프로그램을 생성 하는 방법에 대 한 지침에 대 한 링크입니다.

Xamarin 앱을 지역화 하는 기술 세부 정보로 바로 이동 하려는 경우 다음 플랫폼 관련 방법 도움말 문서 중 하나를 시작 합니다.

- [**Xamarin.Forms** ](~/xamarin-forms/app-fundamentals/localization.md) RESX 파일을 사용 하 여 플랫폼 간 지역화 합니다.
- [**Xamarin.iOS** ](~/ios/app-fundamentals/localization/index.md) 네이티브 플랫폼 지역화 합니다.
- [**Xamarin.Android** ](~/android/app-fundamentals/localization.md) 네이티브 플랫폼 지역화 합니다.

## <a name="i18n-and-l10n"></a>i18n 및 L10n

*국제화* 서로 다른 언어를 표시 하 고 서로 다른 로캘 (예: 숫자 및 날짜 서식 지정)에 대 한 표시를 위해 조정 수 있는 코드를 작성 하는 프로세스입니다. 이 라고도 *전역화*합니다.

*지역화* 뒤에 오는 – 각 언어에 대 한 리소스 (예: 문자열 및 이미지)를 만들고 internationalize 앱 묶어 단계입니다.

국제화 i18n-18 문자 "i"와 "n" 사이 대 한 줄임 종종 줄어듭니다. L10n를-10 개의 문자 사이 "L" 및 "n"에 대 한 지역화 마찬가지로 줄어듭니다.

## <a name="overview"></a>개요

이 문서에서는 국제화 및 지역화 및 적용 되는 방식에 모바일 응용 프로그램 개발 일반적와 관련 된 개념을 소개 합니다.
지역화 포함에 대 한 매개 변수화 해야는 없지만 디자인 하 고 응용 프로그램을 작업을 빌드할 때 하드 코드 된 이전에 있을 수 있습니다.

-   화면 레이아웃 및 텍스트,
-   아이콘, 그래픽 및 색
-   비디오 및 사운드 파일
-   동적 텍스트와 텍스트 서식 (예: 숫자, 통화 및 날짜)
 - 오른쪽에서 왼쪽 (RTL) 언어에 대 한 레이아웃 변경 하 고
-   데이터를 정렬 합니다.

어느 것을 앱에 이러한 팁이 대상으로 하는 모바일 플랫폼 높은 품질의 지역화 된 응용 프로그램 빌드 데 도움이 됩니다.


## <a name="design-considerations"></a>디자인 고려 사항

해당 콘텐츠를 지역화할 수 있도록 응용 프로그램을 설계 국제화를 라고 합니다. 언어 및 로캘 (이미지, 사운드 및 비디오 포함)에 따라 런타임에 로드 되도록 문자열 방금 다른 언어에 대 한 허용 –를 변경할 수 있는 모든 리소스에 대 한 허용 해야 제대로 디자인된 한 앱 보다 더 많은 국제화를 제대로 수행 하 고를 조정 하 서식 및 레이아웃에 대처할 수 있는 다른 문자열의 경우.

이 섹션에서는 국제화 된 응용 프로그램을 작성할 때 고려해 야 몇 가지 디자인 고려 사항을 설명 합니다.

### <a name="layouts-and-string-length"></a>레이아웃 및 문자열 길이

중국어, 일본어 문자열 매우 짧을 수 – 경우에 따라 하나 이상의 문자가 입력된 필드 레이블에 대 한 충분 한 의미를 가질 수 있습니다.

독일어 문자열 (예) 매우 길어질 수 있습니다. 경우에 따라 비교적 짧은 단어 영어로 하거나 잘린 또는 다른 레이아웃을 리플로우 예기치 않게 되 고 다른 언어-매우 긴 됩니다.

영어, 독일어, 및 일본어 iOS 홈 화면에서 몇 가지 항목에 대 한 문자열 길이 비교 합니다.

[![](localization-images/language-compare-sml.png "독일어 vs 일본어 문자열 길이")](localization-images/language-compare.png#lightbox)

다음에 유의 **설정을** 영어로 (8 자)은 13 자로 독일어 변환이 하지만 두 문자만 일본어에서에 대 한 필요 합니다.

여기서는 레이블 표시 및 입력된 필드는 side-by-side-레이아웃은 레이블 길이 크게 달라질 수가지고 작업 하기 어려웠습니다. 종종 필드 위에 레이블을 표시 되는 위치는 레이아웃 화면의 전체 너비는 레이블과 입력에 사용할 수 있는 많으므로 지역화 하기가 더 쉽습니다.

일반적으로 작성 하는 경우 고정된 레이아웃 (특히-나란히 요소) 영어 문자열 보다 더 많은 너비 레이블과 텍스트에 대 한 필요한 최소 50%를 사용 합니다. 이 모든 문제가 해결 되지 않습니다 되지만 대부분의 경우에서 작동 하는 버퍼를 제공 합니다.

### <a name="input-validation"></a>입력된 유효성 검사

유효성 검사 규칙을 작성할 때 가정에 주의 하십시오. 단일 문자에 거의 모든 의미가 있으므로 "require" 영어로 최소 3 개의 문자를 입력 하는 텍스트 필드를 요구 하는 데 유효한 보일 수 있습니다. 중국어, 일본어에서 단일 문자 유효한 입력 될 수 있지만 유효성 검사 메시지 "3 자 이상는 필요한" 무의미 해당 언어에 대 한 합니다.

웹 사이트 URL 문자로 더 복잡해 ASCII 하위 집합으로 제한 되지 않습니다. 또는 다른 단순 작업 등 전자 메일 주소 유효성 검사.

대화 상자를 염두 국제화 된 유효성 검사 규칙 가장 덜 제한적인 규칙을 선택 하거나 각 언어에 대해 다르게 작동 하는 논리를 작성을 작성 합니다.

### <a name="images-and-color"></a>이미지와 색

모든 이미지를 변경 해야 할 사용자의 언어 선택에 따라 합니다. 많은 아이콘이 나 사진 모든 사용자에 게 적합, 말하는 상대방 언어는 중요 하지 않습니다.
하지만 필드를 지역화 하는 데 맞지 일부 리소스와 같은:

 - 보여 주는 이미지 사용자나 특정 위치 – 앱 수 느껴집니다 사용자에 게 보다 적절 로컬 사용자/위치를 보여 줍니다.
 - 아이콘 –의 일부도 해 문화권별 수 있으며 로컬 이해를 사용 하 여 이미지를 지역화 하 여 쉽게 앱을 만들 수 있습니다.
 - 색 – 일부 문화권 이해 색 다르게 – 빨간색 한 영역을 하지만 다른 보시기 경고 의미할 수도 있습니다. 색을 지역화 하는 메커니즘을 구축 해야 하는지 여부를 확인 하려면 앱을 디자인할 때 모국어 확인 하십시오.


### <a name="videos-and-sound"></a>비디오 및 소리

비디오 및 사운드 있는 특별히 고려해 야 할 간편 하 게 번역 된 문자열을 얻을 수 있지만, 여러 음성 기록 추적 하기 때문에 응용 프로그램을 지역화할 때 또는 비디오 클립 비용이 많이 들고 어려울 수 있습니다.

비디오 및 사운드 파일의 여러 복사본 (특히 인 경우 많은 수의 언어에 지역화 하는 다 수의 미디어 파일) 응용 프로그램의 크기를 증가할 크게 수 있습니다. 또한 이렇게 하면 사용자 환경이 저하 속도가 느린 네트워크에서 사용자가 응용 프로그램을 설치한 후 언어 필요한 자산만 다운로드 하는 것이 좋습니다.

종종 여러 가지 방법으로 지역화 문제를 해결 하기 위해-가장 중요 한 점은 하 선불 고려해 야 하 고 응용 프로그램을 처리 하기 디자인 되었는지 확인 합니다.


### <a name="dates-times-numbers-and-currency"></a>날짜, 시간, 숫자 및 통화

.NET 형식 지정 함수를 사용 하는 경우 제대로 구문 분석 (및 throw 되는 변환 예외를 방지) 소수 구분 기호 있도록 문화권을 지정 해야 합니다. 예를 들어 1.99와 1,99은 로캘에 따라 유효한 10 진수 표시입니다.

데이터는 알려진된 원본에서 가져온 경우 (즉. 사용자 고유의 코드 또는 사용자가 제어 하는 웹 서비스에서) 하드 코딩 표준 영어 언어 서식 지정에 InvariantCulture 같은 서식을 일치 하는 문화권 식별자를 할 수 있습니다.

```csharp
double.Parse("1,999.99", CultureInfo.InvariantCulture);
```

데이터를 입력 하 여 응용 프로그램 사용자가 되는, 해당 로캘 반영 하는 CultureInfo 인스턴스를 사용 하 여 구문 분석 합니다.

```csharp
double.Parse("1 999,99", CultureInfo.CreateSpecificCulture("fr-FR"));
```

참조는 [숫자 문자열 구문 분석](http://msdn.microsoft.com/en-us/library/xbtzcc4w(v=vs.110).aspx) 및 [구문 분석 하는 날짜 및 시간 문자열](http://msdn.microsoft.com/en-us/library/2h3syy57(v=vs.110).aspx) 대 한 자세한 내용은 MSDN 문서.

<a name="rtl" />

### <a name="right-to-left-rtl-languages"></a>오른쪽에서 왼쪽으로 (오른쪽에서 왼쪽) 언어

예를 들어, 아랍어, 히브리어 및 우르두어 같은 일부 언어에서는 오른쪽에서 왼쪽으로 읽혀집니다.
이러한 언어를 지 원하는 응용 프로그램에는 오른쪽에서 왼쪽 판독기에 대 한 예를 들어 조정 하는 화면 디자인 사용 해야 합니다.

 - 텍스트가는 오른쪽 맞춤 이어야 합니다.
 - 입력된 필드의 오른쪽에 레이블이 표시 됩니다.
 - 기본 단추 배치 반대로 일반적으로 되어 있습니다.
 - 계층적 탐색 넘기기가 애니메이션 (및 기타 탐색 기능 및 애니메이션) 컨텍스트를 되돌릴 수 또한에 대 한 방향을 사용 하는 합니다.

IOS 및 Android에는 오른쪽에서 왼쪽 레이아웃 및 위의 조정 하는 데 도움이 되는 기본 제공 기능이 글꼴 렌더링을 지원 합니다. Xamarin.Forms 자동으로 현재 RTL 렌더링을 지원 하지 않습니다.

### <a name="sorting"></a>정렬

다른 언어 동일한 문자 집합을 사용할 때에 다르게 알파벳의 정렬 순서를 정의 합니다.

참조는 [문자열 비교 세부](http://msdn.microsoft.com/en-us/library/dd465121(v=vs.110).aspx#the_details_of_string_comparison) 에 [.NET Framework에서 문자열 사용에 대 한 유용한](http://msdn.microsoft.com/en-us/library/dd465121(v=vs.110).aspx) 언어 (CultureInfo) 정렬 순서를 적용 하는 위치는 예입니다.

그럴 가능성은 모바일 플랫폼에서 기본 제공 데이터베이스 기능 언어별 정렬 되므로 비즈니스 논리에 추가 코드를 구현 해야 할 수 있지만 순서 지정을 지원 합니다.

### <a name="text-search"></a>텍스트 검색

작성 하 고 염두에서에 여러 언어로 사용자 검색 알고리즘을 테스트할를 확인 합니다. 고려해 야 할 사항은 다음과 같습니다.

 - 자동 완성-자동 완성 기능을 빌드한 경우 사용자의 언어와 관련 된 제안을 원본을 확인 합니다.
 - – 데이터에 일치 하는 쿼리는 특정에 입력 한 쿼리를 검색 하는 언어는 해당 언어로 작성 된 정당한 콘텐츠에 대해 또는 응용 프로그램에서 모든 콘텐츠에 대해 실행할 수 있습니까?
 - 형태소 분석 – 검색 유사한 단어, 단어 루트 및 다른 검색 최적화를 검색 하는 기본 제공 되는 이러한 최적화를 지 원하는 모든 언어에 대해 작성 된?
 - – 정렬 (위 참조) 결과 올바르게 정렬 되었는지 확인 합니다.


### <a name="data-from-external-sources"></a>외부 원본에서 데이터

대부분의 응용 프로그램 Twitter에서 외부 원본의 데이터를 다운로드 하 고 날씨, 뉴스, 또는 주가 RSS 피드. 이 사용자에 게 표시할 때에 관련이 없는 또는 읽을 수 없는 정보 화면에 표시 됩니다 가능성을 고려해 야 합니다.

시도 하 고 응용 프로그램 사용자와 관련 된 데이터 표시 되는지 확인 하는 데는 몇 가지가 있습니다.

 - 다른 원본-응용 프로그램 사용자의 언어 또는 로캘에 따라 서로 다른 소스에서 데이터를 다운로드할 수 있습니다. 로캘 뉴스, 날씨 및 주식 가격 북미 피드에서 다운로드 한 것 보다 더 좋은 확인 수 있습니다.
 - 지역화 된 표시 – Twitter 또는 사진 피드를 표시 하는 경우 있습니다 표시할지 (수행 시간) 등의 메타 데이터 자신의 언어에서 자체 콘텐츠 원래 언어에 남아 있는 경우에 있습니다.
 - 번역 – 기계 번역 들어오는 데이터의 작업을 수행 하는 응용 프로그램으로 변환 옵션을 작성할 수 있습니다. 이 자동 또는 사용자의 재량 – 될이 수행 되 고, 이후 컴퓨터 번역 되는 경우 사용자에 게 알려야 합니다!

이 오디오 트랙에 대 한 외부 링크에는 영향을 줄 수 또는 콘텐츠 또는 콘텐츠에 표시 되지 것입니다 때 사용자는 사용자 인터페이스에서 알림을 적절 하 게 됩니다 확인 – 비디오 원본을 지정 하기 위해 미리 계획 해야 응용 프로그램을 디자인 하는 경우 변환의 언어입니다.


### <a name="dont-over-translate"></a>과도 하 게 변환 안 함

응용 프로그램의 일부 문자열을 변환할 필요 하거나 최소한의 변환기에 의해 특별 한 주의가 필요 없습니다. 예를 포함 될 수 있습니다.

 - Url-URL을 나열 하는 경우 그렇지 언어에 따라 조정 될 필요가 없습니다. 예를 들어 facebook.com 번역 것 자동 검색 언어는 주 사이트에 필요 하지 않습니다. 로캘 관련 내용이 다른 사이트 및 yahoo.com yahoo.fr 또는 yahoo.it와 같은 다른 URL을 제공 하는 것이 좋습니다.
 - 전화 번호-특히 다른 국가 코드 또는 특정 언어 호출자를 위한 숫자입니다.
 - 연락처 세부 정보 – 주소 및 기타 정보는 언어 또는 로캘 달라질 수 있습니다.
 - 상표 및 제품 이름 – 일부 문자열 같은 언어에서 항상 기록 하는 때문에 변환 하는 기능이 필요 하지 않습니다.

마지막으로, 특정 문자열 특수 하 게 처리 해야 하는 경우 변환기에 대 한 자세한 지침을 포함 해야 합니다.


### <a name="formatted-text"></a>서식 있는 텍스트

모바일 앱 사용 하지 않는 문제가 있으므로 문자열 일반적으로 다양 하 게 서식이 지정 되지 않습니다. 그러나 서식 있는 텍스트 (예: 굵게 또는 기울임꼴 서식을) 응용 프로그램에 필요한 경우 확인 방법을 서식을 입력으로 문자열 파일 보관 올바르게 한 사용자에 게 표시 하기 전에 올바르게 서식이 지정 변환기 알고 (ie. 주저 하지 마시기 바랍니다 실수로 자체 형식 지정 코드는 사용자에 게 수)입니다.



## <a name="translation-tips"></a>번역 팁

응용 프로그램에서 사용 되는 문자열을 번역 지역화 과정의 일부로 간주 됩니다. 일반적으로이 작업 번역 서비스로 아웃소싱를 응용 프로그램이 나 비즈니스 되는지 모를 수 있는 다국어 담당자가 수행 됩니다.

다음 팁은 정확 하 게 변환 하 고 따라서 지역화 된 응용 프로그램의 품질을 개선 하는 문자열을 생성 하는 데 도움이 됩니다.



### <a name="localize-complete-strings-not-words"></a>전체 문자열, 단어 안 함 지역화

경우에 따라 개발자가 응용 프로그램에 걸쳐에 다시 사용할 수 있도록 단일 단어 또는 문장 '조각'를 지정 하려는 방법을 사용 합니다. 예를 들어 텍스트에 대 한 "있는 5 개의 메시지입니다." 번역에 대 한 다음 문자열을 지정할 수 있습니다.

**잘못 된**:

```csharp
"You have"
"no"
"message"
"messages"
```

한 문자열 연결을 사용 하 여 코드에서 올바른 구에 즉석에서 만들려면 다음 시도:

**잘못 된**:

```csharp
"You have" + " " + numMsgs + " " + "messages"
"You have" + " no " + "messages"
```

**이 권장 되지** 모든 언어에 대해 작동 하지 않는 하 고 짧은 각 세그먼트의 컨텍스트를 이해 하는 변환기에 대 한 어려워지게 됩니다. 또한을 일으킬 수 있는 문제 나중에 각기 다른 컨텍스트에서 사용 (및 경우 업데이트 한 다음), 번역 된 문자열을 사용 하 여 다시 유발 합니다.


### <a name="allow-for-parameter-re-ordering"></a>매개 변수 다시 정렬에 대 한 허용

하지만 일부 프로그래밍 언어.NET 이미 개념 지원의 번호가 매겨진된 자리 표시자 이므로 문자열에서 매개 변수의 순서를 지정 하려면 추가 구문 필요

**좋은**:

```csharp
"a {0} b {1} cde {3}"
```

수 (여기서 자리 표시자의 순서와 위치 변경 됨) 다음 변환

```csharp
"{2} {3} f g h {0}"
```

및 토큰은 의도 한 변환기로 정렬 됩니다. 각 자리 표시자는 변환기에 문자열을 보낼 때 포함에 대 한 설명을 포함 해야 합니다.


### <a name="use-multiple-strings-for-cardinality"></a>여러 문자열을 사용 하 여 카디널리티

와 같은 문자열을 피해 야 `"You have {0} message/s."` 더 나은 사용자 환경을 제공 하기 위해 각 상태에 대 한 특정 문자열을 사용 하 여:

**좋은**:

```csharp
"You have no messages."
"You have 1 messages."
"You have 2 messages."
"You have {0} messages."
```

표시 되는 숫자를 평가 하는 응용 프로그램에서 코드를 작성 하 고 적절 한 문자열을 선택 해야 합니다. 일부 플랫폼 (iOS 및 Android 포함)에 현재 언어/로캘에서 대 한 기본 설정에 따라 최상의 복수형 문자열을 자동으로 선택 하도록 기본 제공 기능이 있습니다.


### <a name="allowing-for-gender"></a>성별에 대 한 허용

라틴 계열 언어는 종종 성별 주제에 따라 서로 다른 단어를 사용합니다. 응용 프로그램에서 인식 성별, 하는 경우이 반영 하기 위해 번역 된 문자열을 허용 해야 합니다.

영어, 여기서 문자열을 특정 사용자 또는 응용 프로그램의 사용자에 게 참조에 더욱 명확 하 게 경우도입니다. 메시지와 같은 일부 사이트를 표시 하는 예를 들어 `"Bob commented on his post"` 남성, female, 및 이진이 아님으로 또는 알 수 없는 성별 문자열이 필요 합니다.

**좋은**:

```csharp
"{0} commented on his post"
"{0} commented on her post"
"{0} commented on their post"
```

### <a name="dont-reuse-strings"></a>문자열을 다시 사용 안 함

또는 보다 정확 하 게 다시 사용 하지 마세요 문자열 방금 비슷하기 때문에 문자열 자체에 다른 용도로 또는 의미 합니다.

예: 응용 프로그램에 설정/해제 스위치 있고 스위치 컨트롤에 대 한 텍스트 'on' 및 'off' 지역화 해야 한다고 가정 합니다. 또한 표시할 있습니다 해당 설정의 값 다른 위치에서 텍스트 레이블에서 응용 프로그램에서. 스위치의 상태 (동일한 문자열 기본 언어의 경우에)-대 스위치 디스플레이 대 한 다른 문자열을 사용 하면 예:

-   "On" – 스위치 자체에 표시
-   "Off" – 스위치 자체에 표시
-   "On" – 레이블에 표시
-   "Off" – 레이블에 표시

변환기에 대 한 최대 유연성을 제공 합니다.

-   디자인 상의 이유로 아마도 자체 스위치 "on" 및 "off" 소문자를 사용 하지만 다음 레이블 표시 "On" 및 "Off" 대문자를 사용 합니다.
-   일부 언어 레이블에 표시 될 수 있습니다 (변환 된) 단어 자동 완성 하면서 사용자 인터페이스 컨트롤에 맞게 약식 스위치 값을 할 수 있습니다.
-   또는 일부 언어의 문화적 경험에 대 한 "I"와 "O"를 사용 하지만를 "On" 또는 "Off" 읽을 레이블을 계속 실행할 수 있습니다 스위치의 렌더링 될 수 있습니다.

<!--
# Testing

Once you’ve build and localized your app, you’ll want to be able to test. That means setting your emulator/simulator or device to use another locale or language.

> [!IMPORTANT]
> **WARNING:** Be careful when you set your device to a language you cannot read, as you may not be able to navigate the menu system to return it to your native language!


## iOS

Use Settings.app to switch the language and locale of the iOS Simulator or an iOS device.

On the iOS Simulator you can use the Reset Content and Settings menu item (if the device is in a foreign language and you can’t navigate back to your native tongue).

![]( "ios settings to change language")

## Android

To change the locale on a device

**Home > Menu > Settings > **

Then depending on Android version

**Locale & text > Select locale**

or

**Language & Input > Select language**

![]( "android settings to change language")

When you are testing on the emulator, you can navigate using the settings app as above, or you can reset the locale using the ADB tool command. Using Command Prompt on Windows or Terminal on OS X, start `adb shell` then send commands to set the emulator’s locale. **adb** can usually be found on the Mac in `/Users/YOURNAME/Library/Developer/Xamarin/android-sdk-mac_x86/platform-tools/adb`

### Spanish (Mexico)
setprop persist.sys.language es;setprop persist.sys.country MX;stop;sleep 5;start

### French (France)
setprop persist.sys.language fr;setprop persist.sys.country FR;stop;sleep 5;start

### Japanese (Japan)
setprop persist.sys.language ja;setprop persist.sys.country JP;stop;sleep 5;start

### Portuguese (Brazil)
setprop persist.sys.language pt;setprop persist.sys.country BR;stop;sleep 5;start

### English (USA)
setprop persist.sys.language en;setprop persist.sys.country US;stop;sleep 5;start

**TIP:** the default location of ADB on Mac OS X is
`/Users/[USERNAME]/Library/Developer/Xamarin/android-sdk-mac_x86/platform-tools/adb shell`

-->


### <a name="translation-services"></a>번역 서비스

#### <a name="machine-translation"></a>기계 번역

변환 기능에 앱을 빌드하려면 고려는 [Azure 변환기 텍스트 API](https://azure.microsoft.com/en-au/services/cognitive-services/translator-text-api/)합니다.

테스트 목적으로 개발 하는 동안 앱에서 일부 지역화 된 텍스트를 포함 하도록 많은 온라인 번역 도구 중 하나로 사용할 수 있습니다.

- [Bing 번역기](https://www.bing.com/translator/)
- [Google Translate](http://translate.google.com/)

다른 많은 사용할 수 있습니다. 품질 기계 번역을 일반적으로 없는 것으로 간주 응용 프로그램을 해제 하는 것으로 충분 하지 않고 검토 및 테스트 전문 변환기 또는 네이티브 스피커를 먼저 합니다.

 <!--Microsoft's Multilingual Application Toolkit helps you automatically translate strings, and is demonstrated with Xamarin.Forms in [this sample]().-->

#### <a name="professional-translation"></a>전문 번역

전문 번역 서비스 하는 문자열에 요금에 대 한 완성 된 번역을 제공 하는 자신의 변환기에 게 배포 됩니다.

가장 잘 알려진 서비스 중 하나는 [LionBridge](http://www.lionbridge.com/)합니다. 전문적인 서비스 모든는 일반적인 파일 형식은 문자열, XML, RESX 및 POT/PO를 포함 하 여 지원 합니다.


## <a name="summary"></a>요약

이 문서를 도입 된 일부의 개념을 앱 국제화 하 고 다음 리소스를 지역화 하기 전에 잘 알고 있어야 하 고 각 플랫폼에 대 한 언어 기본 설정을 변경 하는 방법에 대해서도 다룹니다.

Xamarin으로 사용할 수 있는 다양 한 플랫폼 및 플랫폼별 국제화 기술에 이러한 개념을 적용할 수 있습니다.

에 관심이 플랫폼에 대 한 기술 세부 정보를 읽는 계속:

- [Xamarin.Forms](~/xamarin-forms/app-fundamentals/localization.md) RESX 파일을 사용 하 여 플랫폼 간 지역화 합니다.
- [Xamarin.iOS](~/ios/app-fundamentals/localization/index.md) 네이티브 플랫폼 지역화 합니다.
- [Xamarin.Android](~/android/app-fundamentals/localization.md) 네이티브 플랫폼 지역화 합니다.



## <a name="related-links"></a>관련 링크

- [Apple의 지역화 개요](https://developer.apple.com/internationalization/)
- [Android의 지역화 검사 목록](http://developer.android.com/distribute/tools/localization-checklist.html)
- [지역화 대비 응용 프로그램 (MSDN)을 개발 하기 위한 모범 사례](http://msdn.microsoft.com/en-us/library/w7x1y988%28v=vs.90%29.aspx)