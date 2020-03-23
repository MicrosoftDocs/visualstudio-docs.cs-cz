---
title: Aktualizace existující aplikace na MSBuild 15 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d4e7d84768307964b495e8c5e97e7731b0622a1
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75597136"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizace existující aplikace pro MSBuild 15

Ve verzích MSBuild před 15.0 byl MSBuild načten z globální mezipaměti sestavení (GAC) a rozšíření MSBuild byla nainstalována v registru. To zajistilo, že všechny aplikace používaly stejnou verzi nástroje MSBuild a měly přístup ke stejným sadám nástrojů, ale zabránily souběžným instalacím různých verzí sady Visual Studio.

Pro podporu rychlejší, menší a vedle sebe instalace Visual Studio 2017 a novější verze již umístit MSBuild v GAC nebo upravuje registru. Bohužel to znamená, že aplikace, které chtějí používat rozhraní MSBuild API k vyhodnocení nebo sestavení projektů, nemohou implicitně spoléhat na instalaci sady Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Použití msbuildu z visual studia

Chcete-li zajistit, aby programová sestavení z vašich sestavení shody aplikací byla provedena v rámci sady Visual Studio nebo *MSBuild.exe*, načtěte sestavení MSBuild z sady Visual Studio a použijte sady SDK, které jsou k dispozici v sadě Visual Studio. Balíček Microsoft.Build.Locator NuGet tento proces zjednodušuje.

## <a name="use-microsoftbuildlocator"></a>Použití microsoft.build.locator

Pokud redistribuujete *microsoft.Build.Locator.dll* s vaší aplikací, nebudete muset distribuovat další sestavení MSBuild.

Aktualizace projektu pro použití MSBuild 15 a rozhraní API lokátoru vyžaduje několik změn v projektu, popsané níže. Příklad změn potřebných k aktualizaci projektu naleznete [v tématu potvrzení provedená v ukázkovém projektu v úložišti MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Změna odkazů MSBuild

Chcete-li se ujistit, že MSBuild zatížení z centrálního umístění, nesmíte distribuovat jeho sestavení s aplikací.

Mechanismus pro změnu projektu, aby se zabránilo načítání MSBuild z centrálního umístění závisí na tom, jak odkazovat MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Použití balíčků NuGet (upřednostňované)

Tyto pokyny předpokládají, že používáte [odkazy NuGet ve stylu PackageReference](/nuget/consume-packages/package-references-in-project-files).

Změňte soubory projektu tak, aby odkazovaly na sestavení MSBuild z jejich balíčků NuGet. Zadejte, chcete-li `ExcludeAssets=runtime` sdělit NuGet, že sestavení jsou potřeba pouze v době sestavení a neměly by být zkopírovány do výstupního adresáře.

Hlavní a dílčí verze balíčků MSBuild musí být menší nebo rovna minimální verzi sady Visual Studio, kterou chcete podporovat. Například pokud chcete podporovat Visual Studio 2017 a novější `15.1.548`verze, odkaz na verzi balíčku .

Můžete například použít tento xml:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Použití rozšiřujících sestav

Pokud nelze použít balíčky NuGet, můžete odkazovat na sestavení MSBuild, které jsou distribuovány s Visual Studio. Pokud odkazujete přímo na MSBuild, ujistěte se, že nebude `Copy Local` `False`zkopírován do výstupního adresáře nastavením na . V souboru projektu bude toto nastavení vypadat jako následující kód:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Přesměrování vazeb

Odkazem na Microsoft.Build.Locator balíček a ujistěte se, že vaše aplikace automaticky používá požadované přesměrování vazby na verzi 15.1.0.0. Vazba přesměruje na tuto verzi podporují MSBuild 15 a MSBuild 16.

### <a name="ensure-output-is-clean"></a>Ujistěte se, že výstup je čistý

Sestavte projekt a zkontrolujte výstupní adresář a ujistěte se, že neobsahuje žádné *Microsoft.Build.\*. V* dalším kroku byla přidána jiná sestavení dll než *Microsoft.Build.Locator.dll*.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Přidání odkazu na balíček pro microsoft.Build.Locator

Přidejte odkaz na balíček NuGet pro [microsoft.Build.Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Nezadávejte `ExcludeAssets=runtime` pro balíček Microsoft.Build.Locator.

### <a name="register-instance-before-calling-msbuild"></a>Registrovat instanci před voláním MSBuild

Přidejte volání rozhraní API lokátoru před voláním libovolné metody, která používá MSBuild.

Nejjednodušší způsob, jak přidat volání do rozhraní API lokátoru, je přidat volání do

```csharp
MSBuildLocator.RegisterDefaults();
```

v kódu spuštění aplikace.

Pokud chcete jemnější odstupňovanou kontrolu nad zatížení MSBuild, můžete `MSBuildLocator.QueryVisualStudioInstances()` vybrat výsledek `MSBuildLocator.RegisterInstance()` předat ručně, ale to obecně není potřeba.
