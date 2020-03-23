---
title: MSBuild cílová architektura a cílová platforma | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: df6517c5-edd6-4cc4-97ad-b3cdfc78e799
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3cccb9bb87d03d1fb285babe2a02cf30cfb9ed9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633197"
---
# <a name="msbuild-target-framework-and-target-platform"></a>MSBuild cílová architektura a cílová platforma

Projekt může být vytvořen tak, aby běžel na *cílovém frameworku*, což je určitá verze rozhraní .NET Framework, a *cílová platforma*, což je konkrétní softwarová architektura.  Můžete například cílit na aplikaci, která bude spuštěna na rozhraní .NET Framework 2.0 na 32bitové platformě, která je kompatibilní s rodinou procesorů 802x86 ("x86"). Kombinace cílového rámce a cílové platformy se označuje jako *cílový kontext*.

> [!IMPORTANT]
> Tento článek ukazuje starý způsob, jak určit cílový rámec. Projekty ve stylu sady SDK umožňují různé targetframeworky, jako je netstandard. Další informace naleznete v tématu [Target frameworks](/dotnet/standard/frameworks).

## <a name="target-framework-and-profile"></a>Cílový rámec a profil

 Cílová architektura je konkrétní verze rozhraní .NET Framework, na které je váš projekt vytvořen. Specifikace cílového rozhraní je vyžadována, protože umožňuje funkce kompilátoru a odkazy na sestavení, které jsou výhradní pro tuto verzi rozhraní.

 V současné době jsou k dispozici následující verze rozhraní .NET Framework:

- Rozhraní .NET Framework 2.0 (součástí sady Visual Studio 2005)

- Rozhraní .NET Framework 3.0 (součástí systému Windows Vista)

- Rozhraní .NET Framework 3.5 (součástí sady Visual Studio 2008)

- Rozhraní .NET Framework 4.5.2

- Rozhraní .NET Framework 4.6 (součástí sady Visual Studio 2015)

- .NET Framework 4.6.1

- Rozhraní .NET Framework 4.6.2

- Rozhraní .NET Framework 4.7

- Rozhraní .NET Framework 4.7.1

- Rozhraní .NET Framework 4.7.2

- Rozhraní .NET Framework 4.8

Verze rozhraní .NET Framework se liší od sebe navzájem v seznamu sestavení, které každý z nich zpřístupní k dispozici pro odkaz. Například nelze vytvořit aplikace Windows Presentation Foundation (WPF), pokud váš projekt cíle rozhraní .NET Framework verze 3.0 nebo vyšší.

Cílový rámec je určen `TargetFrameworkVersion` ve vlastnosti v souboru projektu. Cílovou architekturu projektu můžete změnit pomocí stránek vlastností projektu v integrovaném vývojovém prostředí sady Visual Studio (IDE). Další informace naleznete v [tématu How to: Target a version of the .NET Framework](../ide/visual-studio-multi-targeting-overview.md). Dostupné hodnoty `TargetFrameworkVersion` jsou `v2.0` `v3.0`, `v3.5` `v4.5.2`, `v4.6` `v4.6.1`, `v4.6.2` `v4.7`, `v4.7.1` `v4.7.2`, `v4.8`, , , , , a .

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
```

 *Cílový profil* je podmnožinou cílového rozhraní. Například profil klienta rozhraní .NET Framework 4 neobsahuje odkazy na sestavení MSBuild.

 > [!NOTE]
 > Cílové profily platí pouze pro [přenosné knihovny tříd](/dotnet/standard/cross-platform/cross-platform-development-with-the-portable-class-library).

 Cílový profil je určen `TargetFrameworkProfile` ve vlastnosti v souboru projektu. Cílový profil můžete změnit pomocí ovládacího prvku cílové ho rozhraní ve stránkách vlastností projektu v rozhraní IDE.

```xml
<TargetFrameworkVersion>v4.0</TargetFrameworkVersion>
<TargetFrameworkProfile>Client</TargetFrameworkProfile>
```

## <a name="target-platform"></a>Cílová platforma

 *Platforma* je kombinace hardwaru a softwaru, která definuje konkrétní runtime prostředí. Například:

- `x86`označuje 32bitový operační systém Windows, který je spuštěn na procesoru Intel 80x86 nebo jeho ekvivalentu.

- `x64`označuje 64bitový operační systém Windows, který je spuštěn na procesoru Intel x64 nebo ekvivalentním.

- `Xbox`označuje platformu Microsoft Xbox 360.

*Cílová platforma* je konkrétní platforma, na které je váš projekt vytvořen. Cílová platforma je `PlatformTarget` určena ve vlastnosti sestavení v souboru projektu. Cílovou platformu můžete změnit pomocí stránek vlastností projektu nebo **nástroje Configuration Manager** v ide.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
</PropertyGroup>

```

*Cílová konfigurace* je podmnožinou cílové platformy. Například `x86``Debug` konfigurace nezahrnuje většinu optimalizace kódu. Cílová konfigurace je `Configuration` určena ve vlastnosti sestavení v souboru projektu. Cílovou konfiguraci můžete změnit pomocí stránek vlastností projektu nebo **nástroje Configuration Manager**.

```xml
<PropertyGroup>
   <PlatformTarget>x86</PlatformTarget>
   <Configuration>Debug</Configuration>
<PropertyGroup>

```

## <a name="see-also"></a>Viz také

- [Multicílení](../msbuild/msbuild-multitargeting-overview.md)
