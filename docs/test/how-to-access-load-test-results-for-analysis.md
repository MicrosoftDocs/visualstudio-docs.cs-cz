---
title: Analyzovat výsledky zátěžového testu
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6be8649ab611a44cb9d2791ae1f4a0e61e930d5b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664884"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Postupy: přístup k výsledkům zátěžového testu pro analýzu

Při spuštění zátěžového testu z Editor zátěžového testu se výsledky zátěžového testu otevřou automaticky a spuštěný test zatížení se zobrazí v **analyzátoru zátěžového testu**. Když spustíte zátěžový test z příkazového řádku, musíte získat přístup k výsledkům zátěžového testu ručně.

Výsledek zátěžového testu pro dokončený zátěžový test obsahuje ukázky čítače výkonu a informace o chybách, které byly pravidelně shromážděny z testovaných počítačů. V průběhu běhu zátěžového testu lze shromáždit velký počet ukázek čítače výkonu. Množství shromážděných dat o výkonu závisí na délce testovacího běhu, intervalu vzorkování, počtu testovaných počítačů, počtu shromažďovaných čítačů, kolekcích dat, které jsou nakonfigurovány, a na úrovních protokolování. Pro velký zátěžový test může být množství shromažďovaných dat o výkonu snadno několik gigabajtů. Další informace naleznete v tématu [řadiče testů a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Přístup k výsledku zátěžového testu

1. Z projektu webového výkonu a zátěžového testu otevřete zátěžový test.

2. Na panelu nástrojů Editor zátěžového testu klikněte na tlačítko **otevřít a spravovat výsledky** .

     Zobrazí se dialogové okno **otevřít a spravovat výsledky** .

3. V **Zadejte název kontroleru pro hledání výsledků zátěžového testu**, vyberte kontroler. Vyberte **\<local >-žádný kontroler** pro přístup k výsledkům uloženým místně.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Vyberte **\<Show výsledky pro všechny testy >** pro zobrazení všech výsledků pro všechny testy.

     Pokud jsou k dispozici výsledky testu zatížení, zobrazí se v seznamu **výsledků zátěžového testu** . Sloupce jsou **čas**, **Doba trvání**, **uživatel**, **výsledek**, **test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

    > [!NOTE]
    > Výsledky se zobrazí s nejnovějšími výsledky v horní části seznamu.

5. V seznamu **výsledky zátěžového testu** vyberte výsledky zátěžového testu, které chcete analyzovat, a zvolte **otevřít**.

6. Zobrazí se **analyzátor zátěžového testu** . Vybraný výsledek zátěžového testu se zobrazí v souhrnném zobrazení. Další informace najdete v tématu [Přehled souhrnu výsledků zátěžového testu](../test/load-test-results-summary-overview.md).

     Můžete spravovat další aspekty výsledků zátěžových testů v dialogovém okně **otevřít a spravovat výsledky** , včetně importu, exportu a odebírání výsledků zátěžového testu. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti výsledků zátěžového testu](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Viz také:

- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)