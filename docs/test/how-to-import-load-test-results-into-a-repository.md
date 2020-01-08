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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589029"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Postupy: Import výsledků zátěžového testu do úložiště

Při spuštění zátěžového testu budou informace shromážděné za běhu uloženy v úložišti výsledků zátěžových testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace najdete v tématu [výsledků zátěžového testu spravovat v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžového testu můžete spravovat z editoru zátěžového testu pomocí **otevřít a spravovat výsledky zátěžového testu** dialogové okno. Můžete otevřít, importovat, exportovat a odstranit výsledky zátěžových testů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Chcete-li importovat do úložiště výsledků

1. Z webového výkonu a zátěžové testování projektu, otevřete zátěžový test.

2. Na panelu nástrojů themeroller vložený **otevřít a spravovat výsledky**.

     **Otevřít a spravovat výsledky zátěžového testu** se zobrazí dialogové okno.

3. V **zadat název kontroléru pro vyhledání výsledků zátěžového testu**, vyberte řadič. Vyberte  **\<místní >** pro přístup k výsledkům uloženým místně.

     Pokud jsou k dispozici výsledky zátěžového testu, jsou uvedeny v **výsledky zátěžového testu** seznamu. Sloupce jsou **čas**, **doba trvání**, **uživatele**, **výsledek**, **testovací**, a  **Popis**. **Testování** obsahuje název testu, a **popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

4. Zvolte **Import**.

     **Import výsledků zátěžového testu** zobrazí se dialogové okno.

5. V **název_souboru** zadejte název souboru výsledků archivované testu a klikněte na tlačítko **otevřít**.

     \- nebo –

     Přejděte k souboru a klikněte na tlačítko **otevřít**.

    > [!NOTE]
    > Soubor výsledků archivované test, který zadáte v tomto kroku musí být vytvořen pomocí provádí se operace exportu.

     Výsledky jsou importovány a zobrazují v **výsledky zátěžového testu** seznamu.

## <a name="see-also"></a>Viz také:

- [Správa výsledků zátěžových testů v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Export zátěžový test výsledků z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
