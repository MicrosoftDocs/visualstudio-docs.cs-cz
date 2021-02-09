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
ms.openlocfilehash: a1e0f998b5fff45a8fee9ac6f9cc6a0ce2268907
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894462"
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

![Možnost založenou na sestavení](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Zjišťování testů v reálném čase

**Testy se nyní zobrazí v Průzkumníku testu při psaní, aniž by bylo nutné sestavit projekt. Co se změnilo?**

Tato funkce se nazývá [zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Pomocí analyzátoru Roslyn vyhledá testy a naplní Průzkumník testů v reálném čase, aniž by bylo nutné sestavit projekt. Další informace o chování zjišťování testů pro dynamicky definované testy, jako jsou teorie nebo vlastní vlastnosti, naleznete v tématu [dynamické zjišťování testů](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Kompatibilita zjišťování testů v reálném čase

**Jaké jazyky a testovací architektury můžou použít zjišťování testů v reálném čase?**

[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) funguje pouze pro spravované jazyky (C# a Visual Basic), protože je vytvořeno pomocí kompilátoru Roslyn. V současné době zjišťování testů v reálném čase funguje pouze pro xUnit, NUnit a MSTest architektury.

## <a name="test-explorer-logs"></a>Protokoly Průzkumníka testů

**Jak můžu zapnout protokoly pro Průzkumníka testů?**

Přejděte k   >  **Možnosti** nástroje  >  **test** a vyhledejte část protokolování.

## <a name="uwp-test-discovery"></a>Zjišťování testů UWP

**Proč se moje testy v projektech UWP nezjistily, dokud nasadím aplikaci?**

Testy UWP cílí na jiný modul runtime při nasazení aplikace. To znamená, že k nalezení testů přesně pro projekty UWP nemusíte sestavovat projekt, ale také nasadit.

## <a name="test-explorer-sorting"></a>Řazení Průzkumníka testů

**Jak funguje řazení výsledků testů v zobrazení hierarchie?**

Zobrazení hierarchie seřadí testy abecedně na rozdíl od výsledku. Předchozí skupina podle nastavení seřadily výsledky testů podle výsledku a pak podle abecedy. Můžete přesto Povolit řazení podle výsledku tak, že v Průzkumníku testů kliknete pravým tlačítkem na záhlaví sloupce, zapnete sloupec stav a potom kliknutím na záhlaví sloupce stav použijete řazení tohoto sloupce. Můžete poskytnout zpětnou vazbu k návrhu v tomto [problému GitHubu](https://github.com/Microsoft/vstest/issues/1425).

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

**V aplikaci Visual Studio 2017 verze 15,8 jsou zjištěny testy, ale nespustí se.**

Všechny projekty testů musí zahrnovat svůj odkaz na NuGet rozhraní .NET test Adapter v souboru. csproj. Pokud ne, zobrazí se v projektu následující výstup testu, pokud je zjišťování pomocí rozšíření testovacího adaptéru po sestavení spuštěno nebo pokud se uživatel pokusí spustit vybrané testy:

**Projekt testů {} neodkazuje na žádný adaptér rozhraní .NET NuGet. Zjišťování nebo provádění testů nemusí pro tento projekt fungovat. Doporučuje se odkazovat na testovací adaptéry NuGet v každém projektu .NET test v řešení.**

Místo používání rozšíření testovacího adaptéru se projekty vyžadují pro použití balíčků NuGet pro testovací adaptéry. Tento požadavek významně zvyšuje výkon a způsobuje méně problémů se kontinuální integrací. Další informace o vyřazení rozšíření testovacího adaptéru .NET najdete v [poznámkách k verzi](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Pokud používáte testovací adaptér nunit 2 a nemůžete migrovat na testovací adaptér nunit 3, můžete toto nové chování zjišťování vypnout v aplikaci Visual Studio verze 15,8 v části **nástroje**  >    >  **test** možností.

![Chování adaptéru Průzkumníka testů v možnostech nástrojů](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>Nenašlo se TestContainer UWP.

**Moje testy UWP již nejsou spouštěny v aplikaci Visual Studio 2017 verze 15,7 a novější.**

Poslední projekty testů UWP určují vlastnost sestavení testovací platformy, která umožňuje lepší výkon pro identifikaci testovacích aplikací. Pokud máte projekt testů UWP, který byl inicializován před verzí sady Visual Studio verze 15,7, může se tato chyba zobrazit ve **výstupních**  >  **testech**:

**System. AggregateException: došlo k jedné nebo více chybám. ---> System. InvalidOperationException: následující TestContainer nebyl nalezen {} v Microsoft. VisualStudio. TestWindow. Controller. TestContainerProvider \<GetTestContainerAsync> D__61. MoveNext ()**

Oprava této chyby:

- Aktualizujte vlastnost Build projektu testu pomocí následujícího kódu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualizujte verzi sady SDK TestPlatform pomocí následujícího kódu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```
::: moniker range=">=vs-2019"
## <a name="using-preview-features"></a>Používání funkcí verze Preview

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
- [Nejčastější dotazy ke službě Live Unit Testing](live-unit-testing-faq.md)