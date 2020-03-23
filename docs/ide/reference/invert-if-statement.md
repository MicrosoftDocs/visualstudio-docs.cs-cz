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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "65531592"
---
# <a name="invert-if-statement"></a>Invertování příkazů if

Toto refaktoring se vztahuje na:

- C#
- Visual Basic

**Co:** Umožňuje invertovat `if` nebo `if else` příkaz beze změny významu kódu.

**Kdy:** Když máte `if` nebo `if else` prohlášení, které by bylo lépe pochopeno, když obrácený.

**Proč:** Obrácení příkazu `if else` nebo příkazu `if` ručně může trvat mnohem déle a případně způsobit chyby. Tato oprava kódu vám pomůže provést tento refaktoring automaticky.

## <a name="invert-if-statement-refactoring"></a>Invertovat, pokud refaktoring příkazu

1. Umístěte kurzor `if` do `if else` příkazu nebo.

    ![Invertovat, pokud je to jiné](media/invert-if.png)

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

    ![Invertovat, pokud jiný kód opravit](media/invert-if-codefix.png)

3. Vyberte **Invertovat, pokud**.

    ![Invertovat, pokud dojde k jinému výsledku](media/invert-if-codefix-result.png)

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
