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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75846811"
---
# <a name="visual-studio-test-explorer-faq"></a>Nejčastější dotazy průzkumníka testů sady Visual Studio
::: moniker range=">=vs-2019"

## <a name="where-is-group-by-traits-in-visual-studio-2019"></a>Kde je skupina podle vlastností v Sadě Visual Studio 2019?
Toto seskupení vlastností bylo přesunuto na sloupec. S vícevrstvou a přizpůsobitelnou hierarchií ve Visual Studiu 2019 verze 16.2 jsme si mysleli, že zahrnutí vlastností jako seskupení vytvořilo nepotřebnou vizuální složitost. Rozhodně nasloucháme zpětné vazbě na tento design! https://developercommunity.visualstudio.com/content/problem/588029/no-longer-able-to-group-by-trait-in-test-explorer.html

Prozatím můžete kliknout pravým tlačítkem myši na sloupec v Průzkumníkovi testů a vybrat sloupce. Zkontrolujte sloupec Vlastnosti a zobrazí se v Průzkumníkovi testů. Nyní můžete filtrovat tento sloupec podle vlastností, které vás zajímají.

![Zobrazení sloupce](media/vs-2019/trait-column.png)
![Vlastnost: Filtrovat sloupec vlastností](media/vs-2019/trait-column-filter.png)
::: moniker-end

## <a name="dynamic-test-discovery"></a>Dynamické zjišťování testů

