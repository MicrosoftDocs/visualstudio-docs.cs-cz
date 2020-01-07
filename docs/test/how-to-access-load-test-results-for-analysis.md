---
title: Analýza výsledků zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, accessing
- Load Test Viewer
- load tests, accessing
- load tests, analyzing
- load tests, results
- Load Test Viewer, viewing
ms.assetid: b0a3e694-2894-479b-b270-7e61e9fafacd
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b6a5da728e24d5d7fdbeccd1e28aa2742e04bf48
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596460"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Postupy: přístup k analýze výsledků zátěžového testu

Když spustíte zátěžový test z editoru zátěžových testů, výsledky zátěžového testu se automaticky otevře a spuštění zátěžového testu se zobrazí v **Analyzéru zátěžového testu**. Při spuštění zátěžového testu z příkazového řádku, je nutné ručně přejít výsledky zátěžového testu.

Výsledek testu zatížení pro dokončený test zatížení obsahuje ukázky čítače výkonu a informace o chybách, které byly pravidelně shromažďovány z testovaných počítačů. V průběhu spuštění zátěžového testu lze shromažďovat velké množství vzorků čítačů výkonu. Množství shromážděných dat o výkonu závisí na délce zkoušky, intervalu vzorkování, počtu testovaných počítačů, počtu shromažďovaných čítačů, sběračích dat, které jsou nakonfigurovány a úrovní protokolování. Pro velký zátěžový test může množství shromážděných dat o výkonu snadno dosáhnout několika gigabajtů. Další informace najdete v tématu [testovací kontrolery a testovací agenty](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Pro přístup k výsledku zátěžového testu

1. Z webového výkonu a zátěžové testování projektu, otevřete zátěžový test.

2. V panelu nástrojů editoru zátěžového testu, zvolte **otevřít a spravovat výsledky** tlačítko.

     **Otevřít a spravovat výsledky** zobrazí se dialogové okno.

3. V **zadat název kontroléru pro vyhledání výsledků zátěžového testu**, vyberte řadič. Vyberte  **\<místní > – žádný kontrolér** pro přístup k výsledkům uloženým místně.

4. V **zobrazit výsledky pro následující zátěžový test**, vyberte test zatížení, jejichž výsledky chcete zobrazit. Vyberte  **\<zobrazit výsledky všech testů >** zobrazíte všechny výsledky pro všechny testy.

     Pokud jsou k dispozici výsledky zátěžového testu, jsou uvedeny v **výsledky zátěžového testu** seznamu. Sloupce jsou **čas**, **doba trvání**, **uživatele**, **výsledek**, **testovací**, a  **Popis**. **Testování** obsahuje název testu, a **popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

    > [!NOTE]
    > Výsledky se zobrazí s nejnovější výsledky v horní části seznamu.

5. V **výsledky zátěžového testu** vyberte výsledky zátěžového testu, kterou chcete analyzovat a zvolte **otevřít**.

6. **Analyzéru zátěžového testu** se zobrazí. Výsledek vybraný zátěžového testu se zobrazí v souhrnném zobrazení. Další informace najdete v tématu [přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md).

     Můžete spravovat výsledky zátěžového testu v pracovat s dalšími aspekty **otevřít a spravovat výsledky** dialogové okno včetně importu, exportu a odebrání výsledky zátěžového testu. Další informace najdete v tématu [spravovat výsledky zátěžového testu v zátěžového testu úložiště výsledků](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Viz také:

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
