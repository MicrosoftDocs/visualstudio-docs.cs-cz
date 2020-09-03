---
title: Sady čítačů a pravidla prahové hodnoty pro zátěžové testování
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596317"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Určení sad čítačů a mezních pravidel pro počítače v zátěžovém testu

Zátěžové testy poskytují pojmenované sady čítačů, které jsou užitečné při analýze dat čítače výkonu. Sady čítačů jsou uspořádány podle technologie a zahrnují aplikace, ASP.NET, aplikace .NET, službu IIS a SQL. Když vytvoříte zátěžový test pomocí **nového Průvodce zátěžovým testem**, přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných a důležitých sad čítačů pro zátěžový test. Čítače můžete spravovat v **Editor zátěžového testu**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o použití vzdálených počítačů v rámci zátěžového testu naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Sady čítačů jsou shromažďovány na počítačích, které zadáte. Přidružení mezi sadou čítačů a počítačem, který se používá během zátěžového testu, je *Mapa sady čítačů*. Například webový server, který testujete, může mít mapování sady čítačů aplikací pro ASP.NET, IIS a .NET.

Ve výchozím nastavení jsou čítače výkonu shromažďovány na řadiči a agentech. Další informace naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

Je důležité přidat testované servery do seznamu počítačů, ve kterých se mají shromáždit čítače. Pak jsou během zátěžového testu shromažďována a sledována veškerá důležitá systémová data.

## <a name="tasks"></a>Úlohy

