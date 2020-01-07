---
title: Projekty s více cíli
description: Tento dokument poskytuje přehled o tom, jak v Visual Studio pro Mac nastavit cílené projekty.
ms.topic: overview
author: jmatthiesen
ms.author: jomatthi
ms.date: 12/12/2019
ms.assetid: 2a561af4-f1fe-493e-9a53-aa6d77d15498
ms.openlocfilehash: 3d1372ab5bd08ce164352293ec9d341ca567e3d5
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75451438"
---
# <a name="projects-with-multiple-target-frameworks"></a>Projekty s více cílovými rozhraními
V Visual Studio pro Mac můžete nakonfigurovat projekt Xamarin nebo .NET Core tak, aby běžel na některé z několika verzí .NET Framework a na některé z několika systémových platforem. Můžete například cílit projekt tak, aby běžel jak v .NET Framework 4,6, tak v rozhraní .NET Core 3,1. 

Další informace o cílových rozhraních naleznete v tématu [cílová rozhraní](/dotnet/standard/frameworks).

> [!NOTE] 
> Toto téma se týká Visual Studio pro Mac. Informace o aplikaci Visual Studio ve Windows najdete v tématu věnovaném [přehledu cílení na rozhraní](/visualstudio/ide/visual-studio-multi-targeting-overview).

## <a name="targeting-multiple-frameworks"></a>Cílení na více platforem

Cílové architektury jsou zadány v souboru projektu, který lze upravit kliknutím pravým tlačítkem myši na projekt a výběrem příkazu **nástroje > upravit soubor** . Pokud je určena jedna cílová architektura, použijte element TargetFramework. Následující soubor projektu konzolové aplikace ukazuje, jak cílit na .NET Core 3,0:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
  </PropertyGroup>

</Project>
```

Použijte element plural TargetFrameworks s více cílovými rozhraními:

```XML
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFrameworks>netstandard1.4;net40;net45</TargetFrameworks>
  </PropertyGroup>
```

Přečtěte si další informace o tom, jak [cílit na více platforem](/dotnet/standard/frameworks#how-to-specify-target-frameworks).

## <a name="working-with-code-in-a-multi-target-project"></a>Práce s kódem v projektu s více cíli
Pokud upravujete C# soubor v projektu s více cílovými rozhraními, můžete určit cílovou architekturu, kterou chcete použít k nastavení prostředí editoru (například zobrazení upozornění, pokud použijete rozhraní API, které není podporováno touto architekturou). Cílové rozhraní můžete změnit pomocí selektoru **cílového rozhraní** v levém horním rohu okna editoru.

![Použití selektoru cílového rozhraní pro změnu cílové architektury, která se nachází v horní části okna editoru](media/project-multitargeting-framework-selector.png)

Někdy je třeba volat různá rozhraní API v závislosti na platformě, na kterou cílí vaše aplikace. K tomu můžete napsat podmíněný kód pro zkompilování kódu pro konkrétní platformu:

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

Při psaní kódu se zobrazí upozornění v návrzích automatického dokončování technologie IntelliSense, které vám umožní zjistit, jestli v žádné z cílových rozhraní, které vaše aplikace podporuje, chybí specifická rozhraní API.

![Varovná zpráva zobrazená v IntelliSense, rozhraní API nebude pro zadanou cílovou architekturu fungovat. Příklad textu: obor názvů System. buffers, SharedUtils (netstandard 2.0) – není k dispozici. K přepnutí kontextu lze použít navigační panel.](media/project-multitargeting-intellisense-warnings.png)

## <a name="see-also"></a>Viz také:

- [Přehled cílení na rozhraní (Windows)](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [Cílová rozhraní v projektech ve stylu sady SDK](/dotnet/standard/frameworks#how-to-specify-target-frameworks)
