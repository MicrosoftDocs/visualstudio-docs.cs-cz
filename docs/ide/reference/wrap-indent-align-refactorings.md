---
title: Zalomit, odsadit a zarovnat refaktoringy
description: Naučte se zabalit a zarovnat řetězy volání metod.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093876"
---
# <a name="wrap-indent-and-align-refactorings"></a>Zalomit, odsadit a zarovnat refaktoringy

## <a name="wrap-and-align-call-chains"></a>Zalamování a zarovnávání posloupností volání

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje zabalit a zarovnat řetězy volání metod.

**Kdy:** Máte dlouhý řetězec skládající se z několika volání metody v jednom příkazu.

**Proč:** Čtení dlouhého seznamu je jednodušší, když jsou zabaleny nebo odsazeny podle uživatelských preferencí.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do libovolného řetězce volání.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte **Obtékat řetězec volání** nebo **Obtékat a zarovnat řetězec volání,** chcete-li přijmout refaktoring.

   ![Zalamování a zarovnání řetězů volání](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Zalamování, odsazení a zarovnání parametrů nebo argumentů

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje zalamovat, odsadit a zarovnat parametry nebo argumenty.

**Kdy:** Máte deklaraci metody nebo volání, které má více parametrů nebo argumentů.

**Proč:** Čtení dlouhého seznamu parametrů nebo argumentů je jednodušší, když jsou zabaleny nebo odsazeny podle uživatelských preferencí.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do seznamu parametrů.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   ![Parametry Zalamování, Odsazení a Zarovnání](media/wrap-parameters.png)

3. Vyberte **Zalomit každý parametr,** chcete-li přijmout refaktoring.

## <a name="wrap-binary-expressions"></a>Balení binárních výrazů

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje zalomit binární výrazy.

**Kdy:** Máte binární výraz.

**Proč:** Čtení binárního výrazu je snazší, když je zabalen do uživatelské předvolby.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do binárního výrazu.
2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**
3. Vyberte **Zalamovat výraz,** chcete-li přijmout refaktoring.

   ![Zalamování a zarovnání řetězů volání](media/wrap-binary-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
