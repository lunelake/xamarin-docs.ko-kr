---
title: 1장. XAML 시작하기
description: Xamarin.Forms 응용 프로그램에서 XAML 페이지 및 코드 숨김 파일을와 함께 작동 visual 내용을 정의 주로 사용 됩니다.
ms.prod: xamarin
ms.assetid: 9073FA0E-BD5A-4492-8A93-54C466F6EDB9
ms.technology: xamarin-forms
author: davidbritch
ms.author: dabritch
ms.date: 05/10/2018
ms.openlocfilehash: 086ed765781d9297f07574519d2cbc9cf93ac4dd
ms.sourcegitcommit: be6f6a8f77679bb9675077ed25b5d2c753580b74
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059550"
---
# <a name="part-1-getting-started-with-xaml"></a>1장. XAML 시작하기

[![샘플 다운로드](~/media/shared/download.png) 샘플 다운로드](https://developer.xamarin.com/samples/xamarin-forms/XamlSamples/)

_Xamarin.Forms 응용 프로그램에서 XAML은 주로 페이지의 시각적 내용 및 C# 코드 숨김 파일을 함께 정의할 때 사용됩니다._

코드 숨김 파일은 태그에 대한 코드 지원을 제공합니다. 해당 두 파일은 모두 자식 뷰 및 속성 초기화를 포함하는 새 클래스 정의에 영향을 줍니다. XAML 파일에서 클래스 및 속성은 XML 요소 및 특성과 함께 참조되고, 태그와 코드 간 연결이 설정됩니다.

## <a name="creating-the-solution"></a>솔루션 만들기

첫 번째 XAML 파일을 편집 하려면 새 Xamarin.Forms 솔루션을 만들려면 Visual Studio 또는 Mac 용 Visual Studio를 사용 합니다. (사용자 환경에 해당 하는 아래에 있는 탭을 선택 합니다.)

# <a name="visual-studiotabwindows"></a>[Visual Studio](#tab/windows)

Windows를 선택 하려면 Visual Studio 사용 **파일 > 새로 만들기 > 프로젝트** 합니다. 에 **새 프로젝트** 대화 상자에서 **Visual C# > 플랫폼 간** 왼쪽 차례로 **Mobile 앱 (Xamarin.Forms)** 가운데 있는 목록에서.

![](get-started-with-xaml-images/win/newprojectdialog.w157.png "새 프로젝트 대화 상자")

솔루션에 대한 위치를 선택하고, 이름을 **XamlSamples**(또는 선호하는 이름)로 입력하고 **확인**을 누릅니다.

다음 화면에서 **Blank** 템플릿 및 **.NET Standard** 코드 공유 전략을 선택합니다.

![](get-started-with-xaml-images/win/newcrossplatformapp.png "새 앱 대화 상자")

**확인**을 누릅니다.

4 개의 프로젝트가 솔루션에 생성 됩니다: 합니다 **XamlSamples** .NET Standard 라이브러리 **XamlSamples.Android**를 **XamlSamples.iOS**, 및 유니버설 Windows 플랫폼 솔루션 **XamlSamples.UWP**합니다.

# <a name="visual-studio-for-mactabmacos"></a>[Visual Studio for Mac](#tab/macos)

Mac 용 Visual Studio에서 선택 **파일 > 새 솔루션** 합니다. 에 **새 프로젝트** 대화 상자에서 **다중 플랫폼 > 앱** 왼쪽 및 **빈 Forms 앱** (*되지* **Forms 앱** ) 템플릿 목록에서:

![](get-started-with-xaml-images/mac/newprojectdialog1.png "새 프로젝트 대화 상자 1")

**다음**을 누릅니다.

다음의 대화 상자에서 앱 이름에 **XamlSamples**(또는 선호하는 이름)를 입력합니다. **.NET Standard 사용** 라디오 단추가 선택되었는지 확인합니다.

![](get-started-with-xaml-images/mac/newprojectdialog2.png "새 프로젝트 대화 상자 2")

**다음**을 누릅니다.

다음의 대화 상자에서 프로젝트 위치를 선택할 수 있습니다.

![](get-started-with-xaml-images/mac/newprojectdialog3.png "새 프로젝트 대화 상자 3")

**만들기**를 누릅니다.

세 개의 프로젝트를 솔루션에 생성 됩니다: 합니다 **XamlSamples** .NET Standard 라이브러리 **XamlSamples.Android**, 및 **XamlSamples.iOS**합니다.

-----

**XamlSamples** 솔루션 생성 후에 다양한 플랫폼 프로젝트를 솔루션 시작 프로젝트로 선택하고, 프로젝트 템플릿으로 생성된 간단한 응용 프로그램을 폰 에뮬레이터나 실제 장치에 빌드 및 배포하여 자신의 개발 환경을 테스트할 수도 있습니다.

플랫폼 특정 코드를 작성할 필요가 없는 경우, 사용자는 거의 대부분의 프로그래밍 시간을 공유된 **XamlSamples** .NET Standard 라이브러리 프로젝트에 할애하게 됩니다. 이 문서는 공유 프로젝트 이외의 내용은 다루지 않을 것입니다.

### <a name="anatomy-of-a-xaml-file"></a>XAML 파일의 분석

**XamlSamples** .NET Standard 라이브러리 내에는 다음과 같은 이름을 가진 파일 쌍이 있습니다.

- **App.xaml**: XAML 파일
- **App.xaml.cs**: XAML 파일과 연결된 C# *코드 숨김* 파일

코드 숨김 파일을 보려면 **App.xaml** 옆에 있는 화살표를 클릭해야 합니다.

둘 다 **App.xaml** 하 고 **App.xaml.cs** 라는 클래스에 기여 `App` 에서 파생 되는 `Application`합니다. XAML 파일을 사용 하 여 다른 대부분의 클래스에서 파생 된 클래스를 적용할 `ContentPage`; 파일과 XAML를 사용 하 여 전체 페이지의 시각적 콘텐츠를 정의 합니다. 경우 다른 두 파일을 **XamlSamples** 프로젝트:

- **MainPage.xaml**: XAML 파일
- **MainPage.xaml.cs**: C# 코드 숨김 파일

**MainPage.xaml** 파일은 다음과 같습니다(하지만 형태가 약간 다를 수 있습니다).

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             xmlns:local="clr-namespace:XamlSamples"
             x:Class="XamlSamples.MainPage">

    <StackLayout>
        <!-- Place new controls here -->
        <Label Text="Welcome to Xamarin Forms!"
               VerticalOptions="Center"
               HorizontalOptions="Center" />
    </StackLayout>

</ContentPage>
```

두 XML 네임 스페이스 ( `xmlns`) 선언 Xamarin 웹 사이트에서 보이는 첫 번째 및 microsoft의 두 번째 Uri 참조입니다. 궁금증에 해당 Uri 지점을 확인 합니다. 아무 것도 없는 합니다. Xamarin 및 Microsoft에서 소유 하는 Uri 하기만 하면 되며 기본적으로 버전 식별자로 작동 합니다.

첫 번째 XML 네임 스페이스 선언은 Xamarin.Forms에서 접두사가 없는 클래스 참조를 갖는 XAML 파일 내의 정의된 태그, 예를 들면 `ContentPage`와 같은 태그를 의미합니다. 두 번째 네임 스페이스 선언은 `x`의 접두사를 정의합니다. 이는 XAML 자체에 내장된 몇 가지 요소와 특성 및 XAML의 다른 구현이 지원되는 곳에서 사용됩니다. 그러나 이러한 요소와 특성은 URI에 포함된 연도에 따라 약간 다릅니다. Xamarin.Forms는 전체가 아니라 2009 XAML 사양을 지원합니다.

`local` 네임 스페이스 선언은 .NET Standard 라이브러리 프로젝트에서 다른 클래스에 접근할 수 있도록 해줍니다.

첫 번째 태그의 끝에서 `x` 접두사는 `Class`라는 특성으로 사용됩니다. 이 `x`와 같은 접두사는 XAML 네임 스페이스에서 거의 보편적이므로 `Class`와 같은 XAML 특성은 거의 항상 `x:Class`와 같이 참조됩니다.

`x:Class` 특성은 `XamlSamples` 네임 스페이스에 있는 `MainPage` 클래스를 완전히 정규화된 .NET 클래스 이름으로 지정합니다. 즉, 이 XAML 파일은 `XamlSamples` 네임 스페이스에 있는 `x:Class` 특성이 표시된 태그 `ContentPage`에서 파생된 `MainPage`라는 새 클래스를 정의합니다.

`x:Class` 특성은 C# 클래스에서 파생되었음을 정의하기 위해 XAML 파일의 루트 요소에만 나타날 수 있습니다. 이것은 XAML 파일에 정의된 새 클래스입니다. XAML 파일에 표시되는 그 밖의 모든 항목은 단순히 기존 클래스에서 인스턴스화되고 초기화하는 용도로 사용됩니다.

**MainPage.xaml.cs** 파일은 다음과 같습니다(사용하지 않는 `using` 지시문은 제외됨).

```csharp
using Xamarin.Forms;

namespace XamlSamples
{
    public partial class MainPage : ContentPage
    {
        public MainPage()
        {
            InitializeComponent();
        }
    }
}
```

`MainPage` 클래스는 `ContentPage`에서 파생되지만 `partial` 클래스 정의를 주목하십시오. 이는 `MainPage`에 대해 다른 partial 클래스 정의가 있을 것이라는 것을 암시하지만, 어디에 있을까요? 그리고 `InitializeComponent` 메서드는 무엇일까요?

Visual Studio 프로젝트가 빌드될 때 생성 하려면 XAML 파일 구문 분석을 C# 코드 파일. 확인 합니다 **XamlSamples\XamlSamples\obj\Debug** 디렉터리 라는 파일을 찾을 수 있습니다 **XamlSamples.MainPage.xaml.g.cs**합니다. 'G'는 생성을 나타냅니다. 이 다른 partial 클래스 정의입니다 `MainPage` 의 정의 포함 하는 `InitializeComponent` 에서 호출 된 메서드는 `MainPage` 생성자입니다. 이러한 두 부분 `MainPage` 클래스 정의 함께 컴파일될 수 있습니다. 여부는 XAML 컴파일 여부에 따라 XAML 파일이 나 XAML 파일의 이진 형식 실행 파일에 포함 됩니다.

런타임에 호출 하 여 특정 플랫폼 프로젝트에서에서 코드를 `LoadApplication` 의 새 인스턴스를 전달 하는 메서드를 `App` .NET 표준 라이브러리의 클래스입니다. 합니다 `App` 클래스 생성자를 인스턴스화합니다 `MainPage`합니다. 해당 클래스의 생성자를 호출 `InitializeComponent`를 호출 합니다 `LoadFromXaml` .NET Standard 라이브러리에서 XAML 파일 (또는 해당 컴파일된 이진 파일)를 추출 하는 메서드. `LoadFromXaml` XAML 파일에 정의 된 모든 개체를 초기화, 부모-자식 관계에서 모두 함께 연결 하, XAML 파일에서 설정 하는 이벤트에는 코드에 정의 된 이벤트 처리기를 연결 및 개체의 결과 트리 페이지의 내용으로 설정 합니다.

일반적으로 생성된 코드 파일에 많은 시간을 투자할 필요는 없지만, 종종 생성된 파일의 코드에서 런타임 예외가 발생하므로 친숙해질 필요가 있습니다.

이 프로그램을 컴파일하고 실행하는 경우, `Label` 요소는 다음 XAML에서 알 수 있듯이 페이지의 가운데에 나타납니다.

[![](get-started-with-xaml-images/xamlsamples.png "기본 Xamarin.Forms 디스플레이")](get-started-with-xaml-images/xamlsamples-large.png#lightbox "기본 Xamarin.Forms 표시")

시각적인 것에 더 관심이 있다면 XAML에 더 관심을 갖기만 하면 됩니다.

## <a name="adding-new-xaml-pages"></a>새 XAML 페이지 추가

# <a name="visual-studiotabwindows"></a>[Visual Studio](#tab/windows)

다른 XAML 기반 추가할 `ContentPage` 프로젝트에 클래스를 선택 합니다 **XamlSamples** .NET Standard 라이브러리 프로젝트 및 호출를 **프로젝트 > 새 항목 추가** 메뉴 항목입니다. 왼쪽에 있는 합니다 **새 항목 추가** 대화 상자에서 **시각적 C#**  및 **Xamarin.Forms**. 목록에서 선택 **콘텐츠 페이지** (되지 **콘텐츠 페이지 (C#)**, 코드 전용 페이지를 만듭니다.는 또는 **콘텐츠 뷰**, 페이지 없는). 예를 들어 페이지에 이름을 지정 **HelloXamlPage.xaml**:

![](get-started-with-xaml-images/win/addnewitemdialog.w157.png "새 항목 추가 대화 상자")

# <a name="visual-studio-for-mactabmacos"></a>[Visual Studio for Mac](#tab/macos)

다른 XAML 기반 추가할 `ContentPage` 프로젝트에 클래스를 선택 합니다 **XamlSamples** .NET Standard 라이브러리 프로젝트 및 호출를 **파일 > 새 파일** 메뉴 항목입니다. 왼쪽에는 **새 파일** 대화 상자에서 **Forms** 왼쪽 및 **Forms ContentPage Xaml** (되지 **Forms ContentPage**는 코드 전용 페이지를 만듭니다. 또는 **콘텐츠 뷰**, 페이지 없는). 예를 들어 페이지에 이름을 지정 **HelloXamlPage**:

![](get-started-with-xaml-images/mac/newfiledialog.png "새 파일 대화 상자")

-----

**HelloXamlPage.xaml** 및 **HelloXamlPage.xaml.cs** 코드 숨김 파일, 이렇게 두 파일이 프로젝트에 추가됩니다.

## <a name="setting-page-content"></a>페이지 콘텐츠 설정

**HelloXamlPage.xaml** 파일 편집에는 다음과 같이 오직 `ContentPage` 및 `ContentPage.Content` 태그만 있으면 됩니다.

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.HelloXamlPage">
    <ContentPage.Content>

    </ContentPage.Content>
</ContentPage>
```

`ContentPage.Content` 태그는 XAML의 고유한 구문 중 일부입니다. 처음에는 유효하지 않은 XML로 표시될 수 있지만, 태그는 적합합니다. 마침표는 XML에서 특수 문자가 아닙니다.

`ContentPage.Content` 태그는 *속성 요소* 태그라고 합니다. `Content`는 `ContentPage`의 속성이고, 일반적으로 단일 뷰나 자식 뷰가 있는 레이아웃으로 설정합니다. 일반적으로 속성은 XAML에서 특성이 되지만, `Content` 특성은 복잡한 개체로 설정하는 것이 어렵습니다. 이런 이유로 속성은 클래스 이름과 마침표로 구분된 속성 이름으로 이루어진 XML 요소로 표현 됩니다. 이제 `Content` 속성은 다음과 같이 `ContentPage.Content` 태그 사이에 설정할 수 있습니다.

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.HelloXamlPage"
             Title="Hello XAML Page">
    <ContentPage.Content>

        <Label Text="Hello, XAML!"
               VerticalOptions="Center"
               HorizontalTextAlignment="Center"
               Rotation="-15"
               IsVisible="true"
               FontSize="Large"
               FontAttributes="Bold"
               TextColor="Blue" />

    </ContentPage.Content>
</ContentPage>
```

또한 `Title` 특성이 루트 태그에 설정되었다는 것에 주의하십시오.

이때 클래스, 속성 및 XML 간의 관계 분명해 집니다:는 Xamarin.Forms 클래스 (같은 `ContentPage` 또는 `Label`) XML 요소에 XAML 파일에 표시 됩니다. 해당 클래스의 속성-포함 `Title` 온 `ContentPage` 7의 속성과 `Label`-일반적으로 XML 특성으로 표시 합니다.

대부분의 바로 가기는 이러한 속성의 값을 설정하기 위해 존재합니다. 일부 속성은 기본 데이터 유형이 있으며, 예를 들어 `Title` 및 `Text` 속성의 유형은 `String`이고, `Rotation` 속성의 유형은 `Double`이며, `IsVisible`의 유형은 `Boolean`(기본적으로 `true`이며 여기서는 오직 설명 용도로 설정됨)입니다.

`HorizontalTextAlignment` 속성은 열거형인 `TextAlignment` 유형입니다. 모든 열거형 유형 속성에는 멤버 이름만 제공하면 됩니다.

그러나 변환기는 더 복잡한 유형의 속성에 대하여 구문 분석에 XAML을 사용합니다. 변환기는 `TypeConverter`에서 파생되는 Xamarin.Forms의 클래스입니다. 대부분이 공용(public) 클래스이지만 몇몇은 아닙니다. 해당 특정 XAML 파일에 대해 다음과 같은 몇 가지 변환기 클래스가 배후에서 작동합니다.

-  `LayoutOptionsConverter` 에 대 한는 `VerticalOptions` 속성
-  `FontSizeConverter` 에 대 한는 `FontSize` 속성
-  `ColorTypeConverter` 에 대 한는 `TextColor` 속성

이러한 변환기는 속성 설정의 허용 구문을 제어합니다.

`ThicknessTypeConverter`는 한 개, 쉼표로 구분된 두 개, 또는 네 개의 숫자를 처리할 수 있습니다. 1개의 숫자를 제공하면 네 면 모두에 적용됩니다. 2개의 숫자이면 첫 번째는 왼쪽 및 오른쪽의 안쪽 여백이며, 두 번째는 위쪽 및 아래쪽입니다. 4개의 숫자이면 순서대로 왼쪽, 위쪽, 오른쪽 및 아래쪽입니다.

`LayoutOptionsConverter`는 `LayoutOptions` 유형의 값에 대한 `LayoutOptions` 구조체의 공용(public) 정적(static) 필드 이름을 변환할 수 있습니다.

`FontSizeConverter`는 `NamedSize` 멤버 또는 숫자 글꼴 크기를 제어할 수 있습니다.

`ColorTypeConverter`는 `Color` 구조체 또는 알파 채널이 있거나 없는 숫자 기호(#)가 앞에 붙은 16 진수 RGB 값의 공용 정적 필드의 이름을 받습니다. 알파 채널이 없는 구문은 다음과 같습니다.

 `TextColor="#rrggbb"`

각 작은 문자는 16진수입니다. 알파 채널 포함 방법은 다음과 같습니다.

 `TextColor="#aarrggbb">`

알파 채널의 FF는 완전히 불투명이고 00은 완전히 투명하다는 것을 기억해 둡니다.

다른 두 가지 형식을 사용하면 다음과 같이 각 채널에 대한 단일 16진수만을 지정할 수 있습니다.

 `TextColor="#rgb"` `TextColor="#argb"`

이러한 경우, 숫자는 값을 구성하도록 반복됩니다. 예를 들어, #CF3는 RGB 색 CC-FF-33입니다.

## <a name="page-navigation"></a>페이지 탐색

**XamlSamples** 프로그램을 실행하면 `MainPage`가 표시 됩니다. 새 `HelloXamlPage`를 보기 위해서는 **App.xaml.cs** 파일에서 새 시작 페이지로 설정하거나 또는 `MainPage`에서 새 페이지로 탐색(navigation)을 합니다.

탐색을 구현하려면 먼저 **App.xaml.cs** 생성자에서 `NavigationPage` 개체를 생성하도록 코드를 변경해야 합니다.

```csharp
public App()
{
    InitializeComponent();
    MainPage = new NavigationPage(new MainPage());
}
```

**MainPage.xaml.cs** 생성자에서 다음과 같이 간단한 `Button` 하나를 추가하고 `HelloXamlPage`로 이동하는 이벤트 처리기를 사용할 수 있습니다.

```csharp
public MainPage()
{
    InitializeComponent();

    Button button = new Button
    {
        Text = "Navigate!",
        HorizontalOptions = LayoutOptions.Center,
        VerticalOptions = LayoutOptions.Center
    };

    button.Clicked += async (sender, args) =>
    {
        await Navigation.PushAsync(new HelloXamlPage());
    };

    Content = button;
}
```

페이지의 `Content` 속성을 설정하면 XAML 파일의 `Content` 속성을 대체하게 됩니다. 해당 프로그램의 새 버전을 컴파일하고 배포하면 단추가 화면에 나타납니다. 단추를 눌러 `HelloXamlPage`로 이동합니다. IPhone, Android 및 UWP 결과 페이지는 다음과 같습니다.

[![](get-started-with-xaml-images/helloxaml1.png "레이블 텍스트를 회전")](get-started-with-xaml-images/helloxaml1-large.png#lightbox "레이블 텍스트를 회전 합니다.")

다시 탐색할 수 있습니다 `MainPage` 를 사용 하 여는 **< 다시** iOS, android에서 휴대폰의 맨 아래 또는 페이지의 맨 위에 있는 왼쪽된 화살표를 사용 하 여 또는 왼쪽된 화살표를 사용 하 여 Windows 10에서 페이지의 맨 위에 있는 단추입니다.

`Label` 표시를 위해 다양한 방법의 XAML 연습을 자유롭게 해 봅니다. 텍스트에 유니코드 문자를 포함하는 경우 표준 XML 구문을 사용할 수 있습니다. 예를 들어, 다음과 같이 인사말에 지능형 따옴표를 삽입합니다.

 `<Label Text="&#x201C;Hello, XAML!&#x201D;" … />`

해당 모양은 다음과 같습니다.

[![](get-started-with-xaml-images/helloxaml2.png "유니코드 문자를 사용 하 여 레이블 텍스트를 회전")](get-started-with-xaml-images/helloxaml2-large.png#lightbox "유니코드 문자를 사용 하 여 레이블 텍스트를 회전 합니다.")

## <a name="xaml-and-code-interactions"></a>XAML 및 코드 상호 작용

합니다 **HelloXamlPage** 샘플 하나만 포함 되어 있습니다. `Label` 페이지의 있지만 매우 일반적인 것은 아닙니다. 대부분의 `ContentPage` 파생형 집합 합니다 `Content` 와 같은 속성의 일부 레이아웃에 정렬를 `StackLayout`입니다. `Children` 의 속성을 `StackLayout` 형식으로 정의 됩니다 `IList<View>` 형식의 개체가 실제로 이지만 `ElementCollection<View>`, 여러 뷰 또는 다른 레이아웃을 사용 하 여 컬렉션을 채울 수 있습니다 하 고 합니다. XAML에서 이러한 부모-자식 관계는 일반 XML 계층 구조를 사용 하 여 설정 됩니다. 라는 새 페이지에 대 한 XAML 파일을 다음과 같습니다 **XamlPlusCodePage**:

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.XamlPlusCodePage"
             Title="XAML + Code Page">
    <StackLayout>
        <Slider VerticalOptions="CenterAndExpand" />

        <Label Text="A simple Label"
               Font="Large"
               HorizontalOptions="Center"
               VerticalOptions="CenterAndExpand" />

        <Button Text="Click Me!"
                HorizontalOptions="Center"
                VerticalOptions="CenterAndExpand" />
    </StackLayout>
</ContentPage>
```

이 XAML 파일은 구문상으로 완전하며 다음과 같이 표시됩니다.

[![](get-started-with-xaml-images/xamlpluscode1.png "페이지의 여러 컨트롤")](get-started-with-xaml-images/xamlpluscode1-large.png#lightbox "페이지의 여러 컨트롤")

그러나 이 프로그램이 기능적으로 결함이 있다고 생각할 수 있습니다. `Slider`는 `Label`에 현재 값을 표시하고, `Button`은 프로그램 내에서 어떤 작업을 수행할 가능성이 있슴니다.

살펴보겠지만 [4 부입니다. 데이터 바인딩 기본 사항](~/xamarin-forms/xaml/xaml-basics/data-binding-basics.md)를 표시 하는 작업을 `Slider` 사용 하 여 값을 `Label` 데이터 바인딩을 사용 하 여 XAML에서 완전히 처리할 수 있습니다. 하지만 코드 솔루션을 먼저 참조 하는 것이 유용 합니다. 이 경우에 처리 합니다 `Button` 클릭 코드를 반드시 있어야 합니다. 즉, 코드 숨김 파일에 대 한 `XamlPlusCodePage` 에 대 한 처리기를 포함 해야 합니다는 `ValueChanged` 의 이벤트를 `Slider` 및 `Clicked` 의 이벤트는 `Button`합니다. 이러한 파일을 추가 해 보겠습니다.

```csharp
namespace XamlSamples
{
    public partial class XamlPlusCodePage
    {
        public XamlPlusCodePage()
        {
            InitializeComponent();
        }

        void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
        {

        }

        void OnButtonClicked(object sender, EventArgs args)
        {

        }
    }
}
```

해당 이벤트 처리기들은 공용(public)일 필요가 없습니다.

XAML 파일로 돌아가서, `Slider` 및 `Button` 태그는 다음과 같이 해당 처리기를 참조하는 `ValueChanged` 및 `Clicked` 이벤트를 포함해야 합니다.

```xaml
<ContentPage xmlns="http://xamarin.com/schemas/2014/forms"
             xmlns:x="http://schemas.microsoft.com/winfx/2009/xaml"
             x:Class="XamlSamples.XamlPlusCodePage"
             Title="XAML + Code Page">
    <StackLayout>
        <Slider VerticalOptions="CenterAndExpand"
                ValueChanged="OnSliderValueChanged" />

        <Label Text="A simple Label"
               Font="Large"
               HorizontalOptions="Center"
               VerticalOptions="CenterAndExpand" />

        <Button Text="Click Me!"
                HorizontalOptions="Center"
                VerticalOptions="CenterAndExpand"
                Clicked="OnButtonClicked" />
    </StackLayout>
</ContentPage>
```

처리기를 이벤트에 할당하는 것은 속성에 값을 할당하는 것과 동일한 구문이라는 것을 알 수 있습니다.

`Slider`의 `ValueChanged` 이벤트에 대한 처리기가 현재 값 표시를 위해 `Label`을 사용할 것이라면 처리기는 코드에서 해당 개체를 참조해야 합니다. `Label`은 `x:Name` 특성을 사용하여 지정하는 이름이 필요합니다.

```xaml
<Label x:Name="valueLabel"
       Text="A simple Label"
       Font="Large"
       HorizontalOptions="Center"
       VerticalOptions="CenterAndExpand" />
```

`x:Name` 특성의 `x` 접두사는 특성이 XAML에 고유하다는 것을 나타냅니다.

`x:Name` 특성에 할당한 이름은 C# 변수 이름과 동일한 규칙입니다. 예를 들어, 문자 또는 밑줄로 시작해야 하고 공백을 포함하면 안됩니다.

이제 `ValueChanged` 이벤트 처리기는 새 `Slider` 값 표시를 위해 `Label`을 설정할 수 있습니다. 새 값은 다음과 같이 이벤트 인수에서 사용할 수 있습니다.

```csharp
void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
{
    valueLabel.Text = args.NewValue.ToString("F3");
}
```

또는, 처리기는 다음과 같이 `sender` 인수에서 해당 이벤트를 생성하는 `Slider` 개체를 가져와서 `Value` 속성을 얻을 수 있습니다.

```csharp
void OnSliderValueChanged(object sender, ValueChangedEventArgs args)
{
    valueLabel.Text = ((Slider)sender).Value.ToString("F3");
}
```

프로그램을 처음 실행하면, `ValueChanged` 이벤트가 아직 실행되지 않았기 때문에 `Label`에 `Slider` 값이 표시되지 않습니다. 하지만 다음과 같이 `Slider`를 조정하기만 하면 값이 표시됩니다.

[![](get-started-with-xaml-images/xamlpluscode2.png "슬라이더 값 표시")](get-started-with-xaml-images/xamlpluscode2-large.png#lightbox "슬라이더 값 표시")

이제는 `Button` 차례입니다. 버튼의 `Text`를 사용하여 경고를 표시하도록 `Clicked` 이벤트 응답을 시연해 보겠습니다. 이벤트 처리기는 다음과 같이 `sender` 인수를 `Button`으로 안전하게 변환한 다음 해당 속성에 접근할 수 있습니다.

```csharp
async void OnButtonClicked(object sender, EventArgs args)
{
    Button button = (Button)sender;
    await DisplayAlert("Clicked!",
        "The button labeled '" + button.Text + "' has been clicked",
        "OK");
}
```

위 메서드는 `DisplayAlert` 메서드가 비동기적으로 수행되므로 메서드가 완료될 때 반환하는 `await` 연산자로 시작하기 때문에 `async`로 정의합니다. 이 메서드는 `sender` 인수에서 이벤트를 발생시키는 `Button`을 얻으므로 동일한 처리기를 여러 단추에 사용할 수 있습니다.

XAML에 정의된 개체 코드 숨김 파일에서 처리되는 이벤트를 발생시키고 코드 숨김 파일은 `x:Name` 특성과 함께 할당된 이름을 사용하여 XAML에 정의된 개체에 접근할 수 있음을 확인했습니다. 이것은 코드 및 XAML이 상호 작용하는 두 가지 기본 방법입니다.

이제 지역(private) 필드인 모든 `x:Name`으로 할당된 모든 이름을 포함하는 새로 생성된 **XamlPlusCode.xaml.g.cs 파일**을 검토하여 XAML 작동 방식에 대한 몇 가지 추가 정보를 얻을 수 있습니다. 해당 파일의 단순화된 버전은 다음과 같습니다.

```csharp
public partial class XamlPlusCodePage : ContentPage {

    private Label valueLabel;

    private void InitializeComponent() {
        this.LoadFromXaml(typeof(XamlPlusCodePage));
        valueLabel = this.FindByName<Label>("valueLabel");
    }
}
```

이 필드를 선언하면 해당 관할권 지역의 `XamlPlusCodePage` 부분(partial) 클래스 파일에서 변수를 자유롭게 사용할 수 있습니다. 런타임 시 필드는 XAML이 구문 분석된 후 할당됩니다. 즉, `XamlPlusCodePage` 생성자가 시작되고 `InitializeComponent`가 호출된 후 유효하지 않으면 `valueLabel` 필드는 `null`이 됩니다.

`InitializeComponent`가 생성자에게 다시 컨트롤을 반환한 후에, 페이지의 비주얼은 마치 컨트롤이 코드에서 인스턴스화 및 초기화된 것처럼 구성되었습니다. XAML 파일은 더 이상 클래스에서 어떤 역할을 수행하지 않습니다. 예를 들어, `StackLayout`에 뷰를 추가하거나 페이지의 `Content` 속성을 완전히 다른 것으로 설정하는 등 원하는 방식으로 페이지에서 해당 개체를 조작할 수 있습니다. 페이지의 `Content` 속성과 레이아웃의 `Children` 컬렉션에 있는 항목을 검사하여 '트리를 돌아다닐' 수 있습니다. 이러한 방식으로 접근되는 뷰 속성을 설정하거나 이벤트 처리기를 동적으로 할당할 수 있습니다.

자유롭습니다. 페이지는 사용자의 것이고 XAML은 페이지 내용을 만들기 위한 유일한 도구입니다.

## <a name="summary"></a>요약

이 소개를 사용 하 여 클래스 정의를 XAML 파일과 코드 파일을 제공 하는 방법 및 XAML 및 코드 파일이 상호 작용 하는 방법을 살펴보았습니다. 하지만 XAML도 자체 고유 구문는 기능이 매우 유연한 방식으로 사용할 수 있도록 합니다. 이러한 탐색을 시작할 수 있습니다 [2 부입니다. 필수 XAML 구문](~/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax.md)합니다.



## <a name="related-links"></a>관련 링크

- [Xaml 샘플](https://developer.xamarin.com/samples/xamarin-forms/XamlSamples/)
- [2부. 필수 XAML 구문](~/xamarin-forms/xaml/xaml-basics/essential-xaml-syntax.md)
- [3부. XAML 태그 확장](~/xamarin-forms/xaml/xaml-basics/xaml-markup-extensions.md)
- [4부. 데이터 바인딩 기본 사항](~/xamarin-forms/xaml/xaml-basics/data-binding-basics.md)
- [5부. MVVM에 데이터 바인딩](~/xamarin-forms/xaml/xaml-basics/data-bindings-to-mvvm.md)
