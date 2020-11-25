---
title: Přidat atribut DebuggerDisplay
description: Naučte se, jak přidat atribut DebuggerDisplay pro řízení způsobu, jakým okno proměnné ladicího programu zobrazuje objekt, vlastnost nebo pole.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871116"
---
# <a name="add-debuggerdisplay-attribute"></a>Přidat atribut DebuggerDisplay

Tato generace kódu platí pro:

- C#

**Co:** [Atribut DebuggerDisplay](../../debugger/using-the-debuggerdisplay-attribute.md) určuje, jak se objekt, vlastnost nebo pole zobrazí v oknech proměnných ladicího programu.

**Když:** Do kódu lze programově [připnout vlastnosti](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips) v rámci ladicího programu.

**Proč:** Vlastnosti připnutí umožňují rychle zkontrolovat objekty podle jejich vlastností tím, že se tato vlastnost nastaví na začátek seznamu vlastností objektu v rámci ladicího programu. 

## <a name="how-to"></a>Postupy

1. Umístěte kurzor na typ, delegáta, vlastnost nebo pole. 

2. Stiskněte klávesu **CTRL** + **.** Chcete-li aktivovat nabídku **rychlé akce a refaktoringu** a vyberte možnost **Přidat atribut DebuggerDisplay**.

    ![Vygenerování operátorů porovnání](media/add-debugger-display-attribute.png)

3. Atribut DebuggerDisplay se přidá společně s metodou auto, která vrátí výchozí ToString (). 

## <a name="see-also"></a>Viz také

- [Generování kódu](../code-generation-in-visual-studio.md)
- [Náhled změn](../../ide/preview-changes.md)