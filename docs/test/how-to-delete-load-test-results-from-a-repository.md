---
title: 'Postupy: Odstranění výsledků zátěžového testu z úložiště'
ms.date: 10/19/2016
ms.topic: conceptual
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
ms.openlocfilehash: 26dc9750a2bf2eaf5d0ee5dd3d08485c458bb74a
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589055"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Postup: Odstranění výsledků zátěžového testu z úložiště

Při spuštění zátěžového testu jsou informace shromážděné během spuštění uloženy v úložišti výsledků zátěžového testu. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžových testů můžete spravovat z Editoru zátěžových testů pomocí dialogového okna **Otevřít a spravovat výsledky zátěžového testu.** Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Odstranění výsledků z úložiště

1. Z webového výkonu a zatížení testovacího projektu otevřete zátěžový test.

2. Na vloženém panelu nástrojů zvolte **Otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **Otevřít a spravovat výsledky zátěžového testu.**

3. V **části Zadejte název řadiče, chcete-li najít výsledky zátěžového testu**, vyberte řadič. Vyberte místní ** \<– žádný řadič>** pro přístup k výsledkům, které jsou uloženy místně.

4. V **části Zobrazit výsledky pro následující zátěžový test**vyberte zátěžový test, jehož výsledky chcete zobrazit. Chcete-li zobrazit všechny výsledky pro všechny testy>, vyberte ** \<možnost Zobrazit výsledky pro všechny testy.**

     Pokud jsou k dispozici výsledky zátěžového testu, zobrazí se v seznamu **výsledky zátěžového testu.** Sloupce jsou **Čas**, **Doba trvání**, **Uživatel**, **Výsledek**, **Test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu. Ve sloupci **Popis** se zobrazí krátké popisy, které byly zadány v **komentářích analýzy** pro tento výsledek testu.

5. V seznamu **Výsledky zátěžového testu** zvolte výsledek. Pomocí **klávesshifta,** klávesy **Ctrl** nebo obojího můžete vybrat více než jeden výsledek.

6. Zvolte **Odebrat**.

     Výsledky jsou odebrány z úložiště.

    > [!NOTE]
    > Po odebrání výsledků zůstane otevřené dialogové okno **Otevřít a spravovat výsledky zátěžového testu.**

## <a name="see-also"></a>Viz také

- [Postup: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
- [Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)
