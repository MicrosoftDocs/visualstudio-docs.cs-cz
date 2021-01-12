---
title: Extrahování lokálních funkcí
description: Zapněte fragment kódu do své vlastní funkce, a to tak, že vyberete kód a zadáte CTRL + R, CTRL + M.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: e007246b85671a0f4606bbdb3d1e9c4e0dc83541
ms.sourcegitcommit: cd7f122c6850cf442a4ca42d51d05c7a8fe9038d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/12/2021
ms.locfileid: "98129455"
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
