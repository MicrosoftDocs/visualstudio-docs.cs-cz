---
title: Čítač sady a mezních pravidel pro zátěžové testování
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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596317"
---
# <a name="specify-counter-sets-and-threshold-rules-for-computers-in-a-load-test"></a>Určení sad čítačů a mezních pravidel pro počítače v rámci zátěžového testu

Zátěžové testy poskytují pojmenované sady čítačů, které jsou užitečné při analýze dat čítače výkonu. Sady čítačů jsou uspořádány podle technologie a aplikace, ASP.NET, aplikace .NET, služby IIS a SQL. Když vytvoříte zátěžový test pomocí **nového Průvodce zátěžovým testem**, můžete přidat počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných a důležitých sad čítačů pro zátěžový test. Můžete spravovat čítače v **editoru zátěžových testů**.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

> [!NOTE]
> Pokud jsou zátěžové testy distribuovány napříč vzdálenými počítači, jsou čítače kontroléru a agentů namapovány na sady čítačů kontrolérů a agentů. Další informace o tom, aby používaly vzdálené počítače v zátěžovém testu naleznete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Nastavení čítače se shromažďují v počítačích, že zadáte. Přidružení mezi sadou čítačů a počítače, který se používá během zátěžového testu je *sada čítačů, mapování*. Například webový server, který testujete by měl mít ASP.NET, IIS a .NET aplikace mapování sady čítače.

Ve výchozím nastavení na kontroléru a agentů se shromažďují čítače výkonu. Další informace najdete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

Je důležité přidat servery v rámci testu do seznamu počítačů, na které se mají shromažďovat čítače. Potom všechny důležité systémové se shromažďují data a monitorovat během zátěžového testu.

## <a name="tasks"></a>Tasks

|Tasks|Související témata|
|-|-----------------------|
|**Správa sad čítačů pro zátěžový test:** po vytvoření zátěžového testu můžete upravit sady čítače v editoru zátěžového testu. Správa sad čítačů zahrnuje výběr sadu počítačů, ze kterých chcete shromažďovat data o výkonu a přiřazení sadu čítačů, které mají být shromažďovány z jednotlivých počítačů. Čítače můžete spravovat v Editoru zátěžového testu.|-   [Postupy: Správa sad čítačů](../test/how-to-manage-counter-sets-using-the-load-test-editor.md)|
|**Přidání sad čítačů k zátěžovému testu:** když vytvoříte zátěžový test pomocí **nového Průvodce zátěžovým testem**, můžete přidat počáteční sadu čítačů. Ty nabízejí sadu předdefinovaných sad čítačů pro zátěžové testy. Po vytvoření zátěžového testu můžete přidat nové čítače do existujících sad čítačů pomocí editoru zátěžového testu.|-   [Postupy: přidání čítačů do sad čítačů](../test/how-to-add-counters-to-counter-sets-using-the-load-test-editor.md)<br />-   [Postupy: Přidání vlastních sad čítačů](../test/how-to-add-custom-counter-sets-using-the-load-test-editor.md)|
|**Zadejte mezního pravidla pomocí čítačů pro zátěžový test:** pravidlo mezní hodnoty je pravidlo, které je nastavena na jednotlivé čítače na sledování využití systémových prostředků během zátěžového testu. Definice sady čítače obsahují předdefinované prahovou hodnotu pravidla pro mnoho klíčových čítačů výkonu. Mezní pravidla v zátěžových testech porovnávají hodnotu čítače výkonu s konstantní hodnotou nebo jinou hodnotou čítače výkonu.|-   [Postupy: Přidání mezního pravidla](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)|
|**Přiřadit popisné názvy počítačů, které čítačem jsou mapovány sady:** můžete přidat značky počítače, které vám umožní použít popisným názvem počítače. Značky jsou zobrazeny v **mapování sady čítačů** uzel pro strom v editoru zátěžového testu. Důležitější, značky se zobrazí v sestavy aplikace Excel, které pomáhají zúčastněné strany identifikovat jakou roli má počítač v zátěžovém testu, například "Server1 Web v lab2" nebo "SQL Server2 Phoenixu".<br /><br /> Další informace najdete v tématu [sestavy zátěžové testy s výsledky pro porovnávání testů a analýzu trendů](../test/compare-load-test-results.md).||

## <a name="use-counter-sets"></a>Použití sad čítačů

Nástroje testu zatížení můžete shromažďovat a graph údaje o výkonu pomocí čítačů v čase. Při spuštění zátěžového testu jsou shromážděna data čítače v intervalech zadané uživatelem. Další informace najdete v tématu [postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md). Čítače lze zobrazit v době běhu nebo je můžete zobrazit po spuštění pomocí zátěžového testu *Analyzéru zátěžového testu*.

Čítač shromáždění dat na serveru a na každém počítači ve kterém je test spuštěn. Pokud jste nastavili skupinu počítačů agenta na základě které chcete spustit testy, se v těchto počítačích čítače shromažďují také.

Existují tři kategorie čítačů: procent, počty a průměr. Některé příklady jsou % využití procesoru, počtu uzamčení systému SQL Server a IIS požadavků za sekundu.

