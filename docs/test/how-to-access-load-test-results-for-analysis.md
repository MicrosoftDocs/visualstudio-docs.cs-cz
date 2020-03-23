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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596460"
---
# <a name="how-to-access-load-test-results-for-analysis"></a>Postup: Přístup k výsledkům zátěžového testu pro analýzu

Při spuštění zátěžového testu z Editoru zátěžového testu se automaticky otevřou výsledky zátěžového testu a průběžný zátěžový test se zobrazí v **analyzátoru zátěžového testu**. Při spuštění zátěžového testu z příkazového řádku je nutné přistupovat k výsledkům zátěžového testu ručně.

Výsledek zátěžového testu pro dokončený zátěžový test obsahuje vzorky čítačů výkonu a informace o chybách, které byly pravidelně shromažďovány z testovaných počítačů. Velký počet vzorků čítače výkonu mohou být shromažďovány v průběhu spuštění zátěžového testu. Množství dat o výkonu, která jsou shromažďována, závisí na délce testu, intervalu vzorkování, počtu testovaných počítačů, počtu shromažďovaných čítačů, nakonfigurovaných sběračích dat a úrovních protokolování. Pro velký zátěžový test může být množství shromažďovaných dat o výkonu snadno několik gigabajtů. Další informace naleznete v [tématu Test řadiče a testovací agenti](configure-test-agents-and-controllers-for-load-tests.md).

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-access-a-load-test-result"></a>Přístup k výsledku zátěžového testu

1. Z webového výkonu a zatížení testovacího projektu otevřete zátěžový test.

2. Na panelu nástrojů Editoru zátěžového testu zvolte tlačítko **Otevřít a Spravovat výsledky.**

     Zobrazí se dialogové okno **Otevřít a spravovat výsledky.**

3. V **části Zadejte název řadiče, chcete-li najít výsledky zátěžového testu**, vyberte řadič. Vyberte místní ** \<> – žádný řadič** pro přístup k místním výsledkům.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Chcete-li zobrazit všechny výsledky pro všechny testy>, vyberte ** \<možnost Zobrazit výsledky pro všechny testy.**

     Pokud jsou k dispozici výsledky zátěžových testů, zobrazí se v seznamu **výsledky zátěžového testu.** Sloupce jsou **Čas**, **Doba trvání**, **Uživatel**, **Výsledek**, **Test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

    > [!NOTE]
    > Výsledky se zobrazí s nejnovějšími výsledky v horní části seznamu.

5. V seznamu **Výsledky zátěžového testu** vyberte výsledky zátěžového testu, které chcete analyzovat, a zvolte **Otevřít**.

6. Zobrazí se **analyzátor zátěžového testu.** Vybraný výsledek zátěžového testu se zobrazí v souhrnném zobrazení. Další informace naleznete v tématu [Přehled souhrnu výsledků zátěžových testů](../test/load-test-results-summary-overview.md).

     Další aspekty výsledků zátěžových testů můžete spravovat v dialogovém okně **Otevřít a spravovat výsledky,** včetně importu, exportu a odebrání výsledků zátěžového testu. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

## <a name="see-also"></a>Viz také

- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
