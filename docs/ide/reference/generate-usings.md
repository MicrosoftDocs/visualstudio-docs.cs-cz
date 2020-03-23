---
title: Generování příkazů using
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
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: 903b160bac0e8096062e09fd78ff4c92c46cf8ee
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094311"
---
# <a name="add-missing-usings-in-visual-studio"></a>Přidání chybějících použití v sadě Visual Studio

Toto generování kódu se vztahuje na:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě přidat potřebné importy nebo [pomocí direktiv](/dotnet/csharp/language-reference/keywords/using-directive) pro kopírování a vkládání kódu.

**Kdy:** Je běžnou praxí kopírovat kód z různých míst v projektu nebo z jiných zdrojů a vložit jej do nového kódu. Tato rychlá akce vyhledá chybějící direktivy importu pro kód kopírování a vložení a zobrazí výzvu k jejich přidání. Tato oprava kódu můžete také přidat odkazy z projektu do projektu.

**Proč:** Vzhledem k tomu, že rychlá akce automaticky přidá potřebné `using` importy, není nutné ručně kopírovat direktivy, které váš kód potřebuje.

## <a name="add-missing-usings-refactoring"></a>Přidání chybějících použití refaktoringu

1. Zkopírujte kód ze souboru a vložte jej `using` do nového bez zahrnutí nezbytných směrnic. Výsledná chyba je doprovázena opravou kódu, `using` která přidá chybějící direktivy.

    > [!NOTE]
    > Tento návrh je třeba povolit v **aplikaci Nástroje > možnosti > textový editor > C# > rozšířené > pomocí direktiv .**

2. Vyberte Ctrl+. otevřete nabídku **Rychlé akce a Refaktorings.**

    ![Generování příkazů using](media/generate-using-codefix.png)

3. Vyberte ** \<pomocí\>odkazu ;** chcete-li přidat chybějící odkaz.

    ![Generovat výsledek použití](media/generate-using-result.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
