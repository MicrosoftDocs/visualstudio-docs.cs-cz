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
ms.openlocfilehash: 78786e6e6e7a8e5d8a8766138cb1a54a49416f9a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610894"
---
# <a name="add-missing-usings-in-visual-studio"></a>Přidat chybějící použití v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje okamžitě přidat potřebné importy nebo [direktivy using](/dotnet/csharp/language-reference/keywords/using-directive) pro kód kopírování a vložení.

**Když:** Je běžné postup kopírování kódu z různých míst v projektu nebo jiných zdrojů a jejich vložení do nového kódu. Tato rychlá akce vyhledá chybějící direktivy importy pro kód pro kopírování a vložení a zobrazí výzvu k jejich přidání.

**Proč:** Vzhledem k tomu, že rychlá akce automaticky přidává nezbytné importy, nemusíte ručně kopírovat direktivy `using`, které váš kód potřebuje.

## <a name="add-missing-usings-refactoring"></a>Přidat refaktoring chybějících použití

1. Zkopírujte kód ze souboru a vložte ho do nového bez zahrnutí nezbytných direktiv `using`. Výsledná chyba je doprovázena opravou kódu, která přidá chybějící direktivy `using`.

    > [!NOTE]
    > Tento návrh je nutné povolit v **nabídce nástroje > možnosti > textový Editor > C# > direktivy Pokročilé > Using**.

2. Vyberte CTRL +. Otevřete nabídku **rychlé akce a refaktoringy** .

    ![Generování příkazů using](media/generate-using-codefix.png)

3. Pokud chcete přidat chybějící odkaz, vyberte **použít \<your referenční \>;** .

    ![Generovat výsledek použití](media/generate-using-result.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
