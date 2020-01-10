---
title: Průzkumník testů – nejčastější dotazy
ms.date: 08/14/2019
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
manager: jillfra
ms.openlocfilehash: cec8ea3ea091ab1ea65bcad2bd4cca139fd74042
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/10/2020
ms.locfileid: "75846811"
---
# <a name="visual-studio-test-explorer-faq"></a>Průzkumník testů sady Visual Studio – nejčastější dotazy
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Kde je v aplikaci Visual Studio 2019 seskupení podle vlastností?
Toto seskupení vlastností se přesunulo na sloupec. S vícevrstvou a přizpůsobitelnou hierarchií v aplikaci Visual Studio 2019 verze 16,2 jsme si mysleli, že jako seskupení vytvořilo nepotřebnou vizuální složitost, včetně vlastností. V tomto designu jsme jednoznačně naslouchají názoru. https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Prozatím můžete kliknout pravým tlačítkem na sloupec v Průzkumníku testů a vybrat sloupce. Zkontrolujte sloupec vlastností a zobrazí se v Průzkumníku testů. Tento sloupec teď můžete filtrovat podle vlastností, které vás zajímají.

![Zobrazit sloupec vlastností](media/vs-2019/trait-column.png)
![filtrovat sloupec vlastností](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Zjišťování dynamických testů

**Průzkumník testů nezjišťuje moje testy, které jsou dynamicky definovány. (Například teorie, vlastní adaptéry, vlastní vlastnosti, #ifdefs atd.) Jak můžu zjistit tyto testy?**

::: moniker range=">=vs-2019"
Sestavte projekt pro spuštění zjišťování založeného na sestavení.
::: moniker-end
::: moniker range="vs-2017"
Sestavte projekt a ujistěte se, že je zapnuté zjišťování na základě sestavení v **nabídce nástroje** > **Možnosti** > **test**.
::: moniker-end
[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) je založen zdroj testu zjišťování. Nedokáže zjistit testy, které používají teorie, vlastní adaptéry, vlastní vlastnosti, příkazy `#ifdef` a další, protože jsou definovány v době běhu. Sestavení je vyžadován pro tyto testy na přesně najít. V sadě Visual Studio 2017 verze 15.6 a novější se spustí zjišťování na základě sestavení (tradiční prozkoumání) až po sestavení. Toto nastavení znamená, že v reálném čase testu zjišťování najde libovolný počet testů, jak jde při úpravách a zjišťování na základě sestavení umožňuje dynamicky definované testů se zobrazí po sestavení. Zjišťování testů v reálném čase vylepšuje rychlost odezvy, ale pořád umožňuje získat úplné a přesné výsledky po sestavení.

## <a name="test-explorer--plus-symbol"></a>Průzkumník testů "+" (plus) symbol

**Co dělá "+" (plus) symbol, který se zobrazí v horní zobrazený řádek znamená Průzkumník testů?**

Symbol plus (+) označuje, že další testy mohou být zjištěny po sestavení při spuštění zjišťování založeného na sestavení. Tento symbol se zobrazí dynamicky definované v případě, že testy se zjistí ve vašem projektu.

![Souhrn řádku znaménko plus](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Zjišťování na základě sestavení

**Zjišťování na základě sestavení již pro můj projekt nepracuje. Návody ho znovu zapnout?**

Přejít na **nástroje** > **Možnosti** > **test** a zaškrtněte políčko pro další **zjišťování testů z sestavených sestavení po sestaveních.**

![Možnosti založené na sestavení](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Zjišťování testů v reálném čase

**Testy se nyní zobrazí v Průzkumníku testu při psaní, aniž by bylo nutné sestavit projekt. Co se změnilo?**

Tato funkce se nazývá [zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Roslyn analyzátor používá k vyhledání testů a naplnit Průzkumníka testů v reálném čase, aniž by bylo potřeba svůj projekt sestavit. Další informace o chování zjišťování testů pro dynamicky definované testy, jako jsou teorie nebo vlastní vlastnosti, naleznete v tématu [dynamické zjišťování testů](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Kompatibilita zjišťování testů v reálném čase

**Jaké jazyky a rozhraní pro testování můžete použít zjišťováním testů v reálném čase?**

[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) funguje jenom pro spravované jazyky (C# a Visual Basic), protože je vytvořen pomocí kompilátoru Roslyn. Prozatím se zjišťování testů v reálném čase funguje jenom pro xUnit, NUnit a MSTest architektur.

## <a name="test-explorer-logs"></a>Protokoly Průzkumníka testů

**Jak můžu zapnout protokolování pro Průzkumník testů?**

Přejděte do **nástroje** > **možnosti** > **Test** a najdete v části protokolování existuje.

## <a name="uwp-test-discovery"></a>Zjišťování testů UPW

**Proč jsou mé testy v projektech UPW nezjištěné dokud nasadit aplikaci?**

Testů UPW cílení různých běhových při nasazení aplikace. To znamená, že se nenašly testy přesně pro projekty UWP vám nejen na svůj projekt sestavit, ale také nasadit.

## <a name="test-explorer-sorting"></a>Test Explorer řazení

**Jak funguje řazení výsledků testů v zobrazení hierarchie?**

Hierarchické zobrazení seřadí testy podle abecedy jako a podle výsledku. Podle nastavení skupiny obvykle řazení výsledků testů podle výsledku a pak podle abecedy. Možnosti na následujícím obrázku pro porovnání najdete v jiné skupině. Můžete poskytnout zpětnou vazbu o návrhu [v tento problém Githubu](https://github.com/Microsoft/vstest/issues/1425).

![SortingExamples](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Zobrazení hierarchie Průzkumníka testů

**V zobrazení hierarchie jsou předány, selhaly, vynechány a nespuštěny ikony vedle seskupení nadřazených uzlů. Co tyto ikony znamenají?**

Ikony vedle seskupení projektu, Namespace a třída zobrazení stavu testů v rámci tohoto seskupení. V následující tabulce.

![Ikony hierarchie Průzkumníka testů](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Hledat podle cesta k souboru

**Do vyhledávacího pole Průzkumníka testů již není filtr "Cesta k souboru".**

Filtr cesty k souboru v poli Hledat v **Průzkumníku testů** byl odebrán v aplikaci Visual Studio 2017 verze 15,7. Tato funkce měla nízké využití a Průzkumník testů může rychleji načíst testovací metody tím, že tuto funkci opustí. Pokud se tato změna přerušení tok vývoj, dejte nám vědět, zasláním svého názoru na [komunity vývojářů](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Odebrání nedokumentované rozhraní

**Některá rozhraní API související s testem již nejsou součástí sady Visual Studio 2019. Co se změnilo?**

V aplikaci Visual Studio 2019 se odeberou některé testovacího okna rozhraní API, které byly dříve označeny veřejné, ale nebyly nikdy oficiálně popsané. Označí se jako "zastaralé" v sadě Visual Studio 2017 poskytnout programu rozšíření včasného varování. Naši znalostní bázi měl velmi málo rozšíření nalezena tato rozhraní API a s nimi provádějí závislost. Patří mezi ně `IGroupByProvider`, `IGroupByProvider<T>`, `KeyComparer`, `ISearchFilter`, `ISearchFilterToken`, `ISearchToken`, a `SearchFilterTokenType`. Pokud se tato změna ovlivní vaše rozšíření, dejte nám vědět, vyplňte chybu na [komunity vývojářů](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Testovací adaptér referenční dokumentace pro NuGet

**V sadě Visual Studio 2017 verze 15.8 mé testy se zjistí, ale nemusíte spouštět.**

Všechny projekty testů musí obsahovat testovací adaptér jejich .NET NuGet odkaz v jejich souboru csproj. Pokud ne, zobrazí se následující výstup testu na projekt Pokud zjišťování adaptéru rozšířením test spustí se po sestavení, nebo pokud uživatel pokusí spustit vybrané testy:

**Testovací projekt {} neodkazuje na žádný adaptér rozhraní .NET NuGet. Zjišťování nebo provádění testů nemusí pro tento projekt fungovat. Doporučuje se odkazovat na testovací adaptéry NuGet v každém projektu .NET test v řešení.**

Namísto použití rozšíření adaptérů testů, jsou nutné k použití balíčků adaptéru NuGet testovací projekty. Tento požadavek výrazně zvyšuje výkon a způsobí, že snižuje počet možných problémů s využitím průběžné integrace. Další informace o vyřazení rozšíření adaptér testu .NET v [poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Pokud používáte NUnit 2 Test Adapter a jsou nelze provést migraci k NUnit 3 test adapter, můžete ji vypnout toto nové chování zjišťování v sadě Visual Studio verzi 15.8 v **nástroje** > **možnosti**  >  **Test**.

![Test Explorer adaptér chování v možnostech nástrojů](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UPW TestContainer nebyl nalezen

**Moje testy UWP již nejsou spouštěny v aplikaci Visual Studio 2017 verze 15,7 a novější.**

Poslední projekty testů UPW zadejte vlastnosti sestavení testovací platformy, která umožňuje lepší výkon pro identifikaci testovací aplikace. Pokud máte projektu testů UPW, který byl inicializován před Visual Studio verze 15.7, může se zobrazit tato chyba v **výstup** > **testy**:

**System. AggregateException: došlo k jedné nebo více chybám. ---> System. InvalidOperationException: následující TestContainer nebyl nalezen {} v Microsoft. VisualStudio. TestWindow. Controller. TestContainerProvider \<GetTestContainerAsync > d__61. MoveNext ()**

Chcete-li vyřešit tuto chybu:

- Aktualizujte vlastnost sestavení projektu testů pomocí následujícího kódu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualizace verze sady SDK TestPlatform pomocí následujícího kódu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Používání příznaků funkcí

**Jak můžu zapnout příznaky funkcí pro vyzkoušení nové funkce pro testování?**

Příznaky funkcí se používají k odeslání experimentální nebo nedokončené částech tohoto produktu avid uživatelům, kteří by chtěli poskytnout zpětnou vazbu před oficiálním dodávání funkcí. Se může omezit správnou funkci prostředí IDE. Je používejte pouze v nouzovém vývojových prostředích, jako jsou virtuální počítače. Příznaky funkcí jsou vždy použijte your vlastní rizikového nastavení. Můžete zapnout seznámit s experimentálními funkcemi, které se [příznaky funkcí rozšíření](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension), nebo prostřednictvím příkazového řádku pro vývojáře.

![Rozšíření příznak funkce](media/testex-featureflag.png)

Chcete-li zapnout příznak funkce prostřednictvím příkazového řádku pro vývojáře Visual Studio, použijte následující příkaz. Změňte cestu k instalaci sady Visual Studio na svém počítači a změňte klíč registru, který chcete, aby příznak funkce.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Příznak s stejný příkaz, můžete vypnout pomocí hodnoty 0 namísto 1 po dword.

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Vytváření a spouštění testů jednotek pro existující kód](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Testování částí kódu](unit-test-your-code.md)
- [Nejčastější dotazy týkající se testování jednotek za provozu](live-unit-testing-faq.md)