|Úlohy|Související témata|
|-|-----------------------|
|**Správa sad čítačů pro zátěžový test:** Po vytvoření zátěžového testu můžete upravit sadu čítačů v Editor zátěžového testu. Správa sad čítačů zahrnuje výběr sady počítačů, ze kterých chcete shromažďovat údaje o výkonu a přiřazování sady čítačů pro shromažďování dat z jednotlivých počítačů. Čítače můžete spravovat v Editor zátěžového testu.|-   [Postupy: Správa sad čítačů](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Přidejte sady čítačů do zátěžového testu:** Při vytváření zátěžového testu s **novým Průvodce zátěžovým testem**přidáte počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Po vytvoření zátěžového testu můžete přidat nové čítače do existujících sad čítačů pomocí Editor zátěžového testu.|-   [Postupy: Přidání čítačů do sad čítačů](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Postupy: Přidání vlastních sad čítačů](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Určete prahové pravidlo pomocí čítačů pro zátěžový test:** Pravidlo prahové hodnoty je pravidlo, které je nastaveno na jednotlivé čítače výkonu pro sledování využití systémových prostředků během zátěžového testu. Definice sady čítačů obsahují předdefinovaná pravidla prahové hodnoty pro mnoho klíčových čítačů výkonu. Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.|-   [Postupy: Přidání prahového pravidla](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Přiřaďte počítačům popisné názvy, na které jsou namapované sady čítačů:** Můžete přidat značky počítačů, které vám umožní použít snadno rozpoznaný název počítače. Značky se zobrazí v uzlu **mapování sady čítačů** pro strom v Editor zátěžového testu. Důležitější je, že značky se zobrazí v sestavách aplikace Excel, které pomůžou účastníkům určit, jakou roli má počítač v rámci zátěžového testu, například "Web Server1 v lab2" nebo "SQL Server2 v Phoenixu pobočce".<br /><br /> Další informace naleznete v tématu [výsledky testů zatížení sestav pro porovnání testů nebo analýzy trendů](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Použití sad čítačů

Nástroje zátěžového testu shromažďují a grafují data o výkonu pomocí čítačů v průběhu času. Data čítače se shromažďují v intervalech zadaných uživatelem během spuštění zátěžového testu. Další informace najdete v tématu [Postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Čítače můžete zobrazit v době běhu nebo je můžete zobrazit po spuštění zátěžového testu pomocí *analyzátoru zátěžového testu*.

Data čítačů se shromažďují na serveru a na všech počítačích, na kterých je spuštěný test. Pokud jste nastavili sadu počítačů agenta, na kterých budou testy spuštěny, jsou tyto čítače shromažďovány i na těchto počítačích.

Existují tři kategorie čítačů: procenta, počty a průměry. Mezi příklady patří% využití CPU, SQL Server počet zámků a požadavky služby IIS za sekundu.

![Sady čítačů zátěžového testu](../test/media/loadtestcountersets.png)

Údaje o výkonu pro jednotlivé požadavky HTTP jsou hlášeny počítačem, který spouští test. například počítač agenta. V případě požadavků můžete monitorovat data, jako je například průměrná doba do prvního bajtu, doba odezvy a požadavky za sekundu.

Pro usnadnění shromažďování dat o výkonu na webovém serveru Visual Studio Enterprise také poskytuje předdefinované pojmenované sady čítačů založené na technologii pro použití v zátěžových testech. Tyto sady jsou užitečné při analýze serveru, na kterém běží služba IIS, ASP.NET nebo SQL Server. Čítače, které nejsou zadány ve výchozí sadě čítačů, lze přidat pomocí Editor zátěžového testu. Je důležité, abyste přidali počítače nebo servery pod testem do zátěžového testu, abyste se ujistili, že můžete monitorovat používání prostředků na těchto počítačích. Další informace najdete v tématu [Postupy: Správa sad čítačů](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analýza výsledků běhu zatížení často vyžaduje znalosti konkrétní oblasti v doméně, aby bylo možné zjistit, jaká data se mají shromáždit, kde můžete nastavit mezní pravidla a jak zjistit, kdy měření odráží konkrétní problém v aplikaci. Další informace najdete v tématu [o mezních pravidlech](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Posouzení intervalu vzorkování čítače výkonu

V nastavení spuštění zátěžového testu v závislosti na délce zátěžového testu vyberte vhodnou hodnotu pro vlastnost **vzorkovací frekvence** . Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zkracuje vzorkovací frekvence omezení množství shromažďovaných dat. Další informace najdete v tématu [Postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Níže jsou uvedeny některé pokyny pro vzorkovací sazby.

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\< 1 hodina|5 sekund|
|1 − 8 hodin|15 sekund|
|8 − 24 hodin|30 sekund|
|> 24 hodin|60 sekund|

## <a name="store-performance-data"></a>Ukládat údaje o výkonu

Během běhu zátěžového testu se data čítače výkonu shromažďují a ukládají do *úložiště load výsledky testů*. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti výsledků zátěžového testu](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>O prahová pravidla

*Pravidlo prahové hodnoty* je pravidlo, které je nastaveno na jednotlivé čítače výkonu pro sledování využití systémových prostředků během zátěžového testu. Definice sady čítačů obsahují předdefinovaná pravidla prahové hodnoty pro mnoho klíčových čítačů výkonu. Další informace najdete v tématu [použití sad čítačů pro snadnější analýzu dat čítače výkonu v zátěžových testech](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Prahová pravidla a úrovně

Při vytváření mezních pravidel v zátěžových testech si zvolíte mezi dvěma typy pravidel:

Porovnat konstantní &mdash; porovnání hodnoty čítače výkonu s konstantní hodnotou.

Porovnání čítačů &mdash; porovnávají hodnotu čítače výkonu s jinou hodnotou čítače výkonu.

Když vytváříte prahová pravidla, nastavíte také úrovně pro pravidlo. Úrovně jsou prahovou hodnotou upozornění a kritickou prahovou hodnotou. Při zobrazení zátěžového testu jsou překročení prahové hodnoty úrovně upozornění označeny žlutým symbolem a porušení prahové hodnoty kritické úrovně je označeno červeným symbolem.

## <a name="the-alert-if-over-property"></a>Výstraha, pokud je vlastnost překročena

Pokud chcete určit, že překročení prahové hodnoty je problém, nastavte vlastnost **Alert** na **hodnotu true** . Pokud je například pravidlo prahové hodnoty nastaveno na **% času procesoru**a chcete-li být upozorněni, je-li hodnota větší než 90, použijte typ pravidla **konstanta Compare** , nastavte **kritickou prahovou hodnotu** na 90 a nastavte **výstrahu, pokud** je nastavena na **hodnotu true**.

Nastavte **výstrahu, pokud** má vlastnost over **hodnotu false** , aby označovala, že se jedná o problém, který je pod prahovou hodnotou. Pokud je například pravidlo prahové hodnoty nastaveno na **požadavky za sekundu**a chcete být upozorněni, pokud je hodnota nižší než 50, použijte typ pravidla **konstanta Compare** , nastavte **kritickou prahovou hodnotu** na 50 a nastavte **výstrahu, pokud má být překročena** hodnota **false**.

## <a name="see-also"></a>Viz také

- [Postupy: Přidání prahového pravidla](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analýza porušení pravidel mezních hodnot](../test/analyze-threshold-rule-violations-in-load-tests.md)
