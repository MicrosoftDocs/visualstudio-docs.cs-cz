---
title: Ladicí program nemůže zobrazit zdrojový kód ani zpětný překlad.
description: Podívejte se na důvody pro zprávu Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad pro aktuální umístění, kde se provádění zastavilo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: bac2f04ab77e34186a4f0ee202fa8d16f6e45e38
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387343"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad.
Tato chyba zní:

 Ladicí program nemůže zobrazit zdrojový kód nebo zpětný překlad pro aktuální umístění, kde se provádění zastavilo.

 K této chybové zprávě může dojít z několika důvodů:

- Možná jste narazili na zarážku v umístění, pro které není žádný zdrojový kód, při ladění jazyka, který nepodporuje zpětný překlad. Otevřete okno **Breakpoints** (Zarážky), vyhledejte zarážku a odstraňte ji.

- Pokud ladíte skript, možná jste narazili na zarážku, zatímco v programu nebyla žádná vlákna. Zvolte **Krok** nebo **Pokračovat** z **nabídky Ladit** a obnovte ladění.

- Aspekty zabezpečení mohou ladicímu programu bránit ve čtení zásobníku, vlákna, registrace a dalších kontextových informací z programu, který ladíte. K tomu s největší pravděpodobností dojde, pokud ladíte webovou aplikaci a nemáte správné oprávnění pro přístup k virtuálnímu adresáři. Nastavte zabezpečení virtuálního adresáře na Anonymní a zkuste to znovu.

## <a name="see-also"></a>Viz také
- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [První seznámení s ladicím programem](../debugger/debugger-feature-tour.md)
- [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)