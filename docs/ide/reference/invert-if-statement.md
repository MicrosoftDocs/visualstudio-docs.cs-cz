---
title: Invertování příkazů if
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring Invertovat příkaz if nebo if else beze změny významu kódu.
ms.custom: SEO-VS-2020
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: cf4ad7c25030e4a331ee67f4957ddac59afdd966
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852229"
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
