---
title: Extrahovat místní funkci
description: Zapněte fragment kódu do své vlastní metody, a to tak, že vyberete kód a zadáte CTRL + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 031fbe22ec61837d489df7a6af923ef0cd2454c7
ms.sourcegitcommit: 260d093d2287ba791f28bdc7103493beabf80b2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77515328"
---
# <a name="extract-local-function-refactoring"></a>Extrahovat refaktoring lokální funkce

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zapnout fragment kódu z existující metody do místní funkce.

**Když:** Máte fragment stávajícího kódu v některé z metod, které je třeba volat z místní funkce.

**Proč:** Tento kód můžete zkopírovat nebo vložit, ale to by vedlo k duplikaci. Lepším řešením je refaktorující fragment do vlastní místní funkce.

## <a name="how-to"></a>Postupy

1. Zvýrazněte kód, který se má extrahovat.

2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** . 

3. Vyberte **Extrahovat lokální funkci**.

    ![Extrahovat místní funkci](media/extract-local-function.png)

## <a name="see-also"></a>Viz také

- [Refaktoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
