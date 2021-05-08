---
title: Průzkumník testů – nejčastější dotazy
description: Přečtěte si tyto Nejčastější dotazy k aplikaci Visual Studio Test Explorer, která zahrnuje některé běžné řešení potíží.
ms.custom: SEO-VS-2020
ms.date: 06/25/2020
ms.topic: conceptual
helpviewer_keywords:
- Test Explorer
- Test window
- Visual Studio Test Explorer
- summary line
- unit tests
- Test Explorer FAQ
ms.author: kehavens
ms.workload:
- multiple
author: kendrahavens
manager: jmartens
ms.openlocfilehash: 22ac969ba2ad918fcbeb7c53e04cd3f2b03a0431
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798567"
---
# <a name="visual-studio-test-explorer-faq"></a>Visual Studio Test Explorer – Nejčastější dotazy

## <a name="dynamic-test-discovery"></a>Dynamické zjišťování testů

**Průzkumník testů nezjišťuje moje testy, které jsou dynamicky definovány. (Například teorie, vlastní adaptéry, vlastní vlastnosti, #ifdefs atd.) Jak můžu zjistit tyto testy?**

::: moniker range=">=vs-2019"
Sestavte projekt pro spuštění zjišťování založeného na sestavení.
::: moniker-end
::: moniker range="vs-2017"
Sestavte projekt a ujistěte se, že je v **nabídce nástroje** >  > **test** možností zapnuto zjišťování na základě sestavení.
::: moniker-end
[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) je zjišťování založené na zdrojovém testu. Nedokáže zjistit testy, které používají teorie, vlastní adaptéry, vlastní vlastnosti, `#ifdef` příkazy a další, protože jsou definovány v době běhu. Aby byly testy přesně nalezeny, je nutné sestavit sestavení. V aplikaci Visual Studio 2017 verze 15,6 a novější se zjišťování na základě sestavení (tradiční zjišťování) spouští pouze po sestaveních. Toto nastavení znamená, že zjišťování testů v reálném čase najde tolik testů, kolik jich může při úpravách a zjišťování na základě sestavení umožňuje zobrazit dynamicky definované testy po sestavení. Zjišťování testů v reálném čase vylepšuje rychlost odezvy, ale pořád umožňuje získat úplné a přesné výsledky po sestavení.

## <a name="test-explorer--plus-symbol"></a>Symbol Průzkumníka testu + (plus)

**Co znamená symbol "+" (plus), který se zobrazí v horním řádku Průzkumníka testů?**

Symbol plus (+) označuje, že další testy mohou být zjištěny po sestavení při spuštění zjišťování založeného na sestavení. Tento symbol se zobrazí, pokud jsou ve vašem projektu zjištěny dynamicky definované testy.

![Řádek souhrnu symbolů plus](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Zjišťování na základě sestavení

**Zjišťování na základě sestavení již pro můj projekt nepracuje. Návody ho znovu zapnout?**

Přejít na  > **Možnosti** nástroje > **test** a zaškrtněte políčko pro další **zjišťování testů z sestavených sestavení po sestaveních.**

![Možnost založená na sestavení](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Zjišťování testů v reálném čase

**Testy se teď během psaní zobrazují v Průzkumníku testů, aniž byste museli sestavovat projekt. Co se změnilo?**

Tato funkce se nazývá [zjišťování testů v reálném čase.](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) Používá analyzátor Roslyn k vyhledání testů a naplnění Průzkumníka testů v reálném čase, aniž by bylo nutné sestavovat projekt. Další informace o chování zjišťování testů pro dynamicky definované testy, jako jsou teorie nebo vlastní vlastnosti, najdete v tématu [Dynamické zjišťování testů.](#dynamic-test-discovery)

## <a name="real-time-test-discovery-compatibility"></a>Kompatibilita zjišťování testů v reálném čase

**Které jazyky a testovací architektury mohou používat zjišťování testů v reálném čase?**

[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) funguje pouze pro spravované jazyky (C# a Visual Basic), protože je sestavené pomocí kompilátoru Roslyn. Zjišťování testů v reálném čase teď funguje jenom pro architektury xUnit, NUnit a MSTest.

## <a name="test-explorer-logs"></a>Protokoly Průzkumníka testů

**Jak můžu zapnout protokoly pro Průzkumníka testů?**

Přejděte na **Nástroje**  >  **Možnosti**  >  **Test a** vyhledejte část Protokolování.

## <a name="uwp-test-discovery"></a>Zjišťování testů UPW

**Proč se moje testy v projektech UPW neobjeví, dokud nenasadím aplikaci?**

Testy UPW cílí při nasazení aplikace na jiný modul runtime. To znamená, že k přesnému vyhledání testů pro projekty UPW potřebujete nejen sestavit projekt, ale také ho nasadit.

## <a name="test-explorer-sorting"></a>Řazení Průzkumníka testů

**Jak funguje řazení výsledků testů v hierarchickém zobrazení?**

Hierarchické zobrazení seřadí testy abecedně, nikoli podle výsledku. Předchozí skupina podle nastavení seřadily výsledky testů podle výsledku a pak podle abecedy. Můžete přesto Povolit řazení podle výsledku tak, že v Průzkumníku testů kliknete pravým tlačítkem na záhlaví sloupce, zapnete sloupec stav a potom kliknutím na záhlaví sloupce stav použijete řazení tohoto sloupce. Můžete poskytnout zpětnou vazbu k návrhu v tomto [problému GitHubu](https://github.com/Microsoft/vstest/issues/1425).

## <a name="test-explorer-hierarchy-view"></a>Hierarchické zobrazení Průzkumníka testů

**V zobrazení hierarchie jsou předány, selhaly, vynechány a nespuštěny ikony vedle seskupení nadřazených uzlů. Co tyto ikony znamenají?**

Ikony vedle projektu, oboru názvů a seskupení tříd zobrazují stav testů v rámci tohoto seskupení. Podívejte se na následující tabulku.

![Ikony hierarchie Průzkumníka testů](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Hledat podle cesty k souboru

**Ve vyhledávacím poli Průzkumníka testů již není k dispozici filtr "Souborová cesta".**

Filtr cesty k souboru v poli Hledat v **Průzkumníku testů** byl odebrán v aplikaci Visual Studio 2017 verze 15,7. Tato funkce měla nízké využití a Průzkumník testů může rychleji načíst testovací metody tím, že tuto funkci opustí. Pokud tato změna přerušuje tok vývoje, dejte nám vědět o odeslání názoru na [komunitu vývojářů](https://aka.ms/feedback/suggest?space=8).

## <a name="remove-undocumented-interfaces"></a>Odebrat nedokumentovaná rozhraní

**Některá rozhraní API související s testem již nejsou součástí sady Visual Studio 2019. Co se změnilo?**

V aplikaci Visual Studio 2019 se odeberou některá rozhraní API testovacího okna, která byla dříve označena jako veřejná, ale nebyla nikdy oficiálně dokumentována. Byly označeny jako "zastaralé" v aplikaci Visual Studio 2017, aby udržovaly rozšíření udržovala včasné varování. Pro naše poznatky našla tato rozhraní API mnohem málo rozšíření a na nich se zavedla závislost. Mezi ně patří `IGroupByProvider` ,,,, `IGroupByProvider<T>` `KeyComparer` `ISearchFilter` `ISearchFilterToken` , `ISearchToken` a `SearchFilterTokenType` . Pokud tato změna ovlivní vaše rozšíření, dejte nám prosím jistotu, že napíšete chybu do [komunity vývojářů](https://aka.ms/feedback/suggest?space=8).

## <a name="test-adapter-nuget-reference"></a>Reference k NuGetu testovacího adaptéru

**V Visual Studio 2017 verze 15.8 se moje testy získejte, ale neschováte je.**

Všechny projekty testů musí v souboru .csproj obsahovat odkaz NuGet adaptéru testu .NET. Pokud ne, zobrazí se v projektu následující výstup testu, pokud se zjišťování rozšířením testovacího adaptéru spustí po sestavení nebo když se uživatel pokusí spustit vybrané testy:

**Projekt testů {} neodkašuje na žádný adaptér NuGet .NET. Zjišťování nebo spouštění testů nemusí pro tento projekt fungovat. V každém projektu testů .NET v řešení doporučujeme odkazovat na adaptéry testů NuGet.**

Místo použití rozšíření testovacího adaptéru se u projektů vyžaduje použití balíčků NuGet testovacího adaptéru. Tento požadavek výrazně zlepšuje výkon a způsobuje méně problémů s kontinuální integrací. Další informace o zahozování rozšíření testovacího adaptéru .NET najdete v [poznámkách k verzi.](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension)

::: moniker range="vs-2017"
> [!NOTE]
> Pokud používáte adaptér testů NUnit 2 a nemůžete migrovat na testovací adaptér NUnit 3, můžete toto nové chování zjišťování vypnout v nástroji Visual Studio verze 15.8 v části **Nástroje**  >  **Možnosti**  >  **Test.**

![Chování adaptéru Průzkumníka testů v možnostech nástrojů](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>TestContainer pro UPW se nenašel

**Testy UPW se už nebudou provádět v Visual Studio 2017 verze 15.7 a novější.**

Nedávné projekty testů UPW určují vlastnost sestavení testovací platformy, která umožňuje lepší výkon pro identifikaci testovacích aplikací. Pokud máte projekt testů UPW, který byl inicializován před Visual Studio verze 15.7, může se tato chyba zobrazit ve **výstupních**  >  **testech:**

**System.AggregateException: Došlo k jedné nebo více chybám. ---> System.InvalidOperationException: Následující testcontainer nebyl nalezen v {} Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync> d__61.MoveNext()**

Pokud chcete tuto chybu vyřešit:

- Aktualizujte vlastnost sestavení projektu testů pomocí následujícího kódu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualizujte verzi sady TestPlatform SDK pomocí následujícího kódu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Použití funkcí Preview

V aplikaci Visual Studio 2019 se můžete vyjádřit k funkcím ve verzi Preview v **nástrojích > možnosti > prostředí > funkce ve verzi Preview**.
::: moniker-end
::: moniker range=">=vs-2017"
## <a name="using-feature-flags"></a>Používání příznaků funkcí

**Jak můžu zapnout příznaky funkcí a vyzkoušet nové funkce testování?**

Příznaky funkcí se používají k dodávání experimentálních nebo nedokončených částí produktu k avidí uživatelů, kteří chtějí poskytnout zpětnou vazbu předtím, než se funkce dodávají úředně. Můžou destabilizovat prostředí IDE. Používejte je jenom v bezpečných vývojových prostředích, jako jsou třeba virtuální počítače. Příznaky funkcí jsou vždy k dispozici v nastavení vlastní riziko. Můžete zapnout experimentální funkce s [rozšířením příznaků funkcí](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)nebo pomocí příkazového řádku pro vývojáře.

![Rozšíření příznak funkce](media/testex-featureflag.png)

Chcete-li zapnout příznak funkce prostřednictvím příkazového řádku vývojáře sady Visual Studio, použijte následující příkaz. Změňte cestu na umístění, kde je v počítači nainstalováno Visual Studio, a změňte klíč registru na požadovaný příznak funkce.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Příznak můžete vypnout stejným příkazem, a to pomocí hodnoty 0 namísto hodnoty 1 po hodnotě DWORD.
::: moniker-end
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Vytvoření a spuštění testů jednotek pro existující kód](/previous-versions/dd293546(v=vs.110))
- [Testování částí kódu](unit-test-your-code.md)
- [Nejčastější dotazy ke službě Live Unit Testing](live-unit-testing-faq.yml)