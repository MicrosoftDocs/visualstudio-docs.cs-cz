---
title: 'Postupy: Odstranění výsledků zátěžového testu z úložiště'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, deleting results
- load test results, removing
- Load Test Results Repository
- load tests, removing results
- load test results, deleting
ms.assetid: c2afe36b-d061-4f0e-9580-c18569ec08f9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: dd196076fb769f80c36ab8630eebf1e8a0f8b234
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287776"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Postupy: odstranění výsledků zátěžového testu z úložiště

Při spuštění zátěžového testu se informace shromážděné během spuštění ukládají do úložiště Load Výsledky testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti load výsledky testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžového testu můžete spravovat z Editor zátěžového testu pomocí dialogového okna **otevřít a spravovat výsledky testů Load** . Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Odstranění výsledků z úložiště

1. Z projektu webového výkonu a zátěžového testu otevřete zátěžový test.

2. Na vloženém panelu nástrojů vyberte **otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **otevřít a spravovat výsledky testů zatížení** .

3. V **Zadejte název kontroleru pro hledání výsledků zátěžového testu**, vyberte kontroler. Tuto možnost vyberte, pokud **\<Local - No controller>** chcete získat přístup k výsledkům uloženým místně.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Tuto možnost vyberte **\<Show results for all tests>** , pokud chcete zobrazit všechny výsledky pro všechny testy.

     Pokud jsou výsledky zátěžového testu k dispozici, zobrazí se v seznamu **výsledků zátěžového testu** . Sloupce jsou **čas**, **Doba trvání**, **uživatel**, **výsledek**, **test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu. Sloupec **Description (popis** ) zobrazuje krátké popisy, které byly zadány v **komentářích analýzy** pro tento výsledek testu.

5. V seznamu **výsledky zátěžového testu** vyberte výsledek. K výběru více než jednoho výsledku můžete použít klávesu **SHIFT** , klávesu **CTRL** nebo obojí.

6. Zvolte **Odebrat**.

     Výsledky se odeberou z úložiště.

    > [!NOTE]
    > Dialogové okno **otevřít a spravovat výsledky testů Load** zůstane otevřené po odebrání výsledků.

## <a name="see-also"></a>Viz také

- [Postupy: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
- [Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)
