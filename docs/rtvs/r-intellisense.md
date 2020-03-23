---
title: IntelliSense pro kód R
description: Visual Studio IntelliSense zobrazuje informace o funkcích, členech objektů, fragmentech kódu a dokončení při psaní kódu R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 854f7d410e327ca92d0c5156d89bc21765e13cc7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "62999119"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense zobrazuje informace o funkcích, které můžete volat, členy objektů, argumenty funkce a [fragmenty kódu](code-snippets-for-r.md) přímo v zobrazení při psaní kódu. Zobrazuje také možné dokončení při psaní a dokončí se po stisknutí **kláves Tab** nebo **Enter** (viz [Možnosti editoru](editing-r-code-in-visual-studio.md#editor-options) pro kartu **Upřesnit).** Technologie IntelliSense je k dispozici v editoru i v [interaktivním okně](interactive-repl-for-r-in-visual-studio.md).

![Technologie IntelliSense s podpisem funkce](media/intellisense-function-signature.png)

Při psaní funkce nebo jiného příkazu poskytuje technologie IntelliSense filtrovanou nabídku automatického dokončování (malá a velká písmena) podle toho, co jste již zadali:

![Nabídka automatického dokončování technologie IntelliSense](media/intellisense-auto-complete-menu.png)

Stisknutím **klávesy Tab** (nebo **Enter**nebo **Space**v závislosti na nastavení možností) vložíte položku vybranou v rozevíracím seznamku. Výběr můžete změnit pomocí kláves se šipkami.

Technologie IntelliSense také poskytuje návrhy pro členy objektů R:

![Návrhy technologie IntelliSense pro členy objektu](media/intellisense-auto-complete-r-objects.png)

Stisknutím **klávesy ESC** nabídku zcela odmítnete. Můžete ji vrátit zpět s **Ctrl**+**Space**.

Zadáním otvoru `(` pro volání funkce `)` vložíte uzávěrku a vyvoláte nápovědu k podpisu, jak je znázorněno výše:

![Nápověda k podpisu technologie IntelliSense pro funkci](media/intellisense-function-signature.png)

Opět platí, **že ESC** odmítá vyskakovací okno; u funkčních podpisů, můžete ji znovu vyvolat pomocí **klávesctrl**+**shift**+**space**.

> [!Tip]
> Pokud parametr pomáhá zakrýt text pod ním, stiskněte a podržte klávesu **Ctrl,** aby byl parametr text průsvitný.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>Technologie IntelliSense pro uživatelem definované funkce a proměnné

Technologie IntelliSense platí pro uživatelem definované funkce ve stejném souboru, včetně dokončování parametrů názvu:

![Technologie IntelliSense pro uživatelem definované funkce](media/intellisense-same-file-functions.png)

![Dokončení parametrů IntelliSense pro uživatelem definované funkce](media/intellisense-parameter-completion.png)

Technologie IntelliSense platí také pro proměnné ve stejném souboru a aktuální relaci:

![Dokončení proměnných IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> V interaktivním okně technologie IntelliSense bere v úvahu pouze názvy v aktuální relaci R a ignoruje soubory v projektu.

## <a name="code-suggestions"></a>Návrhy kódu

Když se na okraji zobrazí žárovka (nazývaná inteligentní značka), Visual Studio naznačuje, že pro běžně používanou akci je k dispozici zástupce. Najeďte například nad čárou, která obsahuje `library` příkaz v editoru, abyste viděli žárovku. Výběrem žárovky zobrazí teces dostupných možností:

![Inteligentní značky pro R v editoru](media/intellisense-smart-tags.png)
