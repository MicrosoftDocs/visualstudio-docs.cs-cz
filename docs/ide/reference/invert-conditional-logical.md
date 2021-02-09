---
title: Invertování podmíněných výrazů a logických operací
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring Invertovat podmíněný výraz nebo podmíněný operátor OR.
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
ms.openlocfilehash: 0bd75a40f52a6148a6c50b212183bb8dc7a52d56
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99852242"
---
# <a name="invert-conditional-expressions-and-conditional-andor-operators"></a>Invertovat podmíněné výrazy a podmíněné operátory AND/OR

Tento refaktoring platí pro:

- C#
- Visual Basic

**Co:** Umožňuje invertovat podmíněný výraz nebo podmíněný operátor AND/OR.

**Když:** Máte podmíněný výraz nebo podmíněný operátor AND/OR, který by měl být lépe srozumitelný, pokud se obrátí.

**Proč:** Obrácení výrazu nebo podmíněného operátoru OR ručně může trvat mnohem delší dobu a může způsobit chyby. Tato oprava kódu vám pomůže tento Refaktorovat automaticky.

## <a name="invert-conditional-expressions-and-conditional-andor-operators-refactoring"></a>Invertování podmíněných výrazů a podmíněného refaktoringu a/nebo operátorů

1. Umístěte kurzor do podmíněného výrazu nebo podmíněného operátoru OR.
2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .
3. Vyberte **Invertovat podmíněné** nebo **nahraďte ' && ' znakem ' | | '**

    ![Snímek obrazovky s možností Invertovat podmíněný](media/invert-conditional.png)

    ![Snímek obrazovky nahrazující && s | | nastavení.](media/invert-logical-operator.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
