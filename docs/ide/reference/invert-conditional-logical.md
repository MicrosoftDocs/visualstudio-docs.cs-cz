---
title: Invertování podmíněných výrazů a logických operací
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring Invertovat podmíněný výraz nebo podmíněný operátor OR.
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
ms.openlocfilehash: 180e42d5399116df95289e4e5fd0aed1255bf3de
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617380"
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
