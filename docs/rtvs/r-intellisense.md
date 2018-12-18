---
title: Technologie IntelliSense pro kód jazyka R
description: IntelliSense ve Visual Studio zobrazí informace o funkcích, členové objektu, fragmenty kódu a dokončování při psaní kódu jazyka R.
ms.date: 01/24/2018
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: a9efdae5623c00abe4626d1bbb21af4a790fa487
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "35666862"
---
# <a name="intellisense"></a>IntelliSense

Zobrazí informace o funkcích, které bude možné volat, členy objektů, argumenty funkce IntelliSense ve Visual Studio a [fragmenty kódu](code-snippets-for-r.md) přímo ve svém zobrazení při psaní kódu. Také možná dokončení se zobrazí při psaní a skončí po stisknutí klávesy **kartu** nebo **Enter** klíče (naleznete v tématu [možnosti editoru](editing-r-code-in-visual-studio.md#editor-options) pro **Upřesnit** kartu). Technologie IntelliSense je k dispozici v editor a [interaktivní okno](interactive-repl-for-r-in-visual-studio.md).

![Technologie IntelliSense zobrazuje signatura funkce](media/intellisense-function-signature.png)

Při zadávání funkce nebo další příkaz, IntelliSense nabídne automatické dokončení nabídky (case-sensitively) Filtroval co jste už zadali:

![Nabídka Automatické doplňování technologie IntelliSense](media/intellisense-auto-complete-menu.png)

Stisknutím klávesy **kartu** (nebo **Enter**, nebo **místo**podle toho, jak nastavit možnosti), vloží položky vybrané v rozevíracím seznamu. Výběr můžete změnit pomocí kláves se šipkami.

Technologie IntelliSense také nabízí návrhy pro členy R objektů:

![Návrhy IntelliSense pro členy objektu](media/intellisense-auto-complete-r-objects.png)

Stisknutím klávesy **ESC** zavře nabídce úplně se vynechá. Můžete ho přenést zpět s **Ctrl**+**místo**.

Zadáním otevírání `(` pro funkci volání vloží uzavírací `)` a vyvolá nápovědu k signatuře, jak je uvedeno výše:

![Signaturám technologie IntelliSense pro funkci](media/intellisense-function-signature.png)

Opět **ESC** zavře automaticky otevírané okno; signatury funkce připravíte ho znovu s **Ctrl**+**Shift**+**místa** .

> [!Tip]
> Pokud parametr nápovědy skryje text pod ním, stiskněte a podržte **Ctrl** klíč, aby parametr více průchody průsvitných text nápovědy.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Technologie IntelliSense pro uživatelem definované funkce a proměnné

Technologie IntelliSense platí pro uživatelem definované funkce ve stejném souboru, včetně dokončování název parametru:

![Technologie IntelliSense pro uživatelem definované funkce](media/intellisense-same-file-functions.png)

![Parametr doplňování technologie IntelliSense pro uživatelem definované funkce](media/intellisense-parameter-completion.png)

Technologie IntelliSense platí také pro proměnné ve stejném souboru a aktuální relace:

![Proměnné doplňování technologie IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> Technologie IntelliSense v interaktivním okně, bere v úvahu pouze názvy v aktuální relaci jazyka R a ignoruje soubory ve vašem projektu.

## <a name="code-suggestions"></a>Návrhy kódu

Když na okraji se zobrazí žárovka (označované jako inteligentních značek), Visual Studio navrhuje, že je k dispozici pro běžně používané akci zástupce. Například, najeďte myší řádek, který obsahuje `library` příkaz v editoru zobrazíte žárovky. Výběr žárovky zobrazí dostupné možnosti:

![Inteligentní značky pro R v editoru](media/intellisense-smart-tags.png)
