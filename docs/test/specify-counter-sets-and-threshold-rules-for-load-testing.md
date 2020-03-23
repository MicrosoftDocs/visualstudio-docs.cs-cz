---
title: Sady čítačů a prahová pravidla pro zátěžové testování
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- counters, counter sets
- load tests, thresholds
- counter sets
- load tests, performance
- load tests, counter sets
- load tests, threshold rules
ms.assetid: 9e14d955-f3a4-4717-bbfe-7f08cdda5678
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 440bc01b52269c477d9d2f2194fd831041f1d20d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596317"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Určení sad čítačů a prahových hodnot pro počítače v zátěžovém testu

Zátěžové testy poskytují pojmenované sady čítačů, které jsou užitečné při analýze dat čítače výkonu. Sady čítačů jsou uspořádány podle technologie a zahrnují aplikace, ASP.NET, .NET aplikace, IIS a SQL. Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných a důležitých sad čítačů pro zátěžový test. Čítače spravujete v **Editoru zátěžových testů**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, jak používat vzdálené počítače v zátěžovém testu, naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Sady čítačů jsou shromažďovány v počítačích, které zadáte. Přidružení mezi sadou čítačů a počítačem, který se používá během zátěžového testu, je *mapa sady čítačů*. Webový server, který testujete, může mít například mapování sad ASP.NET, IIS a čítačů aplikací .NET.

