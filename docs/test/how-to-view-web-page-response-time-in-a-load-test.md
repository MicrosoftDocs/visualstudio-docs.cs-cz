---
title: Doba odezvy stránky v zátěžovém testu
description: Doba potřebná k načtení webové stránky je doba odezvy. Naučte se, jak nastavit cílový čas odezvy pro jednotlivé požadavky webové stránky v testu výkonnosti webu.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, response times
- response times in load tests
- load test results, response times
ms.assetid: e61c49f3-3161-45b1-9220-08b5459065a2
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 540dad5ba6629095c5901b123ebdc4ecb7fb5770
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879524"
---
# <a name="how-to-view-web-page-response-time-in-a-load-test-using-the-load-test-analyzer"></a>Postupy: zobrazení doby odezvy webové stránky v rámci zátěžového testu pomocí analyzátoru zátěžového testu

Čas potřebný k načtení každé webové stránky je známý jako *Doba odezvy*. Při vytváření testu výkonnosti webu můžete nastavit cílový čas odezvy pro každou žádost webové stránky v testu výkonnosti webu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

Pokud spustíte test výkonnosti webu při zatížení zátěžového testu, budete moci analyzovat následující informace pro každou stránku:

- Průměrná doba odezvy stránky.

- Procento iterací testu, které splňují cílovou dobu odezvy stránky.

- Doby odezvy webové stránky můžete analyzovat pomocí zobrazení tabulky nebo zobrazení grafů v **analyzátoru zátěžového testu**:

- Analýza dob odezvy webové stránky v zobrazení tabulek

- Analýza dob odezvy webové stránky v zobrazení grafů

## <a name="view-response-time-data-in-a-table"></a>Zobrazení dat doby odezvy v tabulce

1. V **analyzátoru zátěžového testu** klikněte na tlačítko **tabulky** na panelu nástrojů a ujistěte se, že je zobrazena mřížka tabulky.

2. V rozevíracím seznamu **tabulka** vyberte možnost **stránky**.

3. Data pro jednotlivé stránky se zobrazí v mřížce. Obvykle se zobrazují následující sloupce.

   |Záhlaví sloupce|Description|
   |-|-|
   |**Stránka**|Název webové stránky.|
   |**Scénář**|Název scénáře. Důležité, pokud máte více než jeden scénář v testu výkonnosti webu.|
   |**Test**|Název testu výkonnosti webu. Důležité, pokud máte více než jeden test výkonnosti webu v rámci zátěžového testu.|
   |**Síť**|Typ sítě.<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**Celkem**|Celkový počet požadavků, které byly provedeny pro webovou stránku. Toto je součet všech iterací v rámci zátěžového testu.|
   |**Ave**|Průměrná doba odezvy stránky<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**Dlouhé**|Minimální doba odezvy stránky.<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**Svisl**|Čas odezvy stránky mediánu<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**90%**|90. percentil pro dobu odezvy. To znamená, že 90% stran reagovalo rychleji než toto číslo a 10% stránek reagovalo pomaleji.<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**95 %**|95. percentil pro dobu odezvy. To znamená, že 95% stran reagovalo rychleji než toto číslo a 5% stránek reagovalo pomaleji.|
   |**99%**|99 percentil pro dobu odezvy. To znamená, že 99% stran reagovalo rychleji než toto číslo a 1% stránky reagovaly pomaleji.<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**Počet**|Maximální doba odezvy stránky.<br /><br /> Ve výchozím nastavení se tato data neshromažďují. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**STD dev**|Ve výchozím nastavení nejsou shromažďována standardní data odchylky. Chcete-li shromáždit tato data, v **Editor zátěžového testu** pod uzlem **nastavení spuštění** vyberte uzel nastavení spuštění, který chcete změnit. V okně **vlastnosti** pro vlastnost **úložiště podrobností časování** vyberte možnost **AllIndividualDetails**.|
   |**Čas stránky**|Průměrná doba odezvy všech požadavků, které byly provedeny pro webovou stránku.|
   |**Cíl**|Cílový čas stránky. Toto je konstantní hodnota stránky. **Poznámka:**  Cílový čas stránky se zobrazí pouze v případě, že byl cíl definován pro požadavek v testu výkonnosti webu.|
   |**% Cíle schůzky**|Procento požadavků, které byly provedeny pro webovou stránku, která splnila cílovou dobu odezvy.|

   Další informace naleznete v tématu [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md).

## <a name="view-response-time-data-in-a-graph"></a>Zobrazení dat doby odezvy v grafu

Můžete také zobrazit data doby odezvy v grafu, abyste viděli, jak se v průběhu zátěžového testu mění v čase. To je užitečné hlavně v případě, že se váš vzor zatížení zvětšuje jako testovací běhy (například pokud použijete vzor zatížení kroku). Další informace najdete v tématu [Úpravy vzorů zatížení pro modelování aktivit virtuálních uživatelů](../test/edit-load-patterns-to-model-virtual-user-activities.md).

Zobrazení dat doby odezvy v grafu:

1. V **analyzátoru zátěžového testu** vyberte **grafy** na panelu nástrojů a ujistěte se, že je graf zobrazen.

2. V okně **čítače** rozbalte uzel scénáře, ve kterém máte zájem (například `Scenario1` ).

3. Rozbalte uzel testu výkonnosti webu, který vás zajímá.

4. Rozbalte **stránky** uzlů.

5. Rozbalte uzel stránky, na kterou vás zajímáte.

6. Klikněte pravým tlačítkem na položku **% stránky cíl schůzky** a pak zvolte možnost **Zobrazit čítač v grafu**.

    Data jsou přidána do grafu.

7. Volitelné Opakujte předchozí krok pro **průměrný čas stránky**, **cíl doby odezvy stránky** a **Celkový počet stránek**.

   > [!NOTE]
   > **Cílová doba odezvy stránky** je konstantní.

   Další informace naleznete v tématu [Analýza výsledků zátěžových testů v zobrazení grafů](../test/analyze-load-test-results-in-the-graphs-view.md).

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů a chyb v zobrazení tabulky](../test/analyze-load-test-results-and-errors-in-the-tables-view.md)
- [Postupy: přístup k výsledkům zátěžového testu pro analýzu](../test/how-to-access-load-test-results-for-analysis.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
