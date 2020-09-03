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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278697"
---
# <a name="options-text-editor-cc-experimental"></a>Možnosti, textový editor, C/C++, experimentální

Změnou těchto možností můžete změnit chování související s technologií IntelliSense a databází procházení při programování v jazyce C nebo C++. Tyto funkce jsou skutečně experimentální a můžou se v budoucí verzi upravovat nebo odebírat v rámci sady Visual Studio.

::: moniker range="vs-2017"

Tento článek popisuje možnosti sady Visual Studio 2017. V případě sady Visual Studio 2015 vyberte v selektoru nad obsahem položku **2015** .

::: moniker-end

Chcete-li získat přístup k této stránce vlastností, stiskněte klávesu **CTRL** + **Q** pro aktivaci vyhledávacího pole a pak zadejte **experimentální**. Hledání najde stránku za několika prvních písmeny. K tomu se můžete dostat taky tak, **Tools**že vyberete  >  **Možnosti** nástrojů a rozbalíte **textový editor**, pak **C/C++** a pak zvolíte **experimentální**.

Tyto funkce jsou k dispozici v instalaci sady Visual Studio.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Viz [Přizpůsobení integrovaného vývojového prostředí sady Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-predictive-intellisense"></a>Povolit prediktivní IntelliSense

Prediktivní technologie IntelliSense omezuje počet výsledků zobrazených v rozevíracím seznamu technologie IntelliSense tak, aby se zobrazily pouze výsledky, které jsou relevantní v kontextu. Například pokud zadáte `int x =` a vyvoláte rozevírací seznam IntelliSense, zobrazí se pouze celá čísla nebo funkce vracející celá čísla. Prediktivní technologie IntelliSense je ve výchozím nastavení vypnutá.

::: moniker range="vs-2017"

## <a name="enable-faster-project-load"></a>Povolit rychlejší načítání projektů

Počínaje verzí sady Visual Studio 2017 verze 15,3 Tato funkce označuje **možnost Povolit ukládání projektů do mezipaměti** a přesunula se na stránku vlastností [nastavení projektu VC + +](vcpp-project-settings-projects-and-solutions-options-dialog-box.md) .

Tato možnost umožňuje aplikaci Visual Studio ukládat data projektu do mezipaměti, aby při příštím otevření projektu mohla načíst tato data z mezipaměti, nikoli znovu provést zpracování ze souborů projektu. Použití dat uložených v mezipaměti může výrazně zrychlit dobu načítání projektu.

::: moniker-end

## <a name="additional-features-in-the-visual-studio-marketplace"></a>Další funkce v Visual Studio Marketplace

V [Visual Studio Marketplace](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=All&sortBy=Downloads)můžete procházet další funkce textového editoru. Příkladem jsou [rychlé opravy v jazyce C++](https://marketplace.visualstudio.com/items?itemName=VisualCppDevLabs.CQuickFixes2017), které podporují následující:

- **Přidat chybějící #include** – navrhuje relevantní #include pro neznámé symboly v kódu

- **Přidat pomocí oboru názvů nebo plně kvalifikovat symbol** podobný předchozí položce, ale pro obory názvů

- **Přidat chybějící středník**

- **Online nápovědu** – prohledání online nápovědu pro chybové zprávy

- A další...

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoring v C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/
)
