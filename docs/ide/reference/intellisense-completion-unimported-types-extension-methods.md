---
title: Dokončení technologie IntelliSense pro typy & metody rozšíření
description: Jak používat technologii IntelliSense doplňování pro typy a metody rozšíření, které ještě nebyly importovány s `using` direktivou.
ms.custom: SEO-VS-2020
ms.date: 07/27/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d2ac806b4a83b23a783c59eeee5df801c9237685
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/19/2020
ms.locfileid: "94900917"
---
# <a name="intellisense-completion-for-unimported-types-and-extension-methods"></a>Dokončení technologie IntelliSense pro neimportované typy a metody rozšíření

Tento refaktoring platí pro:

- C#

- Visual Basic

**Co:** Technologie IntelliSense poskytuje pro neimportované typy a metody rozšíření.

**Když:** Chcete použít metody typu nebo rozšíření, které již mají závislost v projektu, ale příkaz using ještě nebyl do souboru přidán.

**Proč:** Příkaz using nemusíte do souboru přidávat ručně.

## <a name="how-to"></a>Postupy

1. Po zahájení psaní názvu typu nebo metody rozšíření, která má závislost v projektu, vám IntelliSense nabídne návrhy. Položky z neimportovaných oborů názvů budou mít svůj obor názvů, který je zobrazen jako přípona.

   > [!TIP]
   > Můžete zobrazit nebo skrýt položky z neimportovaných oborů názvů na vyžádání pomocí **rozbalovacího tlačítka (ALT + A)** , které se zobrazí v levém dolním rohu seznamu dokončení. Chcete-li změnit výchozí chování, přejděte do části **nástroje**  >  **Možnosti**  >  **textový editor**  >  **C#**  /  **základní**  >  **IntelliSense** a vyhledejte **položku Zobrazit položky z neimportované obory názvů**.

2. Vyberte a potvrďte neimportované položky.

   Příkaz using bude automaticky přidán do souboru.

   ![Dokončení IntelliSense pro neimportované typy](media/intellisense-completion-unimported-types.png)

## <a name="see-also"></a>Viz také

- [IntelliSense](../using-intellisense.md)
- [Refactoring](../refactoring-in-visual-studio.md)
