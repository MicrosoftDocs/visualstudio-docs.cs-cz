---
title: Exportovat Výsledky testů zatížení
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f9b20915d5c320ff8db4da849d20267355c26590
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85287750"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Postupy: Export výsledků zátěžového testu z úložiště

Při spuštění zátěžového testu budou informace shromážděné za běhu uloženy v úložišti výsledků zátěžových testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti load výsledky testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžového testu můžete spravovat z Editor zátěžového testu pomocí dialogového okna **otevřít a spravovat výsledky testů Load** . Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Export výsledků z úložiště

1. Z projektu webového výkonu a zátěžového testu otevřete zátěžový test.

2. Na vloženém panelu nástrojů vyberte **otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **otevřít a spravovat výsledky testů zatížení** .

3. V **Zadejte název kontroleru pro hledání výsledků zátěžového testu**, vyberte kontroler. Vyberte **\<Local - No controller>** pro přístup k výsledkům uloženým místně.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Tuto možnost vyberte **\<Show results for all tests>** , pokud chcete zobrazit všechny výsledky pro všechny testy.

     Pokud jsou výsledky zátěžového testu k dispozici, zobrazí se v seznamu **výsledků zátěžového testu** . Sloupce jsou **čas**, **Doba trvání**, **uživatel**, **výsledek**, **test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu. Sloupec **Description (popis** ) zobrazuje krátké popisy, které byly zadány v **komentářích analýzy** pro tento výsledek testu.

5. V seznamu **výsledky zátěžového testu** vyberte výsledek. K výběru více výsledků můžete použít klávesu **SHIFT** , klávesu **CTRL** nebo obojí, a exportovat je do jednoho souboru.

6. Vyberte **exportovat**.

     Zobrazí se dialogové okno **exportovat výsledky testů načtení** .

7. Do pole **název souboru** zadejte název a pak zvolte **Uložit**.

     Výsledky budou exportovány do souboru archivu.

    > [!NOTE]
    > Dialogové okno **otevřít a spravovat výsledky testů Load** zůstane otevřené po zobrazení výsledků.

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Postupy: odstranění výsledků zátěžového testu z úložiště](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)
