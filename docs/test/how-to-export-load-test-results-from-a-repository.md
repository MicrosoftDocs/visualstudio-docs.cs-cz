---
title: Export výsledků zátěžových testů
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load tests, exporting results
- Load Test Results Repository
- load test results, exporting
ms.assetid: 716c2af5-8737-4d31-956f-a0273f7c5c0c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f72dbd687bc9177cd4cfd36416acb23445d30c8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589042"
---
# <a name="how-to-export-load-test-results-from-a-repository"></a>Postup: Export výsledků zátěžového testu z úložiště

Při spuštění zátěžového testu budou informace shromážděné za běhu uloženy v úložišti výsledků zátěžových testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžových testů můžete spravovat z Editoru zátěžových testů pomocí dialogového okna **Otevřít a spravovat výsledky zátěžového testu.** Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-export-results-from-a-repository"></a>Export výsledků z úložiště

1. Z webového výkonu a zatížení testovacího projektu otevřete zátěžový test.

2. Na vloženém panelu nástrojů zvolte **Otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **Otevřít a spravovat výsledky zátěžového testu.**

3. V **části Zadejte název řadiče, chcete-li najít výsledky zátěžového testu**, vyberte řadič. Vyberte místní ** \<– žádný řadič>** pro přístup k výsledkům uloženým místně.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Chcete-li zobrazit všechny výsledky pro všechny testy>, vyberte ** \<možnost Zobrazit výsledky pro všechny testy.**

     Pokud jsou k dispozici výsledky zátěžového testu, zobrazí se v seznamu **výsledky zátěžového testu.** Sloupce jsou **Čas**, **Doba trvání**, **Uživatel**, **Výsledek**, **Test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu. Ve sloupci **Popis** se zobrazí krátké popisy, které byly zadány v **komentářích analýzy** pro tento výsledek testu.

5. V seznamu **Výsledky zátěžového testu** zvolte výsledek. Pomocí **klávesshiftu,** klávesy **Ctrl** nebo obojího můžete vybrat více než jeden výsledek a exportovat je do jednoho souboru.

6. Zvolte **Exportovat**.

     Zobrazí se dialogové okno **Exportovat výsledky zátěžového testu.**

7. Do pole **Název souboru** zadejte název a pak zvolte **Uložit**.

     Výsledky budou exportovány do souboru archivu.

    > [!NOTE]
    > Po zobrazení výsledků výsledků zůstane otevřené dialogové okno **Otevřít a spravovat výsledky zátěžového testu.**

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Postup: Odstranění výsledků zátěžového testu z úložiště](../test/how-to-delete-load-test-results-from-a-repository.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)
