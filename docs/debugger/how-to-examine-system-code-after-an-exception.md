---
title: Kontrola systémového kódu po výjimce | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98f3eb98024e20350151904f297f7e7b4d6f1fea
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72733377"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Postupy: Kontrola systémového kódu po výjimce
Pokud dojde k výjimce, může být nutné prošetřit kód uvnitř volání systému, aby bylo možné určit příčinu výjimky. Následující postup vysvětluje, jak to provést, pokud nejsou načteny symboly pro systémový kód nebo pokud je Pouze můj kód povolen.

### <a name="to-examine-system-code-following-an-exception"></a>Kontrola systémového kódu po výjimce

1. V okně **zásobník volání** klikněte pravým tlačítkem myši a pak klikněte na **Zobrazit externí kód**.

     Pokud není povolena Pouze můj kód, tato možnost není k dispozici v místní nabídce a ve výchozím nastavení je zobrazen systémový kód.

2. Klikněte pravým tlačítkem myši na snímky externích kódů, které se nyní zobrazí v okně **zásobník volání** .

3. Ukažte na **načíst symboly z** a potom klikněte na **Microsoft Symbol Servers**.

    1. Pokud byla povolena Pouze můj kód, zobrazí se dialogové okno. Uvádí, že Pouze můj kód je teď zakázaný. To je nezbytné pro krokování do systémových volání.

    2. Zobrazí se dialogové okno **Stáhnout veřejné symboly** . Zmizí, až se stahování dokončí.

4. Nyní můžete zkontrolovat systémový kód v okně **zásobník volání** a dalších oknech. Například Poklikáním na rámec zásobníku volání můžete zobrazit kód v okně zdroje nebo **zpětný překlad** .

## <a name="see-also"></a>Viz také:
- [Správa výjimek pomocí ladicího programu](../debugger/managing-exceptions-with-the-debugger.md)