---
title: Aktualizace na MSTestV2
description: Informace o tom, jak aktualizovat z MSTestV1 na MSTestV2
ms.custom: SEO-VS-2020
ms.date: 02/26/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ffe45c444321a7efbaee0a2eb5729850a06c5910
ms.sourcegitcommit: 99b66b0f4ced46ead0b2506a103f974f40cc0076
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2021
ms.locfileid: "103366254"
---
# <a name="upgrade-from-mstestv1-to-mstestv2"></a>Upgrade z MSTestV1 na MSTestV2

Můžete upgradovat projekt testů tím, že změníte cílení verze MSTest, na kterou se odkazuje v *. csproj* z MSTestV1 na MSTestV2. Ne všechny funkce v MSTestV1 byly přeneseny do MSTestV2, takže některé změny mohou být požadovány k vyřešení chyb. Podívejte se na [funkce MSTestV1, které nejsou podporované v MSTestV2](#mstestv1-features-that-are-not-supported-in-mstestv2) , abyste pochopili, jaké funkce už nebudou fungovat. Některé z těchto z nich může být nutné odebrat z testů.

1. Odeberte odkaz na sestavení Microsoft. VisualStudio. QualityTools. UnitTestFramework z projektu testování částí.
2. Přidejte do MSTestV2 odkazy na balíček NuGet včetně balíčků [MSTest. TestFramework](https://www.nuget.org/packages/MSTest.TestFramework) a [MSTest. TestAdapter](https://www.nuget.org/packages/MSTest.TestAdapter/) na NuGet.org. Balíčky můžete nainstalovat do konzoly Správce balíčků NuGet pomocí následujících příkazů:

    ```console
    PM> Install-Package MSTest.TestAdapter -Version 2.1.2
    PM> Install-Package MSTest.TestFramework -Version 2.1.2
    ```

### <a name="old-style-csproj-example"></a>Příklad původního stylu csproj

Sample *. csproj* cílící na MSTestV1:

```xml
<Reference Include="Microsoft.VisualStudio.QualityTools.UnitTestFramework, Version=10.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <Private>False</Private>
</Reference>
```

Sample *. csproj* teď cílí na MSTestV2:

```xml
<Reference Include="Microsoft.VisualStudio.TestPlatform.TestFramework, Version=14.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, processorArchitecture=MSIL">
  <HintPath>..\packages\MSTest.TestFramework.2.1.2\lib\net45\Microsoft.VisualStudio.TestPlatform.TestFramework.dll</HintPath>
</Reference>
```

> [!NOTE]
> Projekty testů, které jsou kódované testy uživatelského rozhraní nebo testy webového zatížení, nejsou kompatibilní s MSTestV2. Tyto typy projektů jsou zastaralé. Přečtěte si další informace o vyřazení programového [testu uživatelského rozhraní](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) a vyřazení [webového zátěžového testu](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

### <a name="sdk-style-csproj-net-core-and-net-5"></a>Sada SDK – Style csproj (.NET Core a .NET 5)

Pokud je váš *. csproj* novějším stylem sady SDK *. csproj* , pravděpodobně již používáte MSTestV2. Balíčky NuGet pro [MSTestV2](https://www.nuget.org/packages/MSTest.TestFramework) a [adaptér MSTestV2](https://www.nuget.org/packages/MSTest.TestAdapter/) můžete najít na NuGet.

Příklad:

```xml
<ItemGroup>
  <PackageReference Include="Microsoft.NET.Test.Sdk" Version="16.7.1" />
  <PackageReference Include="MSTest.TestAdapter" Version="2.1.1" />
  <PackageReference Include="MSTest.TestFramework" Version="2.1.1" />
</ItemGroup>
```

## <a name="why-upgrade-to-mstestv2"></a>Proč upgradovat na MSTestV2?

V 2016 jsme vydali další krok vyvíjející rozhraní MSTest s MSTestV2. Další informace o této změně najdete v [příspěvku na blogu](https://devblogs.microsoft.com/devops/taking-the-mstest-framework-forward-with-mstest-v2/)v oznámení.

* MSTestV2 je snazší získat a aktualizovat, protože je dodávána jako [balíček NuGet](https://www.nuget.org/packages/MSTest.TestFramework/).
* MSTestV2 je [Open Source](https://github.com/microsoft/testfx).
* Jednotná implementace App-Platform – MSTestV2 je sblížená implementace, která nabízí jednotnou podporu pro App-Platform napříč .NET Framework, .NET Core, ASP.NET Core a UWP. [Další informace](https://blogs.msdn.microsoft.com/devops/2016/09/01/announcing-mstest-v2-framework-support-for-net-core-1-0-rtm/).
* Implementace je plně rozplatformovaná pro různé platformy (Windows, Linux, Mac). [Další informace](https://blogs.msdn.microsoft.com/devops/2017/04/05/mstest-v2-is-open-source/).
* MSTestV2 podporuje cílení na .NET Framework 4.5.0 a novější, .NET Core 1,0 a novější (univerzální aplikace pro Windows 10 +), ASP.NET Core 1,0 a novější a .NET 5 a novější.
* Poskytuje jednotný mechanismus rozšiřitelnosti koncového uživatele. [Další informace](https://blogs.msdn.microsoft.com/devops/2017/07/18/extending-mstest-v2/).
* Poskytuje jednotnou `DataRow` podporu pro všechny projekty testů založené na MSTest. [Další informace](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Umožňuje umístění `TestCategory` atributu na úrovni třídy nebo sestavení. [Další informace](https://blogs.msdn.microsoft.com/devops/2017/02/25/mstest-v2-now-and-ahead/).
* Testovací metody ze základních tříd definovaných v jiném sestavení jsou nyní zjištěny a spouštěny z odvozené třídy testu. Tato změna přináší konzistentní chování s odvozenými typy testovacích tříd. Pokud se toto chování nevyžaduje z důvodů kompatibility, můžete ho změnit zpátky pomocí následujících parametrů běhu:

    ```xml
    <RunSettings>    
    <MSTest> 
      <EnableBaseClassTestMethodsFromOtherAssemblies>false</EnableBaseClassTestMethodsFromOtherAssemblies> 
    </MSTest> 
    </RunSettings>
    ```

* Poskytuje přesnější kontrolu nad paralelním spouštěním prostřednictvím [sestavení paralelního spouštění](https://github.com/Microsoft/testfx-docs/blob/master/RFCs/004-In-Assembly-Parallel-Execution.md) testů. To umožňuje souběžné spouštění testů v sestavení.
* `TestCleanup`Metoda v `TestClass` je vyvolána i v případě, že odpovídající `TestInitialize` metoda se nezdařila. [Podrobnosti o problému](https://github.com/Microsoft/testfx/issues/250).
* Doba, kterou zabere `AssemblyInitialize` a `ClassInitialize` se nepočítá směrem k době trvání testu. Tato změna omezuje svůj dopad na vypršení časového limitu testu.
* Testy, které nejsou spustitelný, je možné nakonfigurovat tak, aby byly označeny jako neúspěšné prostřednictvím `MapNotRunnableToFailed` značky, která je součástí uzlu adaptéru v `.runsettings` souboru.

    ```xml
    <RunSettings>    
    <MSTest> 
      <MapNotRunnableToFailed>true</MapNotRunnableToFailed> 
    </MSTest> 
    </RunSettings>
    ```

## <a name="mstestv1-features-that-are-not-supported-in-mstestv2"></a>Funkce MSTestV1, které nejsou podporované v MSTestV2

*   Testy nelze zahrnout do "objednaného testu".
*   Adaptér nepodporuje konfiguraci pomocí souboru *. testsettings* . Použijte nový soubor [ *. runsettings*](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md) pro konfiguraci testovacího běhu.
*   Adaptér nepodporuje seznamy testů zadané jako soubor *. vsmdi* .
*   Typy projekt "programový test uživatelského rozhraní" a "projekt testů výkonnosti webu" a "test zátěžového testu" nejsou podporovány. Přečtěte si další informace o vyřazení programového [testu uživatelského rozhraní](https://devblogs.microsoft.com/devops/changes-to-coded-ui-test-in-visual-studio-2019/) a vyřazení [webového zátěžového testu](https://devblogs.microsoft.com/devops/cloud-based-load-testing-service-eol/).

## <a name="see-also"></a>Viz také

- [Konfigurace testovacích běhů s `.runsettings`](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [Testování částí kódu](../test/unit-test-your-code.md)
- [Ladění testů částí pomocí Průzkumníka testů](../test/debug-unit-tests-with-test-explorer.md)
