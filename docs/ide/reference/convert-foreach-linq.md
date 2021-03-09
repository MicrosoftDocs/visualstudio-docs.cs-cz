---
title: Převést smyčku foreach na LINQ
description: Převeďte všechny smyčky foreach, které používají rozhraní IEnumerable pro dotaz LINQ nebo formulář volání LINQ (označované také jako metoda LINQ).
ms.date: 07/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
ms.workload:
- dotnet
ms.openlocfilehash: 8ff489e11cc5c61c5e840b4b12d05ba5da46ce41
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466287"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Převést smyčku foreach na LINQ

Tento refaktoring platí pro:

- C#

**Co:** Umožňuje snadno převést smyčku *foreach* , která používá rozhraní IEnumerable pro dotaz LINQ nebo formulář volání LINQ (označované také jako metoda LINQ).

**Když:** Máte smyčku foreach, která používá rozhraní IEnumerable a chcete, aby se tato smyčka četla jako dotaz LINQ.

**Proč:** Dáváte přednost použití syntaxe LINQ spíše než smyčky foreach. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) vytvoří dotaz do konstrukce jazyka první třídy v jazyce C#. LINQ může snížit množství kódu v souboru, usnadnit čtení kódu a umožnit různým zdrojům dat, aby měly podobné vzory výrazů dotazů.

> [!NOTE]
> Syntaxe LINQ je obvykle méně efektivní než smyčka foreach. Je dobré si uvědomit o všech kompromisech s výkonem, které mohou nastat při použití jazyka LINQ ke zlepšení čitelnosti kódu.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Převést smyčku foreach na refaktoring LINQ

1. Umístěte kurzor do `foreach` klíčového slova.

    ![Foreach s použitím ukázky IEnumerable](media/convert-foreach-to-LINQ.png)

2. Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   ![Ukázka převodu na nabídku LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Vyberte možnost **převést na LINQ** nebo **převést na LINQ (formulář volání)**.

   ![Ukázka výsledku dotazu LINQ](media/convert-foreach-to-LINQ-result.png)

   ![Ukázka výsledku formuláře volání LINQ](media/convert-foreach-to-LINQ-callform-result.png)

### <a name="sample-code"></a>Ukázka kódu

```csharp
using System.Collections.Generic;

public class Class1
{
    public void MyMethod()
    {
        var greetings = new List<string>()
            { "hi", "yo", "hello", "howdy" };

        IEnumerable<string> enumerable()
        {
            foreach (var greet in greetings)
            {
                if (greet.Length < 3)
                {
                    yield return greet;
                }
            }

            yield break;
        }
    }
}
```

## <a name="see-also"></a>Viz také

- [Refactoring](../refactoring-in-visual-studio.md)
- [Okno Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře na platformě .NET](../csharp-developer-productivity.md)
