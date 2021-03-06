---
title: 'Xamarin.Essentials: SMS'
description: Xamarin.Essentials의 SMS 클래스를 사용하면 응용 프로그램이 기본 SMS 응용 프로그램에서 수신자에게 보내도록 지정된 메시지를 열 수 있습니다.
ms.assetid: 81A757F2-6F2A-458F-B9BE-770ADEBFAB58
author: jamesmontemagno
ms.author: jamont
ms.date: 11/04/2018
ms.openlocfilehash: d0655f3e687750e0fca626fb017096a946c0abb3
ms.sourcegitcommit: 01f93a34b466f8d4043cef68fab9b35cd8decee6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/05/2018
ms.locfileid: "52898773"
---
# <a name="xamarinessentials-sms"></a>Xamarin.Essentials: SMS

**Sms** 클래스를 사용하면 응용 프로그램이 기본 SMS 응용 프로그램에서 수신자에게 보내도록 지정된 메시지를 열 수 있습니다.

## <a name="get-started"></a>시작

[!include[](~/essentials/includes/get-started.md)]

## <a name="using-sms"></a>Sms 사용

클래스에서 Xamarin.Essentials에 대한 참조를 추가합니다.

```csharp
using Xamarin.Essentials;
```

SMS 기능은 메시지의 수신자와 메시지 본문이 포함된 `SmsMessage`에 대해 `ComposeAsync` 메서드를 호출하여 작동합니다.

```csharp
public class SmsTest
{
    public async Task SendSms(string messageText, string recipient)
    {
        try
        {
            var message = new SmsMessage(messageText, recipient);
            await Sms.ComposeAsync(message);
        }
        catch (FeatureNotSupportedException ex)
        {
            // Sms is not supported on this device.
        }
        catch (Exception ex)
        {
            // Other error has occurred.
        }
    }
}
```

또한 여러 명의 수신자를 `SmsMessage`에 전달할 수 있습니다.

```csharp
public class SmsTest
{
    public async Task SendSms(string messageText, string[] recipients)
    {
        try
        {
            var message = new SmsMessage(messageText, recipients);
            await Sms.ComposeAsync(message);
        }
        catch (FeatureNotSupportedException ex)
        {
            // Sms is not supported on this device.
        }
        catch (Exception ex)
        {
            // Other error has occurred.
        }
    }
}
```

## <a name="api"></a>API

- [Sms 소스 코드](https://github.com/xamarin/Essentials/tree/master/Xamarin.Essentials/Sms)
- [Sms API 문서](xref:Xamarin.Essentials.Sms)
