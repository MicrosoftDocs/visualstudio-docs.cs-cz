---
title: Sbalení a rozbalení oblastí kódu
description: Přečtěte si, jak můžete použít příkazy rozbalení a sbalení pro práci v režimu osnovy v aplikaci Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 10/15/2020
ms.topic: conceptual
helpviewer_keywords:
- outlining
- Visual Studio, expand/collapse code
- Visual Studio, outlining
- expand/collapse code
- code [Visual Studio], outlining
- code [Visual Studio], hiding
- outlining code
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e45d7192c35ed60442fadf1a3eb302997fbaf381
ms.sourcegitcommit: c9a84e6c01e12ccda9ec7072dd524830007e02a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2020
ms.locfileid: "92136664"
---
# <a name="outlining"></a>Sbalování

Můžete zvolit skrytí kódu ze zobrazení sbalením oblasti kódu tak, aby se zobrazila pod znaménkem plus ( **+** ). Sbalenou oblast rozbalíte kliknutím na symbol plus. Pokud jste uživatel s klávesnicí, můžete vybrat možnost **CTRL** + **m** + **m** pro sbalení a rozbalení. Můžete také sbalit oblast sbalení dvojitým kliknutím na libovolný řádek v oblasti okraje osnovy, který se zobrazí pouze nalevo od kódu. Když najedete myší na sbalenou oblast, zobrazí se obsah sbalené oblasti jako ToolTip.

> [!NOTE]
> Toto téma se týká sady Visual Studio ve Windows. Visual Studio pro Mac naleznete v tématu [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor).

Oblasti v okraji osnovy jsou zvýrazněny také při přesunutí ukazatele myši na okraj myší. Výchozí zvýraznění barvy se v některých konfiguracích barev může zdát nezřetelné. Můžete ho změnit v **nabídce nástroje**  >  **Možnosti**  >  **prostředí**  >  **písma a barvy**–  >  **sbalitelná oblast**.

Když pracujete v předčárovém kódu, můžete rozbalit oddíly, na kterých chcete pracovat, sbalit je po dokončení a pak přejít na jiné oddíly. Pokud nechcete, aby se zobrazovalo sbalení, můžete pomocí příkazu **zastavit sbalení** odebrat informace o přehledu, aniž byste narušili váš podkladový kód.

Tyto akce mají vliv na příkazy **zpět** a **znovu** v nabídce **Upravit** . Operace **kopírování**, **vyjmutí**, **vložení**a přetažení uchovávají informace o sbalení, ale ne stav sbalitelné oblasti. Když například kopírujete sbalenou oblast, operace **vložení** Vloží zkopírovaný text jako rozbalenou oblast.

> [!CAUTION]
> Když změníte oblast s přířádkou, může dojít ke ztrátě osnovy. Například odstranění nebo **vyhledání a nahrazení** operací může vymazat konec oblasti.

Následující příkazy lze najít v podnabídce **Upravit**  >  **sbalení** .

|Název|Popis|
|-|-|
|Skrýt výběr|(**CTRL** + **M**, **CTRL** + **H**) – Sbalí vybraný blok kódu, který by normálně nebyl dostupný pro sbalení, například `if` blok. Pokud chcete odebrat vlastní oblast, použijte **zastavit skrývání současného** (nebo **CTRL** + **M**, **CTRL** + **U**). Není k dispozici v Visual Basic.|
|Přepnout rozšíření osnovy| (**CTRL** + **M**, **CTRL** + **m**) – vrátí aktuální skrytý nebo rozbalený stav nejvnitřnější sekce sbalení, pokud kurzor leží ve vloženém sbaleném oddílu.|
|Přepnout všechna sbalení|(**CTRL** + **M**, **CTRL** + **L**) – nastaví všechny oblasti na stejný sbalený nebo rozbalený stav. Pokud jsou některé oblasti rozbalené a některé sbalené, sbalené oblasti se rozbalí.|
|Zastavit sbalení|(**CTRL** + **M**, **CTRL** + **P**) – Odebere všechny informace o sbalení celého dokumentu.|
|Zastavit skrývání aktuálního|(**CTRL** + **M**, **CTRL** + **U**) – odebere informace o Sbalení aktuálně vybrané uživatelem definované oblasti. Není k dispozici v Visual Basic.|
|Sbalit do definic|(**CTRL** + **M**, **CTRL** + **O**) – sbalí členy všech typů.|
|Sbalit blok:\<logical boundary>|Volat Sbalí oblast ve funkci, která obsahuje bod vložení. Například pokud bod vložení leží uvnitř smyčky, je smyčka skrytá.|
|Sbalit vše v: \<logical structures>|Volat Sbalí všechny struktury uvnitř funkce.|

Můžete také použít sadu Visual Studio SDK k definování textových oblastí, které chcete rozbalit nebo sbalit. Viz [Návod: sbalení](../extensibility/walkthrough-outlining.md).

## <a name="see-also"></a>Viz také

- [Funkce editoru kódu](../ide/writing-code-in-the-code-and-text-editor.md)
- [Editor zdrojového kódu (Visual Studio pro Mac)](/visualstudio/mac/source-editor)
