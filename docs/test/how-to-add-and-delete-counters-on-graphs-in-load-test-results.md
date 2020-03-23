---
title: Přidání a odstranění čítačů na grafech ve výsledcích zátěžového testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: acb08edf74d3ca35a2449f588976681d679caeb4
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115188"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Postupy: Přidání a odstranění čítačů pro grafy ve výsledcích zátěžového testu

Panel **Čítače** můžete použít k přidání čítačů výkonu do grafu.

![Přidánčí počítadlo do grafu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Důležité informace o intervalu vzorkování čítače výkonu**

V nastavení spuštění zátěžového testu zvolte hodnotu pro vlastnost **Vzorkovací frekvence** na základě délky zátěžového testu. Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zvyšuje vzorkovací frekvence množství dat, která shromažďujete. Další informace naleznete v [tématu How to: Specify the sample rate](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Zde jsou některé pokyny pro vzorkovací frekvence:

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\<1 hodina|5 sekund|
|1 - 8 hodin|15 sekund|
|8 - 24 hodin|30 sekund|
|> 24 hodin|60 sekund|

**Důležité informace pro zahrnutí podrobností časování pro shromažďování dat percentilu**

V nastavení spuštění je v editoru zátěžových testů s názvem **Úložiště podrobností časování**vlastnost . Pokud je povolena vlastnost **Úložiště podrobností časování,** bude čas pro spuštění každého jednotlivého testu, transakce a stránky během zátěžového testu uložen v úložišti výsledků zátěžového testu. To umožňuje 90th a 95th percentildata, které mají být zobrazeny v **analyzátoru zátěžového testu** v testech, transakce a stránky tabulky.

Existují dvě možnosti pro povolení **vlastnosti Podrobnosti časování úložiště** ve vlastnostech nastavení spuštění s názvem **StatisticsOnly** a **AllIndividualDetails**. S oběma možnostmi jsou všechny jednotlivé testy, stránky a transakce časovány a data percentilu se počítají z jednotlivých časovacích dat. Rozdíl je, že s **StatisticsOnly** možnost, jakmile data percentilu byla vypočtena, jednotlivé časování data jsou odstraněny z úložiště. To snižuje množství místa, které je požadováno v úložišti při použití podrobnosti časování. Pokročilí uživatelé však mohou chtít zpracovat data podrobností časování jinými způsoby pomocí nástrojů SQL. Pokud se jedná o tento případ, **AllIndividualDetails** možnost by měla být použita tak, aby podrobnosti časování data je k dispozici pro toto zpracování. Navíc pokud nastavíte vlastnost **AllIndividualDetails**, pak můžete analyzovat aktivitu virtuálního uživatele pomocí grafu **virtuální aktivity uživatele** v **analyzátoru zátěžového testu** po dokončení zátěžového testu. Další informace naleznete [v tématu Analýza aktivity virtuálního uživatele v zobrazení Podrobnosti](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Množství místa, které je požadováno v úložišti výsledků zátěžového testu k uložení dat podrobností časování, může být velmi velké, zejména pro déle běžící zátěžové testy. Také čas pro uložení těchto dat v úložišti výsledků zátěžového testu na konci zátěžového testu je delší, protože tato data jsou uložena na agentech zátěžového testu, dokud zátěžový test nedokončí provádění. Po dokončení zátěžového testu jsou data uložena do úložiště. Ve výchozím nastavení je povolena vlastnost **Úložiště podrobností časování.** Pokud se jedná o problém pro testovací prostředí, můžete nastavit **úložiště podrobností časování** na **žádné**.

Další informace naleznete v [tématu Postup: Zadejte vlastnost úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Zobrazení konkrétního čítače výkonu v grafu zátěžového testu

1. Po dokončení zátěžového testu nebo po načtení výsledku testu v panelu nástrojů analyzátoru zátěžového testu zvolte **Grafy**.

     Panel **Čítače** se zobrazí v zobrazení Grafy.

    > [!NOTE]
    > Pokud panel **Čítače** není viditelný, zvolte **Zobrazit panel Čítač** na panelu nástrojů.

2. V panelu **Čítače** rozbalte uzly v hierarchii, dokud nenajdete čítač výkonu, který chcete zobrazit graficky.

     Chcete-li například zobrazit dostupnou paměť v počítači, ve kterém jsou spuštěny testy, rozbalte **položku Počítače**, rozbalte uzel počítače a **rozbalte položku Paměť**. Zobrazí se **čítač Dostupné mbajty.**

3. Zvolte graf, ve kterém chcete zobrazit čítač výkonu.

4. Klepněte pravým tlačítkem myši na čítač výkonu v panelu **Čítače** a vyberte **zobrazit čítač v grafu**.

    > [!TIP]
    > Chcete-li dočasně zastavit zobrazování dat čítače výkonu v grafu, zrušte zaškrtnutí políčka čítače výkonu v legendě. To umožňuje min, max a průměrné statistiky, které mají být stále analyzovány bez zobrazení trendové čáry v grafu. To může být užitečné, pokud graf obsahuje několik překrývajících se vykreslení čítače výkonu při analýze problémů. Další informace naleznete [v tématu Analýza zátěžových testů pomocí legendy zobrazení grafů](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Chcete-li z grafu odebrat data čítače výkonu, klepněte pravým tlačítkem myši na čítač výkonu ve sloupci **Čítač** legendy a vyberte příkaz **Odstranit**.

     \-nebo -

     Klepněte pravým tlačítkem myši na datovou čáru v grafu a vyberte **příkaz Odstranit**.

     \-nebo -

     Zvolte čítač výkonu ve sloupci **Čítač** legendy nebo datové čáry v grafu a stiskněte klávesu **Delete.**

    > [!NOTE]
    > Můžete také zvolit umístění čítače výkonu na legendu, ale ne v grafu pomocí příkazu **Přidat čítač na legendu.**

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Postup: Vytvoření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)
