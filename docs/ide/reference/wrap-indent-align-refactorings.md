---
title: Zabalení, odsazení a zarovnání refaktoringu
description: Naučte se zalamovat a zarovnávat řetězce volání metod.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 7c218d914bc234533af674fc5d138a1c102d85c3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99836265"
---
# <a name="wrap-indent-and-align-refactorings"></a>Zabalení, odsazení a zarovnání refaktoringu

## <a name="wrap-and-align-call-chains"></a>Zalamování a zarovnávání posloupností volání

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje zalamovat a zarovnávat řetězce volání metod.

**Když:** Máte dlouhý řetěz skládající se z několika volání metod v jednom příkazu.

**Proč:** Čtení dlouhého seznamu je snazší, když se zabalí nebo odsadí podle preferencí uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do libovolného řetězce volání.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Chcete-li přijmout refaktoring, vyberte možnost zabalení **řetězu volání** nebo **zabalení a zarovnání řetězce volání** .

   ![Screeenshot z nabídky rychlé akce a Refaktoring v aplikaci Visual Studio se zvoleným řetězcem volání Warap a zobrazenými změnami kódu jazyka C#.](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>Sbalení, odsazení a zarovnání parametrů nebo argumentů

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje zalamovat, odsazovat a zarovnávat parametry nebo argumenty.

**Když:** Máte deklaraci metody nebo volání s více parametry nebo argumenty.

**Proč:** Čtení dlouhého seznamu parametrů nebo argumentů je snazší, když jsou zabalené nebo odsazené podle preferencí uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do seznamu parametrů.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Zabalení, odsazení a zarovnání parametrů](media/wrap-parameters.png)

3. Pokud chcete refaktoring přijmout, vyberte **zalamovat každý parametr** .

## <a name="wrap-binary-expressions"></a>Balení binárních výrazů

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Umožňuje zalamovat binární výrazy.

**Když:** Máte binární výraz.

**Proč:** Čtení binárního výrazu je snazší, pokud je zabaleno do předvolby uživatele.

### <a name="how-to"></a>Postupy

1. Umístěte kurzor do binárního výrazu.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Kliknutím na **zalamovat výraz** přijměte refaktoring.

   ![Screeenshot z nabídky rychlé akce a Refaktoring v aplikaci Visual Studio se zvoleným výrazem Warap a zobrazenými změnami kódu jazyka C#.](media/wrap-binary-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
