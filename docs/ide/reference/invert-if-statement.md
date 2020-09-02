---
title: Invertování příkazů if
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: a0419100cbc5fcd543eb250fa85cbfe2ebd1c97f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65531592"
---
# <a name="invert-if-statement"></a>Invertování příkazů if

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Umožňuje invertovat `if` `if else` příkaz nebo bez změny významu kódu.

**Když:** Máte-li `if` příkaz nebo `if else` , který by měl být lépe srozumitelný při obráceném.

**Proč:** Vrácení `if` `if else` příkazu or rukou může trvat mnohem delší dobu a může způsobit chyby. Tato oprava kódu vám pomůže tento Refaktorovat automaticky.

## <a name="invert-if-statement-refactoring"></a>Invertovat refaktoring příkazu if

1. Umístěte kurzor do `if` `if else` příkazu nebo.

    ![Invertovat, pokud else](media/invert-if.png)

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

    ![Invertovat, pokud jinak Oprava kódu](media/invert-if-codefix.png)

3. Vyberte **Invertovat if**.

    ![Invertovat, pokud výsledek else](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
