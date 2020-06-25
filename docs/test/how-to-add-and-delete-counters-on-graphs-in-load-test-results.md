---
title: Přidávání a odstraňování čítačů v grafech v načtení Výsledky testů
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load test results graphs, adding counters
- load test results graph
- load test, results graph
- load test results, graphs
ms.assetid: 81536233-1962-40d9-9511-0b4633814d90
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2b2cefc56d299c9ec917aea555aec1cd9ca53887
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288465"
---
# <a name="how-to-add-and-delete-counters-on-graphs-in-load-test-results"></a>Postupy: Přidání a odstranění čítačů pro grafy ve výsledcích zátěžového testu

K přidání čítačů výkonu do grafu můžete použít panel **čítače** .

![Přidaný čítač do grafu](../test/media/ltest_selectcounter.png)

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

**Posouzení intervalu vzorkování čítače výkonu**

V nastavení spuštění zátěžového testu v závislosti na délce zátěžového testu vyberte hodnotu vlastnosti **vzorkovací frekvence** . Menší vzorkovací frekvence, jako je například výchozí hodnota pět sekund, vyžaduje více místa v databázi výsledků zátěžového testu. U delších zátěžových testů zkracuje vzorkovací frekvence omezení množství shromažďovaných dat. Další informace najdete v tématu [Postupy: určení vzorkovací frekvence](../test/how-to-specify-the-sample-rate-for-a-load-test.md).

Tady jsou některé pokyny pro vzorkovací frekvence:

|Doba trvání zátěžového testu|Doporučená vzorkovací frekvence|
|-|-----------------------------|
|\<1 hodina|5 sekund|
|1-8 hodin|15 sekund|
|8-24 hodin|30 sekund|
|> 24 hodin|60 sekund|

**Informace o tom, jak zahrnout podrobnosti časování ke shromáždění dat percentilu**

V nastavení běhu v Editor zátěžového testu s názvem **Podrobnosti o časování úložiště**existuje vlastnost. Pokud je povolena vlastnost **úložiště podrobností časování** , pak bude čas pro spuštění každého jednotlivého testu, transakce a stránky během zátěžového testu uložen v úložišti výsledků zátěžového testu. To umožňuje zobrazení dat 90 a 95. percentilu v **analyzátoru zátěžového testu** v tabulkách testy, transakce a stránky.

Existují dvě možnosti, jak povolit vlastnost **úložiště podrobností časování** ve vlastnostech parametrů spuštění s názvem **StatisticsOnly** a **AllIndividualDetails**. S kteroukoli z možností všechny jednotlivé testy, stránky a transakce jsou časované a data percentilu se vypočítávají z dat jednotlivých časování. Rozdíl je v tom, že s možností **StatisticsOnly** , jakmile se dokončí data percentilu, se z úložiště odstraní jednotlivá data časování. Tím se sníží množství místa, které je nutné v úložišti, když použijete podrobnosti časování. Pokročilí uživatelé ale můžou chtít zpracovat podrobná data časování jiným způsobem pomocí nástrojů SQL. V takovém případě by měla být použita možnost **AllIndividualDetails** , aby byly k dispozici podrobná data časování pro toto zpracování. Kromě toho, pokud nastavíte vlastnost na **AllIndividualDetails**, pak můžete analyzovat aktivitu virtuálního uživatele pomocí grafu **aktivity virtuálního uživatele** v **analyzátoru zátěžového testu** po dokončení zátěžového testu. Další informace najdete v tématu [Analýza aktivity virtuálních uživatelů v zobrazení podrobností](../test/analyze-load-test-virtual-user-activity-in-the-details-view.md).

Množství místa, které je nutné v úložišti výsledků zátěžového testu pro uložení dat o časování, může být velmi velké, zejména pro delší spuštěné zátěžové testy. Také čas pro ukládání těchto dat do úložiště výsledků zátěžového testu na konci zátěžového testu je delší, protože tato data jsou uložena v agentech zátěžového testu, dokud zátěžový test neskončí. Po dokončení zátěžového testu jsou data uložena do úložiště. Ve výchozím nastavení je povolena vlastnost **úložiště podrobností časování** . Pokud se jedná o problém vašeho testovacího prostředí, můžete chtít nastavit **úložiště podrobností časování** na **žádné**.

Další informace najdete v tématu [Postupy: určení vlastnosti úložiště podrobností časování](../test/how-to-specify-the-timing-details-storage-property-for-a-load-test.md).

## <a name="to-display-a-particular-performance-counter-on-a-load-test-graph"></a>Zobrazení konkrétního čítače výkonu v grafu zátěžového testu

1. Po dokončení zátěžového testu nebo po načtení výsledku testu klikněte na panelu nástrojů analyzátoru zátěžového testu na tlačítko **grafy**.

     Panel **čítače** se zobrazí v zobrazení grafů.

    > [!NOTE]
    > Pokud panel **čítače** není zobrazený, vyberte na panelu nástrojů položku **Zobrazit panel čítačů** .

2. Na panelu **čítače** rozbalte uzly v hierarchii, dokud nenajdete čítač výkonu, který chcete zobrazit graficky.

     Chcete-li například zobrazit dostupnou paměť v počítači, na kterém jsou testy spuštěny, rozbalte položku **počítače**, rozbalte uzel počítače a poté rozbalte položku **paměť**. Zobrazí se čítač počet **dostupných MB** .

3. Vyberte graf, na kterém chcete zobrazit čítač výkonu.

4. Pravým tlačítkem myši klikněte na čítač výkonu na panelu **čítače** a vyberte možnost **Zobrazit čítač v grafu**.

    > [!TIP]
    > Chcete-li dočasně ukončit zobrazování dat čítače výkonu v grafu, zrušte zaškrtnutí políčka čítače výkonu v legendě. Tím umožníte, aby statistiky min, Max a Average byly stále analyzovány, aniž by se zobrazila čára trendu v grafu. To může být užitečné v případě, že graf obsahuje několik překrývajících se čítačů výkonu při analýze problémů. Další informace naleznete v tématu [použití legendy zobrazení grafů k analýze zátěžových testů](../test/use-the-graphs-view-legend-to-analyze-load-tests.md).

5. Chcete-li z grafu odebrat data čítače výkonu, klikněte pravým tlačítkem myši na čítač výkonu ve sloupci **čítač** legendy a vyberte možnost **Odstranit**.

     \-ani

     V grafu klikněte pravým tlačítkem myši na datový řádek a vyberte **Odstranit**.

     \-ani

     Ve sloupci **čítač** v legendě nebo v datovém řádku v grafu zvolte čítač výkonu a pak stiskněte klávesu **Delete** .

    > [!NOTE]
    > Můžete také zvolit, aby se v legendě umístil čítač výkonu, ale ne v grafu pomocí příkazu **Přidat čítač v legendě** .

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md)
- [Postupy: vytváření vlastních grafů](../test/how-to-create-custom-graphs-in-load-test-results.md)
