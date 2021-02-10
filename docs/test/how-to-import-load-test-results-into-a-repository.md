---
title: 'Postupy: Import výsledků zátěžového testu do úložiště'
description: Naučte se, jak načíst informace do úložiště Load Výsledky testů pomocí dialogového okna otevřít a spravovat Výsledky testů Load.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- results, load test
- load test results, importing
- Load Test Results Repository
- load tests, importing results
ms.assetid: a955b3d2-c8ad-40dd-8ea3-9f1a271e1eed
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: df32fa09b95a9adfbc245ff5c3ec3ab9fbabd1d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961453"
---
# <a name="how-to-import-load-test-results-into-a-repository"></a>Postupy: Import výsledků zátěžového testu do úložiště

Při spuštění zátěžového testu budou informace shromážděné za běhu uloženy v úložišti výsledků zátěžových testů. Úložiště výsledků zátěžových testů obsahuje data čítače výkonu a informace o všech chybách. Další informace najdete v tématu [Správa výsledků zátěžových testů v úložišti load výsledky testů](../test/manage-load-test-results-in-the-load-test-results-repository.md).

Výsledky zátěžového testu můžete spravovat z Editor zátěžového testu pomocí dialogového okna **otevřít a spravovat výsledky testů Load** . Můžete otevřít, importovat, exportovat a odebrat výsledky zátěžového testu.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-import-results-into-a-repository"></a>Import výsledků do úložiště

1. Z projektu webového výkonu a zátěžového testu otevřete zátěžový test.

2. Na vloženém panelu nástrojů vyberte **otevřít a spravovat výsledky**.

     Zobrazí se dialogové okno **otevřít a spravovat výsledky testů zatížení** .

3. V **Zadejte název kontroleru pro hledání výsledků zátěžového testu**, vyberte kontroler. Vyberte **\<local>** pro přístup k výsledkům uloženým místně.

     Pokud jsou k dispozici výsledky testu zatížení, zobrazí se v seznamu **výsledků zátěžového testu** . Sloupce jsou **čas**, **Doba trvání**, **uživatel**, **výsledek**, **test** a **Popis**. **Test** obsahuje název testu a **Popis** obsahuje volitelný popis, který je přidán před spuštěním testu.

4. Klikněte na tlačítko **importovat**.

     Zobrazí se dialogové okno **importovat výsledky testů načtení** .

5. Do pole **název souboru** zadejte název archivovaného souboru výsledků testů a pak zvolte **otevřít**.

     \- ani

     Přejděte k souboru a pak zvolte **otevřít**.

    > [!NOTE]
    > Archivovaný soubor výsledků testů, který zadáte v tomto kroku, se musí vytvořit pomocí operace exportu.

     Výsledky se importují a zobrazí v seznamu **výsledků zátěžového testu** .

## <a name="see-also"></a>Viz také

- [Správa výsledků zátěžového testu v úložišti Výsledky testů zatížení](../test/manage-load-test-results-in-the-load-test-results-repository.md)
- [Analyzovat výsledky zátěžového testu](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [Postupy: Export výsledků zátěžového testu z úložiště](../test/how-to-export-load-test-results-from-a-repository.md)
