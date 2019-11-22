---
title: Možnosti, textový editor, C-C++, experimentální | Microsoft Docs
ms.date: 11/15/2016
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5979363f16f2e9d78a2f50ffbb6511d03146caaa
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297858"
---
# <a name="options-text-editor-cc-experimental"></a>Možnosti, textový editor, C/C++, experimentální
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Změnou těchto možností můžete změnit chování související s technologií IntelliSense a databází procházení při programování v jazyce C nebo C++.

 Chcete-li získat přístup k této stránce, v dialogovém okně **Možnosti** rozbalte v levém podokně položku **textový editor**, rozbalte položku **C++C/** a pak zvolte možnost **experimentální**.

 Tyto funkce jsou k dispozici v instalaci sady Visual Studio 2015 Update 1 RC.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Zobrazit [přizpůsobení nastavení pro vývoj v sadě Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="browsingnavigation"></a>Procházení/navigace
 **Povolit nový databázový stroj** To by mělo automaticky zrychlit naplnění databáze a zrychlit všechny operace databáze (bez ztráty přesnosti) pro operace, jako je například **Přejít k definici** a **Najít všechny odkazy**. (Stačí zavřít a znovu otevřít řešení, aby se změny projevily. není nutné restartovat Visual Studio.)

## <a name="intellisense"></a>IntelliSense
 **Seznam členů s tečkami na šipku** Nahradí '. ' s '-> ', pokud je použit pro seznam členů.

## <a name="refactoring"></a>Refaktoring
 **Povolit extrakci funkce** Extrahujte vybraný kód do vlastní funkce a nahraďte kód voláním nové funkce. Chcete-li získat přístup k této funkci, klikněte pravým tlačítkem myši na vybraný kód a vyberte **rychlé akce**, nebo jednoduše stiskněte výchozí klávesovou zkratku CTRL + tečka [CTRL +.].

 **Povolit změnu signatury** Umožňuje přidat, změnit pořadí a odstranit parametry funkce a rozšířit změny na všechny lokality volání. Přístup k této funkci získáte tak, že kliknete pravým tlačítkem na jakékoli použití funkce a vyberete **rychlé akce**, nebo jednoduše stisknete výchozí klávesovou zkratku CTRL + tečka [CTRL +.].

## <a name="text-editor"></a>Textový editor
 **Povolit rozbalení oborů** Pokud je povoleno, můžete vybraný text uzavřít do složených závorek zadáním "{" do textového editoru.

 **Povolit rozbalení priority** Pokud je povoleno, můžete vybraný text uzavřít závorkami zadáním ' (' do textového editoru.

 Další funkce textového editoru v galerii sady Visual Studio najdete v [tomto](https://go.microsoft.com/fwlink/?LinkId=692016)seznamu. Příkladem jsou [ C++ rychlé opravy](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), které podporují následující:

- **Přidat chybějící #include** – navrhuje relevantní #include pro neznámé symboly v kódu

- **Přidat pomocí oboru názvů nebo plně kvalifikovat symbol** podobný předchozí položce, ale pro obory názvů

- **Přidat chybějící středník**

- **Nápovědu MSDN** – prohledejte vaše chybové zprávy na webu MSDN

  Chcete-li získat žárovku žárovky nebo použít výchozí klávesovou zkratku CTRL + tečka (CTRL +.), můžete buď najeďte myší na vlnovku. Všimněte si, že u klávesové zkratky není potřeba blikající kurzor umístit na konkrétní chybu nebo token; k vyvolání návrhů na cokoli na daném řádku můžete jednoduše použít stejný řádek jako chyba.

## <a name="see-also"></a>Viz také
 Nastavení refaktoringu [možností editoru specifických](../../ide/reference/setting-language-specific-editor-options.md) [pro C++ jazyk (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
