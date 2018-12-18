---
title: Aktualizuje existující aplikaci na MSBuild 15 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology: msbuild
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4da159ae0fcb4347052efcea5d0dbd24d5ccd8f1
ms.sourcegitcommit: d462dd10746624ad139f1db04edd501e7737d51e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50219234"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizace existující aplikace pro MSBuild 15

Ve verzích nástroje MSBuild před 15.0 nástroje MSBuild byl načten z globální mezipaměti sestavení (GAC) a rozšíření nástroje MSBuild byly nainstalovány v registru. To, že jsou splněné všechny aplikace používá stejnou verzi nástroje MSBuild a měl přístup ke stejné sady nástrojů IP adresu, ale vedle sebe instalace různých verzí sady Visual Studio.

Kvůli podpoře rychlejší a menší a vedle sebe instalace sady Visual Studio 2017 už umístí MSBuild v mezipaměti GAC nebo upraví registru. Bohužel to znamená, že aplikace, které chcete použít rozhraní API nástroje MSBuild k vyhodnocování nebo sestavení projektů nelze implicitně spoléhat na instalaci sady Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Použití nástroje MSBuild v sadě Visual Studio

K zajištění, že programový sestavení z aplikace odpovídá sestavení v sadě Visual Studio nebo *MSBuild.exe*načíst sestavení nástroje MSBuild v sadě Visual Studio a používat sady SDK k dispozici v sadě Visual Studio. Balíček Microsoft.Build.Locator NuGet zjednodušuje tento proces.

## <a name="use-microsoftbuildlocator"></a>Použití Microsoft.Build.Locator

Pokud redistribuujete *Microsoft.Build.Locator.dll* s vaší aplikací, nebudete muset distribuovat jiná sestavení nástroje MSBuild.

Aktualizuje se projekt pro použití nástroje MSBuild 15 a Lokátor rozhraní API vyžaduje několik změn ve vašem projektu, je popsáno níže. Chcete-li zobrazit příklad změny muset aplikaci aktualizovat projekt, naleznete v tématu [potvrzení změn provedených příklad projektu v úložišti MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Změnit MSBuild reference

Pokud chcete mít jistotu, že nástroj MSBuild načítá z centrálního umístění, nesmí distribuovat jeho sestavení s vaší aplikací.

Mechanismus pro změnu projektu nástroje MSBuild předejít z centrálního umístění závisí na způsobu odkazujete MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Použití balíčků NuGet (upřednostňováno)

Tyto pokyny předpokládají, že používáte [odkazy na NuGet PackageReference – vizuální styl](https://docs.microsoft.com/nuget/consume-packages/package-references-in-project-files).

Změňte soubory projektu MSBuild sestavení odkazovat z balíčků NuGet. Zadejte `ExcludeAssets=runtime` NuGet říct, že sestavení jsou potřeba pouze v době sestavení a by neměl být zkopírován do výstupního adresáře.

Hlavní a dílčí verzi nástroje MSBuild balíčků musí být menší než nebo rovna hodnotě minimální verze sady Visual Studio, které chcete podporovat. Pokud chcete podporovat všechny verze sady Visual Studio 2017, verze balíčku odkazují `15.1.548`.

Například můžete použít tohoto XML kódu:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Použití rozšíření sestavení

Pokud nemůžete použít balíčky NuGet, můžete odkazovat na sestavení nástroje MSBuild, které jsou distribuovány pomocí sady Visual Studio. Pokud odkazujete MSBuild přímo, ujistěte se, že se nebude zkopírovat do výstupního adresáře tak, že nastavíte `Copy Local` k `False`. V souboru projektu toto nastavení bude vypadat jako v následujícím kódu:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Přesměrování vazby

Odkaz na balíček Microsoft.Build.Locator zajistit, že vaše aplikace automaticky používá požadované vazby přesměruje všech verzí sestavení nástroje MSBuild na verzi `15.1.0.0`.

### <a name="ensure-output-is-clean"></a>Ujistěte se, že je vyčistit výstup

Sestavte projekt a zkontrolujte výstupní adresář, abyste měli jistotu, že neobsahuje žádné *Microsoft.Build\*. Knihovna DLL* sestavení jiný než *Microsoft.Build.Locator.dll*přidali v dalším kroku.

### <a name="add-package-reference"></a>Přidání odkazu na balíček

Přidat odkaz na balíček NuGet do [Microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.0.7-preview-ge60d679b53</Version>
    </PackageReference>
```

### <a name="register-instance-before-calling-msbuild"></a>Zaregistrovat instanci před voláním funkce MSBuild

Přidejte volání do rozhraní API pro Lokátor před voláním jakékoli metody, která používá nástroj MSBuild.

Nejjednodušší způsob, jak přidat volání rozhraní API pro Lokátor je přidání volání

```csharp
MSBuildLocator.RegisterDefaults();
```

v kódu při spuštění aplikace.

Pokud chcete řídit citlivější načítání MSBuild, můžete vybrat výsledek `MSBuildLocator.QueryVisualStudioInstances()` předat `MSBuildLocator.RegisterInstance()` ručně, ale to není obvykle potřeba.