![Sady čítačů zátěžového testu](../test/media/loadtestcountersets.png)

Údaje o výkonu pro jednotlivé požadavky HTTP je hlášených počítači, který spustí test. například počítači agenta. Pro žádosti může monitorovat data, například průměrná doba do prvního bajtu, doby odezvy a počet požadavků za sekundu.

K usnadnění shromažďování dat o výkonu na webovém serveru, Visual Studio Enterprise také poskytuje předdefinované, pojmenované čítačů, založené na technologii pro použití v zátěžových testech. Tyto sady jsou užitečné při analýze serveru, na kterém běží služby IIS, ASP.NET nebo SQL Server. Není k dispozici v sadě výchozí čítače čítačů lze přidat pomocí editoru zátěžových testů. Je důležité, přidejte do vašeho zátěžového testu, abyste měli jistotu, že můžete monitorovat využití prostředků na těchto počítačích počítače nebo servery v rámci testu. Další informace najdete v tématu [postupy: Správa sad čítačů](../test/how-to-manage-counter-sets-using-the-load-test-editor.md).

Analýza výsledků zátěžových často vyžaduje znalosti domény ke konkrétní oblasti pokud chcete zjistit, jaká data shromažďovat, kde mají sadu mezní pravidla a jak zjistit, kdy měření odráží konkrétní problém v aplikaci. Další informace najdete v tématu [o prahovou hodnotu pravidla](#about-threshold-rules).

### <a name="performance-counter-sampling-interval-considerations"></a>Aspekty interval vzorkování čítače výkonu

Vyberte příslušnou hodnotu **vzorkovací frekvence** vlastnost v zátěžovém testu běhu na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pěti sekund, vyžaduje více místa v databázi výsledků zátěžového testu. Pro delší zátěžové testy vzorkovací frekvence snižuje objem dat shromážděných. Další informace najdete v tématu [postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Následují některé pokyny pro vzorkovací frekvence.

|Doba trvání zátěžového testu|Doporučené vzorkovací frekvence|
|-|-----------------------------|
|\< 1 hodina|5 sekund|
|1−8 hodin|15 sekund|
|8−24 hodin|30 sekund|
|> 24 hodin|60 sekund|

## <a name="store-performance-data"></a>Údaje o výkonu Store

Při spuštění zátěžového testu, data čítače výkonu se shromažďují a ukládají v *úložiště výsledků testu zátěže*. Další informace najdete v tématu [spravovat výsledky zátěžového testu v zátěžového testu úložiště výsledků](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="about-threshold-rules"></a>O pravidlech prahová hodnota

A *pravidlo mezní hodnoty* je pravidlo, které je nastavena na jednotlivé čítače na sledování využití systémových prostředků během zátěžového testu. Definice sady čítače obsahují předdefinované prahovou hodnotu pravidla pro mnoho klíčových čítačů výkonu. Další informace najdete v tématu [sad čítačů pomocí, který pomáhá při analýze dat čítače výkonu v zátěžových testech](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md).

## <a name="threshold-rules-and-levels"></a>Mezní pravidla a úrovně

Když vytvoříte mezní pravidla v zátěžových testech, zvolte mezi dvěma typy pravidel:

Porovnat konstanty&mdash;porovnat hodnotu čítače výkonu s konstantní hodnotou.

Porovnat počítadla&mdash;porovnat hodnotu čítače výkonu s jinou hodnotou čítače výkonu.

Při vytváření pravidla prahové hodnoty, můžete také nastavit limity pro pravidlo. Úrovně jsou prahovou hodnotu upozornění a kritická prahová hodnota. Při zobrazení spuštění zátěžového testu mezních hodnot upozornění úrovně jsou označeny žlutým symbolem a porušení kritické prahové hodnoty úrovně jsou označeny červenou symbol.

## <a name="the-alert-if-over-property"></a>Vlastnost upozornění, pokud přesáhne

Nastavte **upozornění, pokud přesáhne** vlastnost **True** k označení, že překročení mezní hodnoty je nějaký problém. Například, pokud pravidlo mezní hodnoty je nastavena na **% času procesoru**, a vy chcete dostat oznámení, pokud je hodnota větší než 90, použijte **konstanta porovnání** typ pravidla, nastavte **kritická prahová hodnota Hodnota** do 90 a nastavte **upozornění, pokud přesáhne** k **True**.

Nastavte **upozornění, pokud přesáhne** vlastnost **False** označuje, že snížení pod mezní hodnotu k problému. Například, pokud pravidlo mezní hodnoty je nastavena na **požadavků za sekundu**, a vy chcete dostat oznámení, pokud je hodnota nižší než 50, použijte **konstanta porovnání** typ pravidla, nastavte **kritickou prahovou hodnotu** 50 a nastavte **upozornění, pokud přesáhne** k **False**.

## <a name="see-also"></a>Viz také:

- [Postupy: Přidání mezního pravidla](../test/how-to-add-a-threshold-rule-using-the-load-test-editor.md)
- [Analýza překročení mezních pravidel](../test/analyze-threshold-rule-violations-in-load-tests.md)
