---
title: Generování příkazů using
description: Přečtěte si, jak pomocí nabídky rychlé akce a refaktoring okamžitě přidat potřebné importy nebo direktivy using pro kód kopírování a vložení.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 38996d1cda52dfe98b6ce9cf24e5adcca6a8b069
ms.sourcegitcommit: 2cf87f79762906ccaa133a7645aa4c77a0bed7da
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2020
ms.locfileid: "96617159"
---
# <a name="add-missing-usings-in-visual-studio"></a>Přidat chybějící použití v aplikaci Visual Studio

Tato generace kódu platí pro:

- C#

- Visual Basic

**Co:** Umožňuje okamžitě přidat potřebné importy nebo [direktivy using](/dotnet/csharp/language-reference/keywords/using-directive) pro kód kopírování a vložení.

**Když:** Je běžné postup kopírování kódu z různých míst v projektu nebo jiných zdrojů a jejich vložení do nového kódu. Tato rychlá akce vyhledá chybějící direktivy importy pro kód pro kopírování a vložení a zobrazí výzvu k jejich přidání. Tato oprava kódu může také přidat odkazy z projektu do projektu.

**Proč:** Vzhledem k tomu, že rychlá akce automaticky přidává nezbytné importy, nemusíte ručně kopírovat `using` direktivy, které váš kód potřebuje.

## <a name="add-missing-usings-refactoring"></a>Přidat refaktoring chybějících použití

1. Zkopírujte kód ze souboru a vložte ho do nového bez zahrnutí nezbytných `using` direktiv. Výsledná chyba je doprovázena opravou kódu, která přidá chybějící `using` direktivy.

    > [!NOTE]
    > Tento návrh je nutné povolit v **nabídce nástroje > možnosti > textový Editor > C# > rozšířené > direktivy using**.

2. Vyberte CTRL +. Otevřete nabídku **rychlé akce a refaktoringy** .

    ![Generování příkazů using](media/generate-using-codefix.png)

3. Pokud chcete přidat chybějící odkaz, vyberte **použít \<your reference\>** .

    ![Generovat výsledek použití](media/generate-using-result.png)

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
- [Tipy pro vývojáře .NET](../csharp-developer-productivity.md)
