---
title: Rozbalení a sbalení oblasti kódu
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: b39e9613e36b45f812738ab4eab6b945727b196b
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064702"
---
# <a name="outlining"></a>Sbalování

Můžete také skrýt nějaký kód ze zobrazení sbalením oblasti kódu tak, aby se objevila pod znaménko plus (**+**). Rozbalte sbalený oblast kliknutím na symbol plus. Pokud jste uživatelem klávesnice, můžete zvolit **Ctrl**+**M**+**M** můžete rozbalit nebo sbalit. Sbalování oblastí můžete také sbalit dvojitým kliknutím na kterýkoli řádek v oblasti na okraji osnovy, které se zobrazí vlevo kód. Když najedete myší sbaleného regionu, můžete zobrazit obsah sbaleného regionu jako popisek.

> [!NOTE]
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac, najdete v části [Editor zdrojového kódu (Visual Studio for Mac)](/visualstudio/mac/source-editor).

Když najedete myší na okraji pomocí myši, jsou také zvýrazněna oblastí na okraji osnovy. Výchozí barva zvýraznění se může zdát slabé místo v některých konfiguracích barvu. Můžete změnit v **nástroje** > **možnosti** > **prostředí** > **písma a barvy**  >  **Sbalitelná oblast**.

Pokud pracujete v osnovy kódu, můžete rozbalit oddíly, které chcete pracovat, je sbalení při dokončení a poté přesuňte do další sekce. Pokud nechcete, aby sbalování zobrazí, můžete použít **ukončit sbalování** příkazu odeberte informace osnovy bez narušení základní kód.

**Zpět** a **znovu** příkazy na **upravit** nabídky, ovlivňují tyto akce. **Kopírování**, **Vyjmout**, **vložit**, a operace přetažení myší zachovat popisující informací, ale stav sbalitelná oblast. Například při kopírování oblast, která je sbalena, **vložte** operace se vložit zkopírovaný text jako rozbalená oblast.

> [!CAUTION]
> Při změně ohraničené oblasti osnovu mohou být ztraceny. Například odstranění nebo operace hledání a nahrazení můžou vymazat konec oblasti.

Následující příkazy můžete najít na **upravit** > **Osnova** podnabídka.

|||
|-|-|
|Skrýt výběr|(**Ctrl**+**M**, **Ctrl**+**H**)-sbalí vybraný blok kódu, který by se obvykle k dispozici pro sbalení, třeba `if` bloku. Chcete-li odebrat vlastní oblasti, použijte **Zastavit skrývání aktuálního** (nebo **Ctrl**+**M**, **Ctrl** + **U**). Není k dispozici v jazyce Visual Basic.|
|Přepne sbalování osnovy|– Vrátí aktuální stav skrytý nebo rozšířené nejvnitřnější sbalení části, pokud kurzor spočívá ve vnořených sbalenou část.|
|Přepnout všechny osnovy|(**Ctrl**+**M**, **Ctrl**+**L**) – nastaví všechny oblasti stejné rozbalit nebo sbalit stavu. Pokud jsou rozbaleny v některých oblastech a některé sbalena, pak sbalených oblasti jsou rozbaleny.|
|Ukončit sbalování|(**Ctrl**+**M**, **Ctrl**+**P**) – odebere všechny osnovy informace pro celý dokument.|
|Zastavit skrývání aktuálního|(**Ctrl**+**M**, **Ctrl**+**U**) – odebere sbalování informace pro aktuálně vybrané uživatelem definované oblasti. Není k dispozici v jazyce Visual Basic.|
|Sbalit do definic|(**Ctrl**+**M**, **Ctrl**+**O**)-sbalí všechny typy jako objekty její členové.|
|Sbalit blok:\<logické hraniční >|(Visual C++) Sbalí oblast ve funkci obsahující kurzor. Například pokud se kurzor nachází uvnitř smyčky, smyčky je skrytá.|
|Sbalit vše do: \<logické struktury >|(Visual C++) Sbalí všechny struktury uvnitř funkce.|

Visual Studio SDK můžete použít také k definování oblastí textu, které chcete rozbalit nebo sbalit. Zobrazit [návod: sbalení](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor zdrojového kódu (Visual Studio for Mac)](/visualstudio/mac/source-editor)