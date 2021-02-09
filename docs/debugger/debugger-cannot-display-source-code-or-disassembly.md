---
title: Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad.
description: Podívejte se na důvody pro zprávu ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad pro aktuální umístění, kde bylo zastaveno provádění.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2966405378d2a6144c921c442e7412a41c454c52
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99873064"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad.
Tato chyba čte:

 Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad pro aktuální umístění, kde bylo spuštění zastaveno.

 Tato chybová zpráva se může vyskytnout z několika důvodů:

- Možná jste narazili na zarážku v umístění, pro které neexistuje zdrojový kód, při ladění jazyka, který nepodporuje zpětný překlad. Otevřete okno **zarážky** , najděte zarážku a odstraňte ji.

- Pokud ladíte skript, možná jste narazili na zarážku, zatímco v programu neexistovala žádná vlákna. V nabídce **ladění** vyberte **Krok** nebo **pokračovat** a pokračujte v ladění.

- Kvůli bezpečnostním hlediskům může ladicí program zabránit načtení zásobníku, vlákna, registraci a dalších informací o kontextu z programu, který ladíte. K tomu pravděpodobně dojde, pokud ladíte webovou aplikaci a nemáte správné oprávnění pro přístup k virtuálnímu adresáři. Nastavte zabezpečení virtuálního adresáře na anonymní a zkuste to znovu.

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)