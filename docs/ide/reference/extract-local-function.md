---
title: Extrahovat místní funkci
description: Přepněte fragment kódu na vlastní metodu výběrem kódu a zadáním Ctrl+R, Ctrl+M.
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77515328"
---
# <a name="extract-local-function-refactoring"></a>Extrahovat refaktoring místní funkce

Toto refaktoring se vztahuje na:

- C#

**Co:** Umožňuje změnit fragment kódu z existující metody na místní funkci.

**Kdy:** Máte fragment existujícího kódu v některé metodě, která musí být volána z místní funkce.

**Proč:** Můžete tento kód zkopírovat nebo vložit, ale to by vedlo k duplikaci. Lepším řešením je refaktorovat tento fragment do své vlastní místní funkce.

## <a name="how-to"></a>Postupy

1. Zvýrazněte kód, který má být extrahován.

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.** 

3. Vyberte **Extrahovat lokální funkci**.

    ![Extrahovat místní funkci](media/extract-local-function.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
