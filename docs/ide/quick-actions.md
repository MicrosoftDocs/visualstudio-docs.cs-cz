---
title: Rychlé akce, žárovky a screwdrivers
ms.date: 03/28/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 71ec5cf14f4cd336b8f92c15b4f0859c7a613354
ms.sourcegitcommit: 88f576ac32af31613c1a10c1548275e1ce029f4f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71186821"
---
# <a name="quick-actions"></a>Rychlé akce

Rychlé akce vám umožní snadno Refaktorujte, generovat nebo jinak upravit kód pomocí jedné akce. Rychlé akce jsou k C#dispozici [C++](/cpp/ide/writing-and-refactoring-code-cpp)pro soubory kódu, a Visual Basic. Některé akce jsou specifické pro určitý jazyk a ostatní se vztahují na všechny jazyky.

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
> Toto téma se vztahuje k sadě Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [refaktoringing (Visual Studio pro Mac)](/visualstudio/mac/refactoring).

Rychlé akce lze použít pomocí ![](media/light-bulb-icon.png) ikony žárovky žárovky nebo ikon](media/screwdriver-icon.png) ikon Screwdriver ![Screwdriver nebo stisknutím **kombinace kláves CTRL**+ **.** Když je kurzor na řádku kódu, pro který je akce k dispozici. Pokud je červená vlnovka upozorňující ![na chybu a v](media/error-light-bulb-icon.png) aplikaci Visual Studio je k dispozici oprava pro tuto chybu, zobrazí se chybová ikona žárovky chyby světle žárovky.

Pro libovolný jazyk mohou třetí strany poskytovat vlastní diagnostiku a návrhy, například jako součást sady SDK, a na základě těchto pravidel se zobrazí žárovky sady Visual Studio.

## <a name="icons"></a>Ikony

Ikona, která se zobrazí, když je rychlá akce k dispozici, poskytne označení typu opravit nebo Refaktoring, který je k dispozici. Ikona ![ikony](media/screwdriver-icon.png) Screwdriver Screwdriver značí, že jsou k dispozici akce pro změnu kódu, ale neměli byste je nutně používat. Ikona ![ikony](media/light-bulb-icon.png) žárovky žluté žárovky indikuje, že jsou k dispozici akce, které *byste měli* udělat pro zlepšení kódu. Ikona ![ikony](media/error-light-bulb-icon.png) žárovky chyby světlejší žárovky indikuje, že je k dispozici akce, která opravuje chybu ve vašem kódu.

## <a name="to-see-a-light-bulb-or-screwdriver"></a>Chcete-li zobrazit žárovku nebo Screwdriver

Pokud je oprava k dispozici, zobrazí se žárovky:

- Když najedete myší na místo chyby

   ![Žárovka při najetí myší](../ide/media/vs2015_lightbulb_hover.png)

- V levém okraji editoru při přesunu kurzoru (kurzoru) na příslušný řádek kódu

Můžete také stisknout **klávesu CTRL**+ **.** kdekoli na řádku zobrazíte seznam dostupných rychlých akcí a refaktoringu.

Chcete-li zobrazit možné opravy, vyberte buď šipku dolů vedle žárovky nebo odkaz **Zobrazit potenciální opravy** . Zobrazí se seznam dostupných rychlých akcí.

![Rozbalení žárovky](../ide/media/vs2015_lightbulb_hover_expanded.png)

## <a name="see-also"></a>Viz také:

- [Generování kódu v aplikaci Visual Studio](../ide/code-generation-in-visual-studio.md)
- [Běžné rychlé akce](../ide/common-quick-actions.md)
- [Styly kódu a rychlé akce](../ide/code-styles-and-code-cleanup.md)
- [Zápis a refaktoring kódu (C++)](/cpp/ide/writing-and-refactoring-code-cpp)
- [Refaktoring (Visual Studio for Mac)](/visualstudio/mac/refactoring)