Ve výchozím nastavení jsou shromažďovány čítače výkonu na řadiči a agenty. Další informace naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Je důležité přidat testované servery do seznamu počítačů, ve kterých mají být shromažďovány čítače. Poté jsou všechna důležitá systémová data shromažďována a sledována během zátěžového testu.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Správa sad čítačů pro zátěžový test:** Po vytvoření zátěžového testu můžete upravit sadu čítačů v Editoru zátěžového testu. Správa sad čítačů zahrnuje výběr sady počítačů, ze kterých chcete shromažďovat data o výkonu, a přiřazení sady čítačů, které se mají shromažďovat z každého jednotlivého počítače. Správu čítače v editoru zátěžového testu.|-   [Postup: Správa sad čítačů](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Přidejte sady čítačů do zátěžového testu:** Při vytváření zátěžového testu pomocí **Průvodce novým zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Po vytvoření zátěžového testu můžete přidat nové čítače do existujících sad čítačů pomocí Editoru zátěžového testu.|-   [Postup: Přidání čítačů k sadám čítačů](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Postup: Přidání vlastních sad čítačů](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Zadejte pravidlo prahové hodnoty pomocí čítačů pro zátěžový test:** Pravidlo prahové hodnoty je pravidlo, které je nastaveno na jednotlivém čítači výkonu pro sledování využití systémových prostředků během zátěžového testu. Definice sady čítačů obsahují předdefinovaná prahová pravidla pro mnoho čítačů výkonu klíče. Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.|-   [Postup: Přidání pravidla prahové hodnoty](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Přiřazení popisných názvů počítačům, na které jsou mapovány sady čítačů:** Můžete přidat značky počítače, které umožňují použít snadno rozpoznaný název v počítači. Značky jsou zobrazeny v uzlu **Mapování sad čítačů** pro strom v Editoru zátěžového testu. Ještě důležitější je, že značky jsou zobrazeny v sestavách aplikace Excel, které pomáhají zúčastněným stranám určit, jakou roli má počítač v zátěžovém testu, například "Webový server1 v laboratoři2" nebo "SQL Server2 v kanceláři Phoenix".<br /><br /> Další informace naleznete [v tématu Zpráva o výsledcích zátěžových testů pro porovnání testů nebo analýzu trendů](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Použití sad čítačů

Nástroje zátěžového testu shromažďují a grafují údaje o výkonu pomocí čítačů v průběhu času. Data čítačů jsou shromažďována v intervalech zadaných uživatelem během spuštění zátěžového testu. Další informace naleznete v [tématu How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Můžete zobrazit čítače za běhu nebo je můžete zobrazit po spuštění zátěžového testu pomocí *analyzátoru zátěžového testu*.

Data čítačů jsou shromažďována na serveru a v libovolném počítači, ve kterém je test spuštěn. Pokud jste nastavili sadu počítačů agentů, na kterých chcete spustit testy, čítače jsou shromažďovány na těchto počítačích také.

Existují tři kategorie čítačů: procenta, počty a průměry. Některé příklady jsou % využití procesoru, počet uzamčení serveru SQL Server a požadavky služby IIS za sekundu.

![Sady čítačů zátěžových zkoušek](../test/media/loadtestcountersets.png)

Údaje o výkonu pro jednotlivé požadavky HTTP jsou hlášeny počítačem, který spouští test. například počítač agenta. U požadavků můžete sledovat data, jako je například průměrná doba do prvního bajtu, doba odezvy a požadavky za sekundu.

Chcete-li usnadnit shromažďování dat o výkonu na webovém serveru, Visual Studio Enterprise také poskytuje předdefinované, pojmenované sady čítačů, založené na technologii pro použití v zátěžových testech. Tyto sady jsou užitečné při analýze serveru, na který je spuštěna služba IIS, ASP.NET nebo SQL Server. Čítače, které nejsou k dispozici ve výchozí sadě čítačů, lze přidat pomocí Editoru zátěžového testu. Je důležité přidat testované počítače nebo servery do zátěžového testu a ujistit se, že můžete sledovat využití prostředků v těchto počítačích. Další informace naleznete v [tématu How to: Manage counter sets](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analýza výsledků zatížení často vyžaduje znalost určité oblasti specifické pro doménu, aby bylo možné vědět, jaká data shromažďovat, kde nastavit prahová pravidla a jak zjistit, kdy měření odráží konkrétní problém v aplikaci. Další informace naleznete v tématu [O pravidlech prahových hodnot](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Aspekty intervalu intervalu vzorkování čítačů výkonu

Vyberte příslušnou hodnotu pro vlastnost **Vzorkovací frekvence** v nastavení spuštění zátěžového testu na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zvyšuje vzorkovací frekvence množství shromážděných dat. Další informace naleznete v [tématu How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Níže jsou uvedeny některé pokyny pro vzorkovací frekvence.

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\<1 hodina|5 sekund|
|1−8 Hodin|15 sekund|
|8−24 hodin|30 sekund|
|> 24 hodin|60 sekund|

## <a name="store-performance-data"></a>Ukládání dat o výkonu

Během spuštění zátěžového testu jsou data čítače výkonu shromažďována a uložena v *úložišti výsledků zátěžového testu*. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>O pravidlech prahových hodnot

*Pravidlo prahové hodnoty* je pravidlo, které je nastaveno na jednotlivém čítači výkonu pro sledování využití systémových prostředků během zátěžového testu. Definice sady čítačů obsahují předdefinovaná prahová pravidla pro mnoho čítačů výkonu klíče. Další informace naleznete [v tématu Použití sad čítačů k analýze dat čítačů výkonu v zátěžových testech](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Prahová pravidla a úrovně

Při vytváření prahových hodnot ových pravidel v zátěžových testech si vyberete mezi dvěma typy pravidel:

Porovnat&mdash;hodnotu čítače výkonu porovnáním s konstantní hodnotou.

Porovnat čítače&mdash;Porovnejte hodnotu čítače výkonu s jinou hodnotou čítače výkonu.

Při vytváření pravidel prahové hodnoty také nastavíte úrovně pravidla. Úrovně jsou prahová hodnota pro varování a kritická prahová hodnota. Při zobrazení spuštění zátěžového testu jsou porušení prahové hodnoty úrovně upozornění označeny žlutým symbolem a porušení prahové hodnoty kritické úrovně je označeno červeným symbolem.

## <a name="the-alert-if-over-property"></a>Vlastnost Výstraha při překročení

Nastavte **vlastnost Výstraha pokud je přes** **true** označující, že překročení prahové hodnoty je problém. Pokud je například pravidlo prahové hodnoty nastaveno na **% času procesoru**a chcete být upozorněni, pokud je hodnota větší než 90, použijte typ pravidla **Porovnat konstantu,** nastavte **hodnotu kritické prahové hodnoty** na 90 a nastavte **výstrahu, pokud je více,** na **hodnotu True**.

Nastavte **vlastnost Výstraha pokud je přes** **na False,** která označuje, že pád pod prahovou hodnotu je problém. Pokud je například pravidlo prahové hodnoty nastaveno na **požadavky/s**a chcete být upozorněni, pokud je hodnota nižší než 50, použijte typ pravidla **Porovnat konstantu,** nastavte **hodnotu kritické prahové hodnoty** na 50 a nastavte **výstrahu, pokud je více,** na **hodnotu False**.

## <a name="see-also"></a>Viz také

- [Postup: Přidání pravidla prahové hodnoty](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analyzovat porušení pravidel prahových hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
