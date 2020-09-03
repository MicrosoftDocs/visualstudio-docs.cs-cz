---
title: Přidat atribut DebuggerDisplay
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 611df048d4ce569c10ae933be9053acf1174c06f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85290354"
---
# <a name="add-debuggerdisplay-attribute"></a>Přidat atribut DebuggerDisplay

Tato generace kódu platí pro:

- C#

**Co:** [Atribut DebuggerDisplay](https://docs.microsoft.com/visualstudio/debugger/using-the-debuggerdisplay-attribute) určuje, jak se objekt, vlastnost nebo pole zobrazí v oknech proměnných ladicího programu.

**Když:** Do kódu lze programově [připnout vlastnosti](https://docs.microsoft.com/visualstudio/debugger/view-data-values-in-data-tips-in-the-code-editor#pin-properties-in-datatips) v rámci ladicího programu.

**Proč:** Vlastnosti připnutí umožňují rychle zkontrolovat objekty podle jejich vlastností tím, že se tato vlastnost nastaví na začátek seznamu vlastností objektu v rámci ladicího programu. 

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na typ, delegáta, vlastnost nebo pole. 

2. Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoringu** a vyberte možnost **Přidat atribut DebuggerDisplay**.

    ![Vygenerování operátorů porovnání](media/add-debugger-display-attribute.png)

3. Atribut DebuggerDisplay se přidá společně s metodou auto, která vrátí výchozí ToString (). 

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)
