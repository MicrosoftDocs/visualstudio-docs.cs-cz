---
title: Přehled XAML
description: Seznamte se se základními informacemi o jazyce XAML a editorem kódu XAML a Návrhář XAML nástroji v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.openlocfilehash: 6f315573b24989e6ad3a3d451de372430b72f70f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99931189"
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

## <a name="xaml-code-editor"></a>Editor kódu XAML

[Editor kódu XAML](xaml-code-editor.md) v integrovaném vývojovém prostředí sady Visual Studio obsahuje všechny nástroje, které potřebujete k vytváření aplikací WPF a UWP pro platformu Windows a pro Xamarin. Forms. A i když rozhraní IDE (integrované vývojové prostředí) v aplikaci Visual Studio má mnoho funkcí, které můžete použít k vývoji aplikací pro jiné platformy, má také některé funkce, které jsou jedinečné pouze v jazyce XAML.

## <a name="xaml-designer"></a>Návrhář XAML

Visual Studio a Blend pro Visual Studio poskytují [Návrhář XAML](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) , které vám pomůžou sestavovat uživatelská rozhraní (UI) pro aplikace WPF, UWP a Xamarin. Forms. Ovládací prvky lze přetáhnout z okna sada nástrojů nebo assets a nastavit vlastnosti v okno Vlastnosti. Když to uděláte, Visual Studio a Blend pro Visual Studio vytvoří odpovídající kód XAML. Pokud dáváte přednost úpravám kódu XAML přímo, můžete to provést také.

## <a name="whats-new"></a>Novinky

Nejnovější informace najdete v následujících zdrojích informací:

- **[Vylepšení nástrojů jazyka XAML v rámci sady Visual Studio 2019 verze 16,7 Preview 1](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** Blogový příspěvek
- Příspěvek na blogu k **[novinkám v jazyce XAML Developer Tools v aplikaci Visual Studio 2019](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)**
- **[Nové funkce XAML v aplikaci Visual Studio](https://youtu.be/yI9OyA4ZM2E)** video na YouTube

## <a name="see-also"></a>Viz také

- [XAML v aplikacích WPF](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [XAML v aplikacích pro UWP](/windows/uwp/xaml-platform/xaml-overview)
- [XAML v aplikacích Xamarin. Forms](/xamarin/xamarin-forms/xaml/)
