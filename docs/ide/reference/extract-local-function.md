---
title: Extrahování lokálních funkcí
description: Zapněte fragment kódu do své vlastní funkce, a to tak, že vyberete kód a zadáte CTRL + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 80ac8f23b5404d70b70166915cd791f2c0d7ed07
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99860968"
---
# <a name="extract-local-function-refactoring"></a>Extrahovat refaktoring lokální funkce

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zapnout fragment kódu z existující metody do místní funkce.

**Když:** Máte fragment stávajícího kódu v některé z metod, které je třeba volat z místní funkce.

**Proč:** Tento kód můžete zkopírovat nebo vložit, ale to by vedlo k duplikaci. Lepším řešením je refaktorující fragment do vlastní místní funkce.

## <a name="how-to"></a>Postupy

1. Zvýrazněte kód, který se má extrahovat.

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** . 

3. Vyberte **Extrahovat lokální funkci**.

    ![Snímek obrazovky okna Visual Studio Code se zvýrazněným řádkem Nabídka rychlé akce a refaktoring je otevřená a je vybraná možnost extrahovat místní funkci.](media/extract-local-function.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
