---
title: Doba odezvy stránky v zátěžovém testu
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: cf8bc1205658899a51cf1a50e83a9a8b34034b25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594315"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Postup: Zobrazení doby odezvy webové stránky v zátěžovém testu pomocí analyzátoru zátěžového testu

Doba, kterou každá webová stránka načte, se označuje jako *doba odezvy*. Při vytváření testu výkonu webu můžete nastavit cíl doby odezvy pro každou žádost o webovou stránku v testu výkonu webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud spustíte test výkonu webu pod stresem v zátěžovém testu, budete moci analyzovat následující informace pro každou stránku:

- Průměrná doba odezvy pro stránku.

- Procento iterací testu, které splňují cíl doby odezvy pro stránku.

- Časy odpovědí webové stránky můžete analyzovat pomocí zobrazení Tabulky nebo Grafy v **analyzátoru zátěžového testu**:

- Analýza doby odezvy webové stránky v zobrazení tabulek

- Analýza doby odezvy webové stránky v zobrazení grafů

## <a name="view-response-time-data-in-a-table"></a>Zobrazení dat doby odezvy v tabulce

1. V **analyzátoru zátěžového testu**zvolte **tabulky** na panelu nástrojů, abyste se ujistili, že je zobrazena mřížka tabulky.

2. V rozevíracím seznamu **Tabulka** vyberte **Stránky**.

3. Data pro každou stránku se zobrazí v mřížce. Obvykle se zobrazují následující sloupce.

   |Záhlaví sloupce|Popis|
   |-|-|
   |**Stránka**|Název webové stránky.|
   |**Scénář**|Název scénáře. Důležité, pokud máte více než jeden scénář v testu výkonu webu.|
   |**Test**|Název testu výkonu webu. Důležité, pokud máte více než jeden test výkonu webu v zátěžovém testu.|
   |**Síť**|Typ sítě.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Celkem**|Celkový počet požadavků, které byly provedeny pro webovou stránku. Toto je součet pro všechny iterace v zátěžovém testu.|
   |**Ave**|Průměrná doba odezvy stránky.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Min**|Minimální doba odezvy stránky.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Medián**|Medián doby odezvy stránky.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**90%**|90. percentil pro dobu odezvy. To znamená, že 90 % stránek reagovalo rychleji než toto číslo a 10 % stránek reagovalo pomaleji.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**95%**|95. percentil pro dobu odezvy. To znamená, že 95 % stránek reagovalo rychleji než toto číslo a 5 % stránek reagovalo pomaleji.|
   |**99%**|99. percentil pro dobu odezvy. To znamená, že 99 % stránek reagovalo rychleji než toto číslo a 1 % stránek reagovalo pomaleji.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Max**|Maximální doba odezvy stránky.<br /><br /> Ve výchozím nastavení nejsou tato data shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Std Dev**|Ve výchozím nastavení nejsou data směrodatné odchylky shromažďována. Chcete-li tato data shromažďovat, vyberte v **editoru zátěžového testu**v uzlu **Spustit nastavení** uzel, který chcete změnit. V okně **Vlastnosti** pro vlastnost **Úložiště podrobností časování** vyberte **položku AllIndividualDetails**.|
   |**Čas stránky**|Průměrná doba odezvy pro všechny požadavky, které byly provedeny pro webovou stránku.|
   |**Cíl**|Cíl času stránky. Toto je konstantní hodnota pro stránku. **Poznámka:**  Cíl času stránky se zobrazí pouze v případě, že byl cíl definován pro požadavek v testu výkonu webu.|
   |**% cíle plnění**|Procento požadavků, které byly provedeny pro webovou stránku, která splnila cíl doby odezvy.|

   Další informace naleznete [v tématu Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Zobrazení dat doby odezvy v grafu

Můžete také zobrazit data doby odezvy v grafu a zjistit, jak se během zátěžového testu v průběhu času mění. To je užitečné zejména v případě, že se vzor zatížení zvyšuje při spuštění testu (například pokud použijete vzor zatížení kroku). Další informace naleznete v [tématu Úprava vzorů zatížení k modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Zobrazení dat doby odezvy v grafu:

1. V **analyzátoru zátěžového testu**zvolte **Grafy** na panelu nástrojů a ujistěte se, že je graf zobrazen.

2. V okně **Čítače** rozbalte uzel scénáře, ve kterém máte `Scenario1`zájem (například).

3. Rozbalte uzel testu výkonu webu, o který máte zájem.

4. Rozbalte **stránky**uzlu .

5. Rozbalte uzel stránky, o kterou máte zájem.

6. Klikněte pravým tlačítkem myši na **% cílů schůzky stránek** a pak v grafu zvolte Zobrazit **počítadlo**.

    Data jsou přidána do grafu.

7. (Nepovinné) Opakujte předchozí krok pro **prům. čas stránky**, **cíl doby odezvy stránky**a celkový počet **stránek**.

   > [!NOTE]
   > **Cíl doby odezvy stránky** je konstantní.

   Další informace naleznete [v tématu Analýza výsledků zátěžových testů v zobrazení Grafy](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů a chyb v zobrazení Tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Postup: Přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
