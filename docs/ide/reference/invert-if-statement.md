---
title: Invertování příkazů if
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring Invertovat příkaz if nebo if else beze změny významu kódu.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 71b3a11e053b6a600d0b33db7c52a91c4950bf5b
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96616977"
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
