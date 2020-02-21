---
title: Generování příkazů using
ms.date: 02/19/2019
ms.topic: reference
author: kendrahavens
ms.author: kehavens
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- dotnet
helpviewer_keywords:
- add missing usings
ms.openlocfilehash: f3b3435e10d6bb9a71fd16b9286759b136c167f4
ms.sourcegitcommit: ea5e02720d71185f8e27fbea205024371b0c7ceb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/21/2020
ms.locfileid: "77544539"
---
# <a name="add-missing-usings-in-visual-studio"></a>Přidat chybějící použití v aplikaci Visual Studio

Tato generace kód platí pro:

- C#

**Co:** Umožňuje okamžitě přidat potřebné importy nebo [direktivy using](/dotnet/csharp/language-reference/keywords/using-directive) pro kód kopírování a vložení.

**Když:** Je běžné postup kopírování kódu z různých míst v projektu nebo jiných zdrojů a jejich vložení do nového kódu. Tato rychlá akce vyhledá chybějící direktivy importy pro kód pro kopírování a vložení a zobrazí výzvu k jejich přidání. Tato oprava kódu může také přidat odkazy z projektu do projektu.

**Proč:** Vzhledem k tomu, že rychlá akce automaticky přidává nezbytné importy, nemusíte ručně kopírovat direktivy `using`, které váš kód potřebuje.

## <a name="add-missing-usings-refactoring"></a>Přidat refaktoring chybějících použití

1. Zkopírujte kód ze souboru a vložte ho do nového bez zahrnutí nezbytných direktiv `using`. Výsledná chyba je doprovázena opravou kódu, která přidá chybějící direktivy `using`.

    > [!NOTE]
    > Tento návrh je nutné povolit v **nabídce nástroje > možnosti > textový Editor > C# > direktivy Pokročilé > Using**.

2. Vyberte CTRL +. Otevřete nabídku **rychlé akce a refaktoringy** .

    ![Generování příkazů using](media/generate-using-codefix.png)

3. Chcete-li přidat chybějící odkaz, vyberte možnost **použití \<referenční\>;** .

    ![Generovat výsledek použití](media/generate-using-result.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
