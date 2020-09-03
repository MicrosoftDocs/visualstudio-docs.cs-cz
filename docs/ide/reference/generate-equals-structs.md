---
title: Generování operátorů IEquatable pro struktury
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ccc5be9debbdc2b4901d4aad15a0dc4d2bf1bb9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290330"
---
# <a name="generate-iequatable-operators-when-generating-equals-for-structs"></a>Generovat operátory IEquatable při generování se rovná pro struktury

Tato generace kódu platí pro:

- C#

**Co:** Umožňuje generovat operátory **Equals** a **IEquatable** pro [struktury](https://docs.microsoft.com/dotnet/csharp/language-reference/builtin-types/struct).

**Když:** Máte strukturu, automaticky přidáme IEquatable a také operátory Equals a NOT Equals.

**Proč:**

- Pokud implementujete typ hodnoty, měli byste zvážit přepsání metody **Equals** , aby se zvýšil výkon při výchozí implementaci metody Equals na ValueType.

- Implementující rozhraní IEquatable implementuje metodu rovnosti () specifickou pro typ.

## <a name="how-to"></a>Postupy

1. Umístěte kurzor někam na řádek deklarace struktury.

2. Dále proveďte jednu z následujících akcí:

   - Stiskněte klávesu **CTRL** + **.** pro aktivaci nabídky **rychlé akce a refaktoringy** .

   - Klikněte pravým tlačítkem a vyberte nabídku **rychlé akce a refaktoring** .

   - Klikněte na ![screwdriver](../media/screwdriver-icon.png) ikona, která se zobrazí na levém okraji

   ![Generovat IEquatable a Equals pro struktury](media/generate-equals-structs.png)

3. V rozevírací nabídce vyberte **Generovat Equals (objekt)** .

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
