---
title: Aktualizace existující aplikace na MSBuild 15 | Microsoft Docs
description: Zjistěte, jak zajistit, aby se programová sestavení z vaší aplikace shodovala s sestaveními provedenými v sadě Visual Studio nebo MSBuild.exe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bd7f47466074536c9088840e726f768f62f9346b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99965925"
---
# <a name="update-an-existing-application-for-msbuild-15"></a>Aktualizace existující aplikace pro MSBuild 15

Ve verzích MSBuild starších než 15,0 byl nástroj MSBuild načten z globální mezipaměti sestavení (GAC) a rozšíření nástroje MSBuild byla nainstalována do registru. To zajišťuje, aby všechny aplikace používaly stejnou verzi nástroje MSBuild a měly přístup ke stejným prvkům sady nástrojů, ale zabránily souběžným instalacím různých verzí sady Visual Studio.

V rámci podpory rychlejší, menší a souběžné instalace sady Visual Studio 2017 a novějších verzí již nástroj MSBuild neumísťuje do mezipaměti GAC nebo upravuje registr. To bohužel znamená, že aplikace, které chtějí používat rozhraní API MSBuild k vyhodnocení nebo sestavení projektů, se nemůžou implicitně spoléhat na instalaci sady Visual Studio.

## <a name="use-msbuild-from-visual-studio"></a>Použití nástroje MSBuild ze sady Visual Studio

Aby se programová sestavení z vaší aplikace shodovala s sestaveními provedenými v sadě Visual Studio nebo *MSBuild.exe*, načítat sestavení nástroje MSBuild ze sady Visual Studio a používat sady SDK dostupné v sadě Visual Studio. Tento proces zjednodušuje balíček NuGet Microsoft. Build. Locator.

## <a name="use-microsoftbuildlocator"></a>Použití Microsoft. Build. Locator

Pokud redistribuujete *Microsoft.Build.Locator.dll* s vaší aplikací, nebudete muset distribuovat další sestavení nástroje MSBuild.

Aktualizace projektu na použití nástroje MSBuild 15 a rozhraní API lokátoru vyžaduje v projektu několik změn, které jsou popsány níže. Chcete-li zobrazit příklad změn požadovaných k aktualizaci projektu, přečtěte si [potvrzení provedených na ukázkovém projektu v úložišti MSBuildLocator](https://github.com/Microsoft/MSBuildLocator/commits/example-updating-to-msbuild-15).

### <a name="change-msbuild-references"></a>Změnit odkazy MSBuild

Aby bylo zajištěno, že nástroj MSBuild načte z centrálního umístění, nesmíte distribuovat jeho sestavení do aplikace.

Mechanismus pro změnu projektu, aby nedocházelo k načítání MSBuild z centrálního umístění, závisí na tom, jak odkazujete na MSBuild.

#### <a name="use-nuget-packages-preferred"></a>Používat balíčky NuGet (preferované)

V těchto pokynech se předpokládá, že používáte [odkazy na PackageReference ve stylu NuGet](/nuget/consume-packages/package-references-in-project-files).

Soubory projektu můžete změnit tak, aby odkazovaly na sestavení MSBuild ze svých balíčků NuGet. Určete `ExcludeAssets=runtime` , aby se NuGet informovalo, že sestavení jsou potřeba jenom v čase sestavení, a neměla by se kopírovat do výstupního adresáře.

Hlavní a dílčí verze balíčků MSBuild musí být menší než nebo rovna minimální verzi sady Visual Studio, kterou chcete podporovat. Například pokud chcete podporovat sadu Visual Studio 2017 a novější verze, referenční verze balíčku `15.1.548` .

Můžete například použít tento kód XML:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.Build" Version="15.1.548" ExcludeAssets="runtime" />
  <PackageReference Include="Microsoft.Build.Utilities.Core" Version="15.1.548" ExcludeAssets="runtime" />
</ItemGroup>
```

#### <a name="use-extension-assemblies"></a>Použít sestavení rozšíření

Pokud nemůžete použít balíčky NuGet, můžete odkazovat na sestavení nástroje MSBuild, která jsou distribuována se sadou Visual Studio. Pokud přímo odkazujete na MSBuild, ujistěte se, že se nezkopíruje do výstupního adresáře nastavením `Copy Local` na `False` . V souboru projektu bude toto nastavení vypadat jako v následujícím kódu:

```xml
    <Reference Include="Microsoft.Build, Version=15.1.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
      <Private>False</Private>
    </Reference>
```

#### <a name="binding-redirects"></a>Přesměrování vazeb

Vytvořte odkaz na balíček Microsoft. Build. Locator, abyste zajistili, že vaše aplikace automaticky používá přesměrování požadované vazby na verzi 15.1.0.0. Přesměrování vazby na tuto verzi podporuje MSBuild 15 i MSBuild 16.

### <a name="ensure-output-is-clean"></a>Zajistěte, aby byl výstup čistý.

Sestavte projekt a zkontrolujte výstupní adresář, abyste se ujistili, že neobsahuje žádné *Microsoft. Build. \* .* v dalším kroku jsou přidána jiná sestavení knihovny DLL než *Microsoft.Build.Locator.dll*.

### <a name="add-package-reference-for-microsoftbuildlocator"></a>Přidat odkaz na balíček pro Microsoft. Build. Locator

Přidejte odkaz na balíček NuGet pro [Microsoft. Build. Locator](https://www.nuget.org/packages/Microsoft.Build.Locator/).

```xml
    <PackageReference Include="Microsoft.Build.Locator">
      <Version>1.1.2</Version>
    </PackageReference>
```

Nezadávejte `ExcludeAssets=runtime` pro balíček Microsoft. Build. Locator.

### <a name="register-instance-before-calling-msbuild"></a>Registrovat instanci před voláním MSBuild

> [!IMPORTANT]
> V metodě, která volá MSBuildLocator, nelze odkazovat na žádné typy MSBuild (z `Microsoft.Build` oboru názvů). Například to nemůžete udělat:
>
> ```csharp
> void ThisWillFail()
> {
>     MSBuildLocator.RegisterDefaults();
>     Project p = new Project(SomePath); // Could be any MSBuild type
>     // Code that uses the MSBuild type
> }
> ```
>
> Místo toho je nutné provést tento postup:
>
> ```csharp
> void MethodThatDoesNotDirectlyCallMSBuild()
> {
>     MSBuildLocator.RegisterDefaults();
>     MethodThatCallsMSBuild();
> }
> 
> void MethodThatCallsMSBuild()
> {
>     Project p = new Project(SomePath);
>     // Code that uses the MSBuild type
> }
> ```

Nejjednodušší způsob, jak přidat volání do rozhraní API lokátoru, je přidat volání do

```csharp
MSBuildLocator.RegisterDefaults();
```

ve spouštěcím kódu aplikace.

Pokud chcete lepší kontrolu nad nasazováním nástroje MSBuild, můžete vybrat výsledek, který `MSBuildLocator.QueryVisualStudioInstances()` je třeba předat `MSBuildLocator.RegisterInstance()` ručně, ale obvykle to není potřeba.
