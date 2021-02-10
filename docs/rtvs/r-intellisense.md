---
title: IntelliSense pro kód R
description: Visual Studio IntelliSense zobrazí informace o funkcích, členech objektů, fragmentech kódu a dokončováních při psaní kódu R.
ms.date: 01/24/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jmartens
ms.workload:
- data-science
ms.openlocfilehash: de6a8ffbaa0fb10929d013a351ebffa8e3f4b529
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939432"
---
# <a name="intellisense"></a>IntelliSense

Visual Studio IntelliSense zobrazí informace o funkcích, které můžete volat, členy objektů, argumenty funkce a [fragmenty kódu](code-snippets-for-r.md) přímo ve vašem zobrazení při psaní kódu. Zobrazuje taky možné dokončování při psaní a dokončuje se po stisknutí klávesy **TAB** nebo kláves **ENTER** (viz [Možnosti editoru](editing-r-code-in-visual-studio.md#editor-options) pro kartu **Upřesnit** ). Technologie IntelliSense je k dispozici v editoru i [interaktivním okně](interactive-repl-for-r-in-visual-studio.md).

![IntelliSense znázorňující signaturu funkce](media/intellisense-function-signature.png)

Když zadáte funkci nebo jiný příkaz, IntelliSense nabídne nabídku automatického dokončování filtrovanou (velká a malá písmena) podle toho, co jste už zadali:

![Nabídka automatického dokončování IntelliSense](media/intellisense-auto-complete-menu.png)

Stisknutí klávesy **TAB** (nebo **zadání nebo zadání** **mezer** v závislosti na nastavení možností) vloží položku vybranou v rozevíracím seznamu. Výběr můžete změnit pomocí kláves se šipkami.

Technologie IntelliSense také poskytuje návrhy pro členy objektů R:

![Návrhy IntelliSense pro členy objektů](media/intellisense-auto-complete-r-objects.png)

Stisknutí klávesy **ESC** zavře nabídku úplně. Můžete ho přenést pomocí **kláves CTRL** + .

Zadáním otevření `(` pro volání funkce vložíte `)` nápovědu k podpisu, jak je uvedeno výše:

![Nápovědu k podpisu IntelliSense pro funkci](media/intellisense-function-signature.png)

Znovu **ESC** zavře automaticky otevírané okno. u signatur funkcí je můžete přenést znovu s  +  + **mezerou** CTRL + SHIFT.

> [!Tip]
> Pokud v nápovědě k překrýváte text pod ním, stiskněte a podržte klávesu **CTRL** , aby text v nápovědě k parametru byl průhledný.

## <a name="intellisense-for-user-defined-functions-and-variables"></a>IntelliSense pro uživatelsky definované funkce a proměnné

Technologie IntelliSense se vztahuje na uživatelsky definované funkce ve stejném souboru, včetně dokončování názvu a parametru:

![IntelliSense pro uživatelsky definované funkce](media/intellisense-same-file-functions.png)

![Dokončování parametrů technologie IntelliSense pro uživatelsky definované funkce](media/intellisense-parameter-completion.png)

Technologie IntelliSense platí také pro proměnné ve stejném souboru a aktuální relaci:

![Dokončení proměnné technologie IntelliSense](media/intellisense-variable-completion.png)

> [!Note]
> V interaktivním okně bude IntelliSense zohledňovat pouze názvy v aktuální relaci jazyka R a ignoruje soubory v projektu.

## <a name="code-suggestions"></a>Návrhy kódu

V případě, že se na okraji zobrazuje žárovka (nazývaná inteligentní značka), Visual Studio navrhne, že je k dispozici klávesová zkratka pro běžně využívanou akci. Například najeďte myší na řádek, který obsahuje `library` příkaz v editoru, aby se zobrazila žárovka. Výběr žárovky zobrazuje dostupné možnosti:

![Inteligentní značky pro R v editoru](media/intellisense-smart-tags.png)
