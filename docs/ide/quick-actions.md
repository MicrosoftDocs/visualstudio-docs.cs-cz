---
title: Rychlé akce, žárovky a šroubováky
ms.date: 03/28/2018
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 2ce8ce85e027a7ed7f78d0da1f68f328c1ca103d
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596954"
---
# <a name="quick-actions"></a>Rychlé akce

Rychlé akce umožňují snadno refaktorovat, generovat nebo jinak upravovat kód pomocí jediné akce. Rychlé akce jsou k dispozici pro soubory kódu jazyka C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)a Visual Basic. Některé akce jsou specifické pro jazyk a jiné platí pro všechny jazyky.

Rychlé akce lze použít k:

- Použití opravy kódu pro porušení pravidel [analyzátoru kódu](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Potlačit](../code-quality/use-roslyn-analyzers.md#suppress-violations) porušení pravidel analyzátoru kódu nebo [nakonfigurovat](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity) jeho závažnost

::: moniker-end

::: moniker range="vs-2017"

- [Potlačení](../code-quality/use-roslyn-analyzers.md#suppress-violations) porušení pravidel analyzátoru kódu

::: moniker-end

- Použití refaktoringu (například [vložky dočasné proměnné)](../ide/reference/inline-temporary-variable.md)

- Generovat kód (například [zavést místní proměnnou)](../ide/reference/introduce-local-variable.md)

> [!NOTE]
> Toto téma platí pro Visual Studio v systému Windows. Visual Studio pro Mac najdete [v tématu Refaktoring (Visual Studio for Mac).](/visualstudio/mac/refactoring)

Rychlé akce lze použít pomocí ![ikony](media/light-bulb-icon.png) žárovky nebo ![ikony](media/screwdriver-icon.png) ikon šroubováku šroubováku nebo stisknutím **klávesctrl**+**.** pokud je kurzor na řádku kódu, pro který je k dispozici akce. Pokud je k dispozici ![červená vlnovka](media/error-light-bulb-icon.png) označující chybu, zobrazí se ikona chybové žárovky chyby žárovky a Visual Studio má k dispozici opravu pro tuto chybu.

Pro libovolný jazyk mohou třetí strany poskytnout vlastní diagnostiku a návrhy, například jako součást sady SDK, a žárovky sady Visual Studio se zobrazí na základě těchto pravidel.

## <a name="icons"></a>Ikony

Ikona, která se zobrazí, když je k dispozici rychlá akce, ukazuje typ opravy nebo refaktoringu, který je k dispozici. ](media/screwdriver-icon.png) Ikona *šroubováku šroubováku* ![označuje pouze to, že jsou k dispozici akce pro změnu kódu, ale neměli byste je nutně používat. Ikona *žárovky žluté žárovky* ![označuje, že jsou k dispozici akce, které byste měli udělat pro zlepšení kódu. *should* ](media/light-bulb-icon.png) Ikona chybové *žárovky* ![error bulb indikuje, že je k dispozici akce, která opravuje chybu ve vašem kódu.](media/error-light-bulb-icon.png)

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Zobrazení žárovky nebo šroubováku

Pokud je k dispozici oprava, zobrazí se žárovky:

- Když najedete myší na místo chyby

   ![Žárovka s myší vznášející se](../ide/media/vs2015_lightbulb_hover.png)

- V levém okraji editoru, když přesunete stříška (kurzor) do příslušného řádku kódu

Můžete také stisknout **klávesu Ctrl**+**.** kdekoli na řádku zobrazíte seznam dostupných rychlých akcí a refaktoringů.

Chcete-li zobrazit potenciální opravy, vyberte buď šipku dolů vedle žárovky, nebo odkaz **Zobrazit potenciální opravy.** Zobrazí se seznam dostupných rychlých akcí.

![Rozbalení žárovky](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Viz také

- [Generování kódu v sadě Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Běžné rychlé akce](../ide/common-quick-actions.md)
- [Styly kódu a rychlé akce](../ide/code-styles-and-code-cleanup.md)
- [Psát a refaktorovat kód (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoring (Visual Studio pro Mac)](/visualstudio/mac/refactoring)
