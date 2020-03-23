---
title: 'Postupy: Import výsledků zátěžového testu do úložiště'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: bbc8c352c7bf3cda0524f07aa82b6ccbe70602b2
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589029"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Postup: Import výsledků zátěžového testu do úložiště

Při spuštění zátěžového testu budou informace shromážděné za běhu uloženy v úložišti výsledků zátěžových testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace naleznete [v tématu Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžových testů můžete spravovat z Editoru zátěžových testů pomocí dialogového okna **Otevřít a spravovat výsledky zátěžového testu.** Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Import výsledků do úložiště

1. Z webového výkonu a zatížení testovacího projektu otevřete zátěžový test.

2. Na vloženém panelu nástrojů zvolte **Otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **Otevřít a spravovat výsledky zátěžového testu.**

3. V **části Zadejte název řadiče, chcete-li najít výsledky zátěžového testu**, vyberte řadič. Vyberte místní ** \<>** pro přístup k výsledkům uloženým místně.

     Pokud jsou k dispozici výsledky zátěžových testů, zobrazí se v seznamu **výsledky zátěžového testu.** Sloupce jsou **Čas**, **Doba trvání**, **Uživatel**, **Výsledek**, **Test**a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

4. Zvolte **Importovat**.

     Zobrazí se dialogové okno **Importovat výsledky zátěžového testu.**

5. Do pole **Název souboru** zadejte název archivovaného souboru výsledků testu a pak zvolte **Otevřít**.

     \-nebo -

     Přejděte k souboru a pak zvolte **Otevřít**.

    > [!NOTE]
    > Archivovaný soubor výsledků testu, který zadáte v tomto kroku, musí být vytvořen provedením operace Export.

     Výsledky jsou importovány a zobrazí se v seznamu **výsledky zátěžového testu.**

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžových testů v úložišti výsledků zátěžových testů](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postup: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
