---
title: Zabalení, odsazení a zarovnání refaktoringu
description: Naučte se zalamovat a zarovnávat řetězce volání metod.
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "79093876"
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

   ![Zalamovat a zarovnávat řetězy volání](media/wrap-binary-expression.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
