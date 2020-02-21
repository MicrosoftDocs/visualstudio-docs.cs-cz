---
title: Sbalení, odsazení a zarovnání refaktoringu
description: Naučte se zalamovat a zarovnávat řetězce volání metod.
ms.date: 02/19/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 349f2eeccfea4fea03967929b01114c0de1af155
ms.sourcegitcommit: 3c105990656cd509062ce60e52e776c794f6305d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77527666"
---
# <a name="wrap-indent-and-align-refactorings"></a>Sbalení, odsazení a zarovnání refaktoringu

## <a name="wrap-and-align-call-chains"></a>Zalamování a zarovnávání posloupností volání

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zalamovat a zarovnávat řetězce volání metod.

**Když:** Máte dlouhý řetěz skládající se z několika volání metod v jednom příkazu.

**Proč:** Čtení dlouhého seznamu je snazší, když se zabalí nebo odsadí podle preferencí uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do libovolného řetězce volání.
2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Chcete-li přijmout refaktoring, vyberte možnost zabalení **řetězu volání** nebo **zabalení a zarovnání řetězce volání** .

   ![Zalamovat a zarovnávat řetězy volání](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Sbalení, odsazení a zarovnání parametrů nebo argumentů

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje zalamovat, odsazovat a zarovnávat parametry nebo argumenty.

**Když:** Máte deklaraci metody nebo volání s více parametry nebo argumenty.

**Proč:** Čtení dlouhého seznamu parametrů nebo argumentů je snazší, když jsou zabalené nebo odsazené podle preferencí uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do seznamu parametrů.
2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Zabalení, odsazení a zarovnání parametrů](media/wrap-parameters.png)

3. Pokud chcete refaktoring přijmout, vyberte **zalamovat každý parametr** .

## <a name="wrap-binary-expressions"></a>Balení binárních výrazů

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje zalamovat binární výrazy.

**Když:** Máte binární výraz.

**Proč:** Čtení binárního výrazu je snazší, pokud je zabaleno do předvolby uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do binárního výrazu.
2. Stiskněte klávesu **Ctrl**+ **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Kliknutím na **zalamovat výraz** přijměte refaktoring.

   ![Zalamovat a zarovnávat řetězy volání](media/wrap-binary-expression.png)

## <a name="see-also"></a>Viz také

- [Refaktoring](../refactoring-in-visual-studio.md)