**Průzkumník testů nezjišťuje moje testy, které jsou dynamicky definovány. (Například teorie, vlastní adaptéry, vlastní vlastnosti, #ifdefs atd.) Jak mohu tyto testy objevit?**

::: moniker range=">=vs-2019"
Sestavte svůj projekt pro spuštění zjišťování na základě sestavení.
::: moniker-end
::: moniker range="vs-2017"
Sestavte svůj projekt a ujistěte se, že zjišťování na základě sestavení je zapnuto v **testu** **možností** > **nástrojů** > .
::: moniker-end
[Zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) je zjišťování testů založených na zdrojích. Nemůže zjistit testy, které používají teorie, vlastní adaptéry, `#ifdef` vlastní vlastnosti, příkazy a další, protože jsou definovány za běhu. Sestavení je vyžadováno pro tyto testy přesně nalezeny. Ve Visual Studiu 2017 verze 15.6 a novější, zjišťování založené na sestavení (tradiční objevitel) běží pouze po sestavení. Toto nastavení znamená, že zjišťování testů v reálném čase najde při úpravách co nejvíce testů a zjišťování založené na sestavení umožňuje dynamicky definované testy, které se zobrazí po sestavení. Zjišťování testů v reálném čase zlepšuje odezvu, ale stále umožňuje získat úplné a přesné výsledky po sestavení.

## <a name="test-explorer--plus-symbol"></a>Symbol Průzkumníka testů '+' (plus)

**Co znamená symbol +(plus), který se zobrazí v horním řádku Průzkumníka testů?**

Symbol '+' (plus) označuje, že další testy mohou být zjištěny po sestavení při spuštění zjišťování na základě sestavení. Tento symbol se zobrazí, pokud jsou v projektu zjištěny dynamicky definované testy.

![Plus řádek souhrnu symbolů](media/testex-plussymbol.png)

::: moniker range="vs-2017"
## <a name="assembly-based-discovery"></a>Zjišťování založené na sestavení

**Zjišťování založené na sestavení již nepracuje pro můj projekt. Jak ji znovu zapnu?**

Přejděte na **nástroje** > **Možnosti** > **Test** a zaškrtněte políčko **navíc zjišťovat testy z sestavení po sestavení.**

![Možnost založená na sestavení](media/testex-toolsoptions.png)
::: moniker-end

## <a name="real-time-test-discovery"></a>Zjišťování testů v reálném čase

**Testy se nyní zobrazí v Průzkumníku testů při psaní, aniž by bylo třeba vytvořit svůj projekt. Co se změnilo?**

Tato funkce se nazývá [zjišťování testů v reálném čase](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/). Používá analyzátor Roslyn k nalezení testů a naplnění Průzkumníka testů v reálném čase, aniž byste museli vytvářet projekt. Další informace o chování zjišťování testů pro dynamicky definované testy, jako jsou teorie nebo vlastní vlastnosti, naleznete [v tématu Dynamické zjišťování testů](#dynamic-test-discovery).

## <a name="real-time-test-discovery-compatibility"></a>Kompatibilita zjišťování testů v reálném čase

**Jaké jazyky a testovací rámce mohou používat zjišťování testů v reálném čase?**

[Zjišťování testů](https://devblogs.microsoft.com/dotnet/real-time-test-discovery/) v reálném čase funguje pouze pro spravované jazyky (C# a Visual Basic), protože je vytvořen pomocí kompilátoru Roslyn. Pro tuto chvíli zjišťování testů v reálném čase funguje pouze pro rozhraní xUnit, NUnit a MSTest.

## <a name="test-explorer-logs"></a>Protokoly Průzkumníka testů

**Jak lze zapnout protokoly pro Průzkumníka testů?**

Přejděte do části **Nástroje–** > **test** **možností** > a najděte tam oddíl Protokolování.

## <a name="uwp-test-discovery"></a>Zjišťování testu UPW

**Proč nejsou moje testy v projektech UPW zjištěny, dokud nenasadím svou aplikaci?**

Testy UPW cílí na jiný běhový čas při nasazení aplikace. To znamená, že přesně najít testy pro projekty UPW je třeba nejen k sestavení projektu, ale také nasadit.

## <a name="test-explorer-sorting"></a>Řazení průzkumníka testů

**Jak fungují výsledky testů řazení v zobrazení hierarchie?**

Zobrazení hierarchie seřadí testy abecedně na rozdíl od výsledku. Druhá skupina podle nastavení obvykle seřadí výsledky testů podle výsledku a pak abecedně. Porovnání naleznete v různých možnostech podle skupiny na následujícím obrázku. Můžete poskytnout zpětnou vazbu o návrhu [v tomto problému GitHub](https://github.com/Microsoft/vstest/issues/1425).

![Příklady řazení](media/testex-sortingex.png)

## <a name="test-explorer-hierarchy-view"></a>Zobrazení hierarchie Průzkumníka testů

**V zobrazení hierarchie jsou předány, se nezdařilo, přeskočeny ikony vedle seskupení nadřazených uzlů. Co tyto ikony znamenají?**

Ikony vedle aplikace Project, Obor názvů a Seskupení tříd zobrazují stav testů v rámci tohoto seskupení. Podívejte se na následující tabulku.

![Ikony hierarchie průzkumníka testů](media/testex-hierarchyicons.png)

## <a name="search-by-file-path"></a>Hledání podle cesty k souboru

**Ve vyhledávacím poli Průzkumníka testů již není filtr Cesta k souboru.**

Filtr cesty k souboru ve vyhledávacím poli **Průzkumníka testů** byl odebrán ve Visual Studiu 2017 verze 15.7. Tato funkce měla nízké využití a Průzkumník testů může rychleji načíst testovací metody vynecháním této funkce. Pokud tato změna přeruší tok vývoje, dejte nám vědět odesláním zpětné vazby na [komunitu vývojářů](https://developercommunity.visualstudio.com/).

## <a name="remove-undocumented-interfaces"></a>Odebrání nedokumentovaných rozhraní

**Některá testovací prostředí API již nejsou k dispozici v sadě Visual Studio 2019. Co se změnilo?**

V sadě Visual Studio 2019 budou odebrána některá testovací okna, která byla dříve označena jako veřejná, ale nikdy nebyla oficiálně zdokumentována. Byly označeny jako "zastaralé" v sadě Visual Studio 2017 poskytnout údržbáři rozšíření včasné varování. Pokud je nám známo, jen velmi málo rozšíření našel tato api a vzal závislost na nich. Patří `IGroupByProvider`mezi `IGroupByProvider<T>` `KeyComparer`ně `ISearchFilter` `ISearchFilterToken`, `ISearchToken`, `SearchFilterTokenType`, , , a . Pokud tato změna ovlivní vaše rozšíření, dejte nám vědět podáním chyby v [komunitě vývojářů](https://developercommunity.visualstudio.com).

## <a name="test-adapter-nuget-reference"></a>Testovací adaptér NuGet odkaz

**Ve Visual Studiu 2017 verze 15.8 jsou moje testy zjištěny, ale nespustí.**

Všechny testovací projekty musí obsahovat jejich .NET testovací adaptér NuGet odkaz v jejich souboru .csproj. Pokud tomu tak není, následující testovací výstup se zobrazí v projektu, pokud zjišťování rozšíření testovacího adaptéru je spuštěna po sestavení, nebo pokud se uživatel pokusí spustit vybrané testy:

**Testovací {} projekt neodkazuje na žádný adaptér .NET NuGet. Zjišťování nebo spuštění testu nemusí pro tento projekt fungovat. Doporučuje se odkazovat nuget testovací adaptéry v každém testovacím projektu .NET v řešení.**

Namísto použití rozšíření testovacíadaptér, projekty jsou nutné k použití testovací adaptér NuGet balíčky. Tento požadavek výrazně zlepšuje výkon a způsobuje méně problémů s průběžnou integrací. Další informace o vyřazení rozšíření testovacího adaptéru .NET naleznete v [poznámkách k verzi](/visualstudio/releasenotes/vs2017-relnotes-v15.8#testadapterextension).

::: moniker range="vs-2017"
> [!NOTE]
> Pokud používáte testovací adaptér NUnit 2 a nemůžete migrovat na testovací adaptér NUnit 3, můžete toto nové chování zjišťování vypnout v sadě Visual Studio verze 15.8 v**testu****možností** >  **nástrojů** > .

![Chování adaptéru Aplikace Test Explorer v možnostech nástrojů](media/testex-adapterbehavior.png)
::: moniker-end

## <a name="uwp-testcontainer-was-not-found"></a>UWP TestContainer nebyl nalezen.

**Moje testy UPW se již neprovádějí ve Visual Studiu 2017 verze 15.7 a novější.**

Nedávné testovací projekty UPW určují vlastnost sestavení testovací platformy, která umožňuje lepší výkon pro identifikaci testovacích aplikací. Pokud máte testovací projekt UPW, který byl inicializován před Visual Studio verze 15.7, může se zobrazit tato chyba ve **výstupních** > **testech**:

**System.AggregateException: Došlo k jedné nebo více chybám. ---> System.InvalidOperationException: Následující TestContainer {} nebyl nalezen na adrese Microsoft.VisualStudio.TestWindow.Controller.TestContainerProvider \<GetTestContainerAsync>d__61.MoveNext()**

Chcete-li tuto chybu opravit,

- Aktualizujte vlastnost sestavení testovacího projektu pomocí následujícího kódu:

```XML
<UnitTestPlatformVersion Condition="'$(UnitTestPlatformVersion)' == ''">$(VisualStudioVersion)</UnitTestPlatformVersion>
```

- Aktualizujte verzi sady TestPlatform SDK pomocí následujícího kódu:

```XML
<SDKReference Include="TestPlatform.Universal, Version=$(UnitTestPlatformVersion)" />
```

## <a name="using-feature-flags"></a>Použití příznaků prvků

**Jak lze zapnout příznaky funkcí a vyzkoušet si nové testovací funkce?**

Vlaječky funkcí se používají k odeslání experimentálních nebo nedokončených částí produktu vášnivým uživatelům, kteří by chtěli poskytnout zpětnou vazbu před oficiálním odesláním funkcí. Mohou destabilizovat vaše ide zkušenosti. Používejte je pouze v bezpečných vývojových prostředích, jako jsou virtuální počítače. Příznaky funkcí jsou vždy nastavení použití na vlastní riziko. Experimentální funkce můžete zapnout s [rozšířením příznaků funkcí](https://marketplace.visualstudio.com/items?itemName=PaulHarrington.FeatureFlagsExtension)nebo pomocí příkazového řádku vývojáře.

![Rozšíření příznaku funkce](media/testex-featureflag.png)

Chcete-li zapnout příznak funkce prostřednictvím příkazového řádku vývojáře sady Visual Studio, použijte následující příkaz. Změňte cestu k místu, kde je visual studio nainstalována v počítači, a změňte klíč registru na příznak funkce, který chcete.

```shell
vsregedit set “C:\Program Files (x86)\Microsoft Visual Studio\Preview\Enterprise" HKLM FeatureFlags\TestingTools\UnitTesting\HierarchyView Value dword 1
```

> [!NOTE]
> Příznak můžete vypnout stejným příkazem pomocí hodnoty 0 namísto 1 za dword.

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting?displayProperty=fullName>
- [Vytvoření a spuštění testů částí pro existující kód](https://msdn.microsoft.com/e8370b93-085b-41c9-8dec-655bd886f173)
- [Testování částí kódu](unit-test-your-code.md)
- [Nejčastější dotazy týkající se testování živých částí](live-unit-testing-faq.md)
