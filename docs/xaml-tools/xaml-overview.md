---
title: Přehled XAML
ms.date: 07/31/2019
ms.topic: reference
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: af6ef98c5bffc4563cfa8fc8e0b29a910aeb85e8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72601871"
---
# <a name="overview-of-xaml"></a>Přehled jazyka XAML

Jazyk Extensible Application Markup Language (XAML) (XAML) je deklarativní jazyk založený na formátu XML. Jazyk XAML je často používán v následujících typech aplikací k sestavení uživatelských rozhraní:

- [Aplikace Windows Presentation Foundation (WPF)](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Aplikace Univerzální platforma Windows (UWP)](/windows/uwp/xaml-platform/xaml-overview)
- [Aplikace Xamarin. Forms](/xamarin/xamarin-forms/xaml/)

Následující kód XAML definuje ovládací prvek jednoduchého tlačítka.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML se používá také k definování pracovních postupů v [aplikacích technologie Windows Workflow Foundation (WF)](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml).

## <a name="xaml-designer"></a>Návrhář XAML

Visual Studio a Blend pro Visual Studio poskytují Návrhář XAML, které vám pomůžou sestavovat uživatelská rozhraní (UI) pro aplikace WPF, UWP a Xamarin. Forms. Ovládací prvky lze přetáhnout z okna sada nástrojů nebo assets a nastavit vlastnosti v okno Vlastnosti. Při provádění těchto akcí aplikace Visual Studio a Blend pro Visual Studio vytvoří odpovídající kód XAML. Pokud dáváte přednost úpravám kódu XAML přímo, můžete to provést také.

Články v této dokumentaci popisují Návrhář XAML v sadě Visual Studio a Blend pro Visual Studio.

## <a name="see-also"></a>Viz také:

- [XAML v aplikacích WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML v aplikacích pro UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML v aplikacích Xamarin. Forms](/xamarin/xamarin-forms/xaml/)