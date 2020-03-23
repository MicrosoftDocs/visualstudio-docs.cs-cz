---
title: Převést smyčku foreach na LINQ
descritpion: Convert any foreach loop that uses an IEnumerable to a LINQ query or a LINQ call form (also known as a LINQ method).
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
ms.openlocfilehash: 12c03830ccd37e0970e3c74bc78cdd9c8a8732b7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094218"
---
# <a name="convert-a-foreach-loop-to-linq"></a>Převést smyčku foreach na LINQ

Toto refaktoring se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje snadno převést *foreach* smyčky, která používá IEnumerable na linq dotazu nebo linq volání formuláře (také známý jako metoda LINQ).

**Kdy:** Máte foreach smyčky, která používá IEnumerable a chcete, aby smyčka číst jako dotaz LINQ.

**Proč:** Dáváte přednost použití syntaxe LINQ spíše než foreach smyčky. [LINQ](/dotnet/csharp/programming-guide/concepts/linq/introduction-to-linq) provede dotaz do konstrukce jazyka první třídy v jazyce C#. LINQ můžete snížit množství kódu v souboru, usnadnit čtení kódu a povolit různé zdroje dat mít podobné vzory výrazů dotazu.

> [!NOTE]
> Syntaxe LINQ je obvykle méně efektivní než foreach smyčky. Je dobré být si vědom všech výkonu kompromisu, který může nastat při použití LINQ ke zlepšení čitelnosti kódu.

## <a name="convert-a-foreach-loop-to-linq-refactoring"></a>Převést smyčku foreach na refaktoring LINQ

1. Umístěte kurzor `foreach` do klíčového slova.

    ![Foreach pomocí souboru IEnumerable vzorku](media/convert-foreach-to-LINQ.png)

2. Stiskněte **klávesu Ctrl**+**.** spouštět nabídku **Rychlé akce a Refaktorings.**

   ![Převést na ukázku nabídky LINQ](media/convert-foreach-to-LINQ-codefix.png)

3. Vyberte **Převést na LINQ** nebo **Převést na Linq (formulář volání).**

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
- [Tipy pro vývojáře rozhraní .NET](../csharp-developer-productivity.md)
