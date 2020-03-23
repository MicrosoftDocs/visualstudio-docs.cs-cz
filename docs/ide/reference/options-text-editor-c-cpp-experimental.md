---
title: Možnosti, textový editor, C/C++, experimentální
ms.date: 08/02/2017
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 7e239ad3d2091f334f18ec00a367fc47d5c21db3
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "77278697"
---
# <a name="options-text-editor-cc-experimental"></a>Možnosti, textový editor, C/C++, experimentální

Změnou těchto možností můžete změnit chování související s IntelliSense a databáze procházení při programování v jazyce C nebo C++. Tyto funkce jsou skutečně experimentální a mohou být upraveny nebo odebrány z sady Visual Studio v budoucí verzi.

::: moniker range="vs-2017"

Tento článek popisuje možnosti v sadě Visual Studio 2017. Pro Visual Studio 2015 vyberte **2015** ve voliči nad obsahem.

::: moniker-end

Chcete-li získat přístup k této stránce vlastností, aktivujte vyhledávací pole stisknutím **klávesctrl**+**q** a zadejte **příkaz experimental**. Hledání vyhledá stránku za několika prvními písmeny. Můžete se k němu také dostat výběrem**možnosti** **nástroje** > a rozbalením **textového editoru**, pak **C /C++** a pak zvolte **Experimentální**.

Tyto funkce jsou k dispozici v instalaci sady Visual Studio.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení prostředí IDE sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Povolení prediktivního technologie IntelliSense

Prediktivní technologie IntelliSense omezuje počet výsledků zobrazených v rozevíracím seznamu Technologie IntelliSense, takže se v kontextu zobrazují pouze výsledky, které jsou relevantní. Pokud například zadáte `int x =` a vyvoláte rozevírací soubor IntelliSense, zobrazí se pouze celá čísla nebo funkce, které vracejí celá čísla. Prediktivní technologie IntelliSense je ve výchozím nastavení vypnutá.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Povolit rychlejší načítání projektu

Od Visual Studio 2017 verze 15.3 se tato funkce nazývá **Povolit ukládání do mezipaměti projektu** a byla přesunuta na stránku vlastností [Nastavení projektu VC++.](vcpp-project-settings-projects-and-solutions-options-dialog-box.md)

Tato možnost umožňuje sadě Visual Studio ukládat data projektu do mezipaměti tak, aby při příštím otevření projektu mohla načíst data uložená v mezipaměti, nikoli je znovu načítat ze souborů projektu. Použití dat uložených v mezipaměti může výrazně urychlit dobu načítání projektu.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Další funkce na webu Visual Studio Marketplace

Další funkce textového editoru můžete procházet na [webu Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads). Příkladem jsou [rychlé opravy jazyka C++,](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017)který podporuje následující:

- **Přidání chybějící#include** – navrhne relevantní #include pro neznámé symboly ve vašem kódu

- **Přidat pomocí oboru názvů/Plně kvalifikovat symbol** - Stejně jako předchozí položka, ale pro obory názvů

- **Přidat chybějící středník**

- **Online nápověda** – Hledání chybových zpráv online

- A další...

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoring v Jazyce C++ (Blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
