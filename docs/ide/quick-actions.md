---
title: Rychlé akce, žárovky a screwdrivers
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596954"
---
# <a name="quick-actions"></a>Rychlé akce

Rychlé akce umožňují snadno Refaktorovat, generovat nebo jinak upravovat kód jedinou akcí. Rychlé akce jsou k dispozici pro soubory kódu C#, [C++](/cpp/ide/writing-and-refactoring-code-cpp)a Visual Basic. Některé akce jsou specifické pro určitý jazyk a ostatní se vztahují na všechny jazyky.

Rychlé akce lze použít k těmto akcím:

- Použití opravy kódu pro porušení pravidla [analyzátoru kódu](../code-quality/roslyn-analyzers-overview.md)

::: moniker range=">=vs-2019"

- [Potlačit](../code-quality/use-roslyn-analyzers.md#suppress-violations) porušení pravidla analyzátoru kódu nebo [nakonfigurovat](../code-quality/use-roslyn-analyzers.md#automatically-configure-rule-severity) jeho závažnost

::: moniker-end

::: moniker range="vs-2017"

- [Potlačit](../code-quality/use-roslyn-analyzers.md#suppress-violations) porušení pravidla analyzátoru kódu

::: moniker-end

- Použít refaktoring (například [Vložit dočasnou proměnnou](../ide/reference/inline-temporary-variable.md))

- Generovat kód (například [zavést místní proměnnou](../ide/reference/introduce-local-variable.md))

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [refaktoringing (Visual Studio pro Mac)](/visualstudio/mac/refactoring).

Rychlé akce lze použít pomocí ikony žárovky žárovky ![ ](media/light-bulb-icon.png) nebo ![ ikon ikon Screwdriver Screwdriver ](media/screwdriver-icon.png) nebo stisknutím **kombinace kláves CTRL** + **.** Když je kurzor na řádku kódu, pro který je akce k dispozici. ![ ](media/error-light-bulb-icon.png) Pokud je červená vlnovka upozorňující na chybu a v aplikaci Visual Studio je k dispozici oprava pro tuto chybu, zobrazí se chybová ikona žárovky chyby světle žárovky.

Pro libovolný jazyk mohou třetí strany poskytovat vlastní diagnostiku a návrhy, například jako součást sady SDK, a na základě těchto pravidel se zobrazí žárovky sady Visual Studio.

## <a name="icons"></a>Ikony

Ikona, která se zobrazí, když je rychlá akce k dispozici, poskytne označení typu opravit nebo Refaktoring, který je k dispozici. *screwdriver* ![ Ikona ikony Screwdriver Screwdriver ](media/screwdriver-icon.png) značí, že jsou k dispozici akce pro změnu kódu, ale neměli byste je nutně používat. *yellow light bulb* ![ Ikona ikony žárovky žluté žárovky ](media/light-bulb-icon.png) indikuje, že jsou k dispozici akce, které *byste měli* udělat pro zlepšení kódu. Ikona ikony žárovky chyby světlejší *žárovky* ![ ](media/error-light-bulb-icon.png) indikuje, že je k dispozici akce, která opravuje chybu ve vašem kódu.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Chcete-li zobrazit žárovku nebo Screwdriver

Pokud je oprava k dispozici, zobrazí se žárovky:

- Když najedete myší na místo chyby

   ![Žárovka při najetí myší](../ide/media/vs2015_lightbulb_hover.png)

- V levém okraji editoru při přesunu kurzoru (kurzoru) na příslušný řádek kódu

Můžete také stisknout **klávesu CTRL** + **.** kdekoli na řádku zobrazíte seznam dostupných rychlých akcí a refaktoringu.

Chcete-li zobrazit možné opravy, vyberte buď šipku dolů vedle žárovky nebo odkaz **Zobrazit potenciální opravy** . Zobrazí se seznam dostupných rychlých akcí.

![Rozbalení žárovky](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Viz také

- [Generování kódu v aplikaci Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Běžné rychlé akce](../ide/common-quick-actions.md)
- [Styly kódu a rychlé akce](../ide/code-styles-and-code-cleanup.md)
- [Zápis a refaktoring kódu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoring (Visual Studio pro Mac)](/visualstudio/mac/refactoring)
