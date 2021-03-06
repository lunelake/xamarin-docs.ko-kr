---
title: Spinner
ms.prod: xamarin
ms.assetid: 004089E9-7C1D-2285-765A-B69143091F2A
ms.technology: xamarin-android
author: conceptdev
ms.author: crdun
ms.date: 02/06/2018
ms.openlocfilehash: 90b4755cdb4b8248c2b731d070d720076d4dda40
ms.sourcegitcommit: e268fd44422d0bbc7c944a678e2cc633a0493122
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50102999"
---
# <a name="spinner"></a>Spinner

[`Spinner`](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 항목을 선택 하기 위한 드롭다운 목록을 제공 하는 위젯이입니다. 이 가이드에는 뒤에 선택된 된 항목을 사용 하 여 관련 된 다른 값을 표시 하는 수정 하는 회전자의 선택 항목의 목록을 표시 하는 간단한 앱을 만드는 방법을 설명 합니다.

## <a name="basic-spinner"></a>기본 회전자

이 자습서의 첫 번째 부분에서는 행성 목록을 표시 하는 간단한 회전자 위젯을 만들어야 합니다. 행성을 선택 하면 알림 메시지는 선택한 항목을 표시 합니다.

[![HelloSpinner 앱의 예제 스크린샷](spinner-images/01-example-screenshots-sml.png)](spinner-images/01-example-screenshots.png#lightbox)

명명 된 새 프로젝트를 시작 **HelloSpinner**합니다.

오픈 **Resources/Layout/Main.axml** 다음 XML을 삽입 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical"
    android:padding="10dip"
    android:layout_width="fill_parent"
    android:layout_height="wrap_content">
    <TextView
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="10dip"
        android:text="@string/planet_prompt"
    />
    <Spinner
        android:id="@+id/spinner"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:prompt="@string/planet_prompt"
    />
</LinearLayout>
```

에 [ `TextView` ](https://developer.xamarin.com/api/type/Android.Widget.TextView/)의 `android:text` 특성 및 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/)의 `android:prompt` 특성 모두 동일한 문자열 리소스를 참조 합니다. 이 텍스트는 위젯의 제목으로 동작합니다. 적용할 때 합니다 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/), 위젯을 선택 시 나타나는 선택 대화 상자에 표시할 제목 텍스트를 표시 됩니다.

편집할 **Resources/Values/Strings.xml** 와 같이 파일을 수정 합니다.

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
  <string name="app_name">HelloSpinner</string>
  <string name="planet_prompt">Choose a planet</string>
  <string-array name="planets_array">
    <item>Mercury</item>
    <item>Venus</item>
    <item>Earth</item>
    <item>Mars</item>
    <item>Jupiter</item>
    <item>Saturn</item>
    <item>Uranus</item>
    <item>Neptune</item>
  </string-array>
</resources>
```

두 번째 `<string>` 요소에서 참조 하는 제목 문자열을 정의 합니다 [ `TextView` ](https://developer.xamarin.com/api/type/Android.Widget.TextView/) 및 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 위의 레이아웃 합니다.
합니다 `<string-array>` 요소에 목록으로 표시 되는 문자열의 목록을 정의 합니다 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 위젯.

이제 열 **MainActivity.cs** 추가한 다음 `using` 문:

```csharp
using System;
```

다음으로, 다음 코드를 삽입 합니다 [`OnCreate()`](https://developer.xamarin.com/api/member/Android.App.Activity.OnCreate/(Android.OS.Bundle))
방법:

```csharp
protected override void OnCreate (Bundle bundle)
{
    base.OnCreate (bundle);

    // Set our view from the "Main" layout resource
    SetContentView (Resource.Layout.Main);

    Spinner spinner = FindViewById<Spinner> (Resource.Id.spinner);

    spinner.ItemSelected += new EventHandler<AdapterView.ItemSelectedEventArgs> (spinner_ItemSelected);
    var adapter = ArrayAdapter.CreateFromResource (
            this, Resource.Array.planets_array, Android.Resource.Layout.SimpleSpinnerItem);

    adapter.SetDropDownViewResource (Android.Resource.Layout.SimpleSpinnerDropDownItem);
    spinner.Adapter = adapter;
}
```

후 합니다 `Main.axml` 레이아웃 콘텐츠 보기로 설정 되어 합니다 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 위젯을 사용 하 여 레이아웃에서 캡처된 [ `FindViewById<>(int)` ](https://developer.xamarin.com/api/member/Android.App.Activity.FindViewById/p/System.Int32/)합니다.
는 [`CreateFromResource()`](https://developer.xamarin.com/api/member/Android.Widget.ArrayAdapter.CreateFromResource/p/Android.Content.Context/System.Int32/System.Int32/)
메서드는 다음 새로 만들고 [ `ArrayAdapter` ](https://developer.xamarin.com/api/type/Android.Widget.ArrayAdapter/), 각 항목에 대 한 초기 모양 문자열 배열에 바인딩하는 합니다 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 는 이어서 각 항목 선택 하면 스핀 상자에 표시 되는 방식 . 합니다 `Resource.Array.planets_array` ID 참조가 합니다 `string-array` 위에 정의 된 및 `Android.Resource.Layout.SimpleSpinnerItem` ID 플랫폼에 의해 정의 된 표준 회전자 모양, 레이아웃을 참조 합니다.
[`SetDropDownViewResource`](https://developer.xamarin.com/api/member/Android.Widget.ArrayAdapter.SetDropDownViewResource/p/System.Int32/)
위젯을 열릴 때 각 항목에 대 한 모양을 정의 하 라고 합니다. 마지막으로, 합니다 [ `ArrayAdapter` ](https://developer.xamarin.com/api/type/Android.Widget.ArrayAdapter/) 를 사용 하 여 해당 항목의 모든 연결로 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 설정 하 여는 [ `Adapter` ](https://developer.xamarin.com/api/type/Android.Widget.ArrayAdapter) 속성입니다.

이제 항목에서 선택 하는 경우 응용 프로그램을 notifys는 콜백 메서드를 제공 합니다 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/)합니다. 이 메서드가 모양을 다음과 같습니다.

```csharp
private void spinner_ItemSelected (object sender, AdapterView.ItemSelectedEventArgs e)
{
    Spinner spinner = (Spinner)sender;
    string toast = string.Format ("The planet is {0}", spinner.GetItemAtPosition (e.Position));
    Toast.MakeText (this, toast, ToastLength.Long).Show ();
}
```

보낸 사람에 게로 캐스팅 되는 항목을 선택 하면를 [ `Spinner` ](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 항목에 액세스할 수 있도록 합니다. 사용 하 여는 `Position` 속성에는 `ItemEventArgs`, 선택한 개체의 텍스트 찾아 표시 하는 데 사용할 수 있습니다를 [ `Toast` ](https://developer.xamarin.com/api/type/Android.Widget.Toast/)합니다.

응용 프로그램 실행 다음과 같이 표시 됩니다.

[![전 세계적으로 선택 하는 Mars 사용 하 여 회전자의 스크린샷 예제](spinner-images/02-basic-example-sml.png)](spinner-images/02-basic-example.png#lightbox)

## <a name="spinner-using-keyvalue-pairs"></a>키/값 쌍을 사용 하 여 회전자

사용 하는 데 필요한 경우가 `Spinner` 일종의 앱에서 사용 되는 데이터를 사용 하 여 연결 된 키 값을 표시 합니다. 때문에 `Spinner` 작동 하지 않습니다 키/값 쌍을 사용 하 여 직접 키/값 쌍을 개별적으로 저장, 채우는 해야는 `Spinner` 키 값을 사용 하 여를 사용 하 여 회전자에서 선택된 된 키의 위치 관련된 데이터 값을 조회 합니다. 

다음 단계에는 **HelloSpinner** 선택한 행성에 대 한 평균 온도 표시 하도록 앱을 수정 하는:

다음을 추가 합니다 `using` 문을 **MainActivity.cs**:

```csharp
using System.Collections.Generic;
```

다음 인스턴스 변수를 추가 합니다 `MainActivity` 클래스입니다.
이 목록에 행성 및 해당 평균 온도 대 한 키/값 쌍 유지 합니다.

```csharp
private List<KeyValuePair<string, string>> planets;
```

에 `OnCreate` 메서드를 앞에 다음 코드를 추가 `adapter` 선언 됩니다.

```csharp
planets = new List<KeyValuePair<string, string>>
{
    new KeyValuePair<string, string>("Mercury", "167 degrees C"),
    new KeyValuePair<string, string>("Venus", "464 degrees C"),
    new KeyValuePair<string, string>("Earth", "15 degrees C"),
    new KeyValuePair<string, string>("Mars", "-65 degrees C"),
    new KeyValuePair<string, string>("Jupiter" , "-110 degrees C"),
    new KeyValuePair<string, string>("Saturn", "-140 degrees C"),
    new KeyValuePair<string, string>("Uranus", "-195 degrees C"),
    new KeyValuePair<string, string>("Neptune", "-200 degrees C")
};
```

이 코드는 행성 및 해당 관련된 평균 온도 대 한 간단한 저장소를 만듭니다. (실제 앱에서는 데이터베이스 일반적으로 키와 연결 된 데이터를 저장 합니다.)

위 코드 바로 다음 키를 추출 하 고 순서로 목록에 다음 줄을 추가 합니다.

```csharp
List<string> planetNames = new List<string>();
foreach (var item in planets)
    planetNames.Add (item.Key);
```

이 목록에 전달 된 `ArrayAdapter` 생성자 (대신는 `planets_array` 리소스):

```csharp
var adapter = new ArrayAdapter<string>(this,
    Android.Resource.Layout.SimpleSpinnerItem, planetNames);
```

수정 `spinner_ItemSelected` 선택한 위치에 연결 된 전 세계적으로 선택한 (온도) 값을 찾는 사용 되도록 합니다.

```csharp
private void spinner_ItemSelected(object sender, AdapterView.ItemSelectedEventArgs e)
{
    Spinner spinner = (Spinner)sender;
    string toast = string.Format("The mean temperature for planet {0} is {1}",
        spinner.GetItemAtPosition(e.Position), planets[e.Position].Value);
    Toast.MakeText(this, toast, ToastLength.Long).Show();
}
```

응용 프로그램 실행 알림에이 같습니다.

[![온도 표시 하는 전 세계 선택의 예](spinner-images/03-keyvalue-example-sml.png)](spinner-images/03-keyvalue-example.png#lightbox)
   
  

## <a name="resources"></a>자료

-   [`Resource.Layout`](https://developer.xamarin.com/api/type/Android.Resource+Layout/) 
-   [`ArrayAdapter`](https://developer.xamarin.com/api/type/Android.Widget.ArrayAdapter/) 
-   [`Spinner`](https://developer.xamarin.com/api/type/Android.Widget.Spinner/) 

*이 페이지의 일부는 생성 하 고 Android Open Source Project에서 공유 된 조건에 따라 사용 되는 작업에 따라 수정 합니다*
[*Creative Commons 2.5 Attribution License* ](http://creativecommons.org/licenses/by/2.5/).
