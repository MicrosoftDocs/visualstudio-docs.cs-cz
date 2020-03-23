---
title: Projekty s více cíleními
description: Tento dokument poskytuje přehled o tom, jak nastavit víceúčelové projekty v Sadě Visual Studio pro Mac.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/20/2020
ms.locfileid: "75451438"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projekty s více cílovými rámci
V sadě Visual Studio for Mac můžete nakonfigurovat projekt Xamarin nebo .NET Core tak, aby běžel na libovolné z několika verzí rozhraní .NET Framework a na libovolné z několika systémových platforem. Můžete například cílit na projekt, který by se měl spouštět v rozhraní .NET Framework 4.6 i .NET Core 3.1. 

Další informace o cílových architekturách naleznete [v tématu Target Frameworks](/dotnet/standard/frameworks).

> [!NOTE] 
> Toto téma se týká Visual Studia pro Mac. Visual Studio v systému Windows najdete v [tématu Přehled cílení na rozhraní .](/visualstudio/ide/visual-studio-multi-targeting-overview)

## <a name="targeting-multiple-frameworks"></a>Cílení na více architektur

Cílové architektury jsou určeny v souboru projektu, který můžete upravit kliknutím pravým tlačítkem myši na projekt a výběrem příkazu **Nástroje > Upravit soubor.** Pokud je zadán jeden cílový rámec, použijte targetframework element. Následující soubor projektu konzoly aplikace ukazuje, jak cílit na rozhraní .NET Core 3.0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Použijte plurální TargetFrameworks prvek s více cílové architektury:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Další informace o tom, jak [cílit na více architektur](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Práce s kódem v projektu s více cíli
Při úpravách souboru Jazyka C# v projektu s více cílovými rámci můžete určit, které cílové rozhraní, které chcete použít k vedení prostředí editoru (například zobrazení upozornění, pokud používáte rozhraní API, které není podporováno tímto rámcem). Cílovou architekturu můžete změnit pomocí voliče **cílové architektury** v levém horním rohu okna editoru.

![Použití voliče cílové ho rozhraní ke změně cílového rozhraní, který se nachází v horní části okna editoru](media/project-multitargeting-framework-selector.png)

Někdy je třeba volat různá api v závislosti na platformě, na kterou vaše aplikace cílí. Chcete-li to provést, můžete napsat podmíněný kód pro kompilaci kódu pro konkrétní platformu:

```C#
public class MyClass
{
    static void Main()
    {
#if NET40
        Console.WriteLine("Target framework: .NET Framework 4.0");
#elif NET45  
        Console.WriteLine("Target framework: .NET Framework 4.5");
#else
        Console.WriteLine("Target framework: .NET Standard 1.4");
#endif
    }
}
```

Při psaní kódu se zobrazí upozornění v návrzích automatického dokončování technologie IntelliSense, které vás upozorní, pokud pro některý z cílových rámců, které vaše aplikace podporuje, chybí konkrétní rozhraní API.

![Varovná zpráva zobrazená v aplikaci IntelliSense, rozhraní API nebude fungovat pro zadaný cílový rámec. Příklad textu: obor názvů System.Buffers, SharedUtils (netstandard2.0) - Není k dispozici. K přepínání kontextu můžete použít navigační panel.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Viz také

- [Přehled cílení na architekturu (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Cílové architektury v projektech ve stylu Sady SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
