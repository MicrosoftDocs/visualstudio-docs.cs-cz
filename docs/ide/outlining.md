---
title: Sbalení a rozbalení oblastí kódu
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 791663c04d1c1e79eebaed39d339d8d118ffeaae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748856"
---
# <a name="outlining"></a>Sbalování

Můžete zvolit, že chcete skrýt nějaký kód ze zobrazení sbalením oblasti kódu tak, aby se zobrazila pod znaménkem plus ( **+** ). Sbalenou oblast rozbalíte kliknutím na symbol plus. Pokud jste uživatel s klávesnicí, můžete pro sbalení a rozbalení zvolit **Ctrl** +**m** +**m** . Můžete také sbalit oblast sbalení dvojitým kliknutím na libovolný řádek v oblasti okraje osnovy, který se zobrazí pouze nalevo od kódu. Když najedete myší na sbalenou oblast, zobrazí se obsah sbalené oblasti jako ToolTip.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor).

Oblasti v okraji osnovy jsou zvýrazněny také při přesunutí ukazatele myši na okraj myší. Výchozí zvýraznění barvy se v některých konfiguracích barev může zdát nezřetelné. Můžete ho změnit v **nabídce nástroje**  > **možnosti**  > **prostředí**  > **písma a barvy**  > **sbalitelnou oblastí**.

Když pracujete v předčárovém kódu, můžete rozbalit oddíly, na kterých chcete pracovat, sbalit je po dokončení a pak přejít na jiné oddíly. Pokud nechcete, aby se zobrazovalo sbalení, můžete pomocí příkazu **zastavit sbalení** odebrat informace o přehledu, aniž byste narušili váš podkladový kód.

Tyto akce mají vliv na příkazy **zpět** a **znovu** v nabídce **Upravit** . Operace **kopírování**, **vyjmutí**, **vložení**a přetažení uchovávají informace o sbalení, ale ne stav sbalitelné oblasti. Když například kopírujete sbalenou oblast, operace **vložení** Vloží zkopírovaný text jako rozbalenou oblast.

> [!CAUTION]
> Když změníte oblast s přířádkou, může dojít ke ztrátě osnovy. Například odstranění nebo vyhledání a nahrazení operací může vymazat konec oblasti.

Následující příkazy lze najít v podnabídce **upravit** ** > .**

|||
|-|-|
|Skrýt výběr|(**Ctrl** +**M**, **CTRL** +**H**) – Sbalí vybraný blok kódu, který by normálně nebyl dostupný pro sbalení, například blok `if`. Pokud chcete odebrat vlastní oblast, použijte **zastavit skrývání současného** (nebo **CTRL** +**M**, **CTRL** +**U**). Není k dispozici v Visual Basic.|
|Přepnout rozšíření osnovy|– Vrátí aktuální skrytý nebo rozbalený stav v rámci nejvnitřnější sekce sbalení, když je kurzor umístěný ve vnořeném sbaleném oddílu.|
|Přepnout všechna sbalení|(**Ctrl** +**M**, **CTRL** +**L**) – nastaví všechny oblasti na stejný sbalený nebo rozbalený stav. Pokud jsou některé oblasti rozbalené a některé sbalené, sbalené oblasti se rozbalí.|
|Zastavit sbalení|(**Ctrl** +**M**, **CTRL** +**P**) – Odebere všechny informace o sbalení celého dokumentu.|
|Zastavit skrývání aktuálního|(**Ctrl** +**M**, **CTRL** +**U**) – odebere informace o Sbalení aktuálně vybrané uživatelem definované oblasti. Není k dispozici v Visual Basic.|
|Sbalit do definic|(**Ctrl** +**M**, **CTRL** +**O**) – sbalí členy všech typů.|
|Sbalit blok: \<logical hranici >|(C++) Sbalí oblast ve funkci, která obsahuje bod vložení. Například pokud bod vložení leží uvnitř smyčky, je smyčka skrytá.|
|Sbalit vše v: \<logical struktury >|(C++) Sbalí všechny struktury uvnitř funkce.|

Můžete také použít sadu Visual Studio SDK k definování textových oblastí, které chcete rozbalit nebo sbalit. Viz [Návod: sbalení](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Viz také:

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor)