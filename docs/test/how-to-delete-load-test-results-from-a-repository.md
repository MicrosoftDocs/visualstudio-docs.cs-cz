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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75589055"
---
# <a name="how-to-delete-load-test-results-from-a-repository"></a>Postupy: výsledků zátěžového testu odstranit z úložiště

Při spuštění zátěžového testu, informace, které byly shromážděny během spuštění uložená v úložiště výsledků testu zátěže. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace najdete v tématu [výsledků zátěžového testu spravovat v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžového testu můžete spravovat z editoru zátěžového testu pomocí **otevřít a spravovat výsledky zátěžového testu** dialogové okno. Můžete otevřít, importovat, exportovat a odstranit výsledky zátěžových testů.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-delete-results-from-a-repository"></a>Chcete-li odstranit z úložiště výsledků

1. Z webového výkonu a zátěžové testování projektu, otevřete zátěžový test.

2. Na panelu nástrojů themeroller vložený **otevřít a spravovat výsledky**.

     **Otevřít a spravovat výsledky zátěžového testu** se zobrazí dialogové okno.

3. V **zadat název kontroléru pro vyhledání výsledků zátěžového testu**, vyberte řadič. Vyberte  **\<místní – žádný kontrolér >** pro přístup k výsledkům, které se ukládají místně.

4. V **zobrazit výsledky pro následující zátěžový test**, vyberte test zatížení, jejichž výsledky chcete zobrazit. Vyberte  **\<zobrazit výsledky všech testů >** zobrazíte všechny výsledky pro všechny testy.

     Pokud výsledky zátěžového testu jsou k dispozici, jsou uvedeny v **výsledky zátěžového testu** seznamu. Sloupce jsou **čas**, **doba trvání**, **uživatele**, **výsledek**, **testovací**, a  **Popis**. **Testování** obsahuje název testu, a **popis** obsahuje volitelný popis, který je přidán před spuštěním testu. **Popis** sloupec zobrazuje krátké popisy, které byly zadány v **komentáře analýzy** pro tento výsledek testu.

5. V **výsledky zátěžového testu** seznamu, vyberte výsledek. Můžete použít **Shift** klíč, **Ctrl** klíč, nebo obojí a vyberte více než jeden výsledek.

6. Zvolte **odebrat**.

     Výsledky se odeberou z úložiště.

    > [!NOTE]
    > **Otevřít a spravovat výsledky zátěžového testu** dialogové okno zůstane otevřený po odebrání výsledky.

## <a name="see-also"></a>Viz také:

- [Postupy: Export zátěžový test výsledků z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
- [Správa výsledků zátěžových testů v úložiště výsledků testu zátěže](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analýza výsledků zátěžových testů](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Import výsledků zátěžového testu do úložiště](../test/how-to-import-load-test-results-into-a-repository.md)
