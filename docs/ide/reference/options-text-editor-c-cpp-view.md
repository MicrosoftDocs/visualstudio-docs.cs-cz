---
title: Zobrazit možnosti, textový Editor, C/C++
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: mikeblome
ms.author: mblome
manager: wpickett
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.workload:
- cplusplus
ms.openlocfilehash: c4ffef0b1b76f453048ff20e3cbada0b8a591c65
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388829"
---
# <a name="options-text-editor-cc-view"></a>Zobrazit možnosti, textový Editor, C/C++

Chcete-li změnit výchozí chování editoru kódu při programování v jazyce C nebo C++, použijte tyto stránky vlastností.

Chcete-li získat přístup k této stránky vlastností, zvolte **nástroje** > **možnosti** a rozbalte **textový Editor**, pak **C/C++** a klikněte na tlačítko **Zobrazení**.

## <a name="code-squiggles"></a>Podtržení vlnovkou kódu

Můžete povolit nebo zakázat následujících nastavení můžete spravovat způsob, jak v textu, který zpracovává editor kódu podtržení vlnovkou pro jazyky C a C++:

- **Makra v oblastech přeskočeno procházení** – definuje, jak zvýrazněte makra, které jsou uvnitř přeskočené oblastí pomocí databáze procházení, jako jsou makra, jejichž definice zahrnují složené závorky.

- **Makra lze převést na constexpr** – definuje, jak zvýrazněte definice maker, které lze převést na `constexpr` definice.

## <a name="inactive-code"></a>Neaktivní kód

- **Zobrazit neaktivní bloky** – neaktivní bloky preprocesoru budou odlišně zbarveny.

- **Zakázat krytí neaktivního kódu** -plnou barvu namísto průhlednosti, se používá pro neaktivní bloky kódu.

- **Míra průhlednosti neaktivního kódu v procentech** – stupeň průhlednosti bloků neaktivního kódu.

## <a name="miscellaneous"></a>Různé

- **Vytvořit výčet úkolů komentáře** – otevřených zdrojových souborech pro tokeny VS a dejte nám o nich v okně seznamu úkolů.

- **Zvýraznit odpovídající tokeny** – zvýraznit uzavírající závorky nebo syntaxi, které odpovídají, kde je umístěn kurzor.

## <a name="outlining"></a>Sbalování

- **Povolit sbalování** -vstoupit do režimu sbalování po otevření souboru.

- **Popisují Pragma region** : automaticky popisují `#pragma` oblasti bloky.

- **Popisují výkazu bloků** – automaticky sbalit bloky příkazů.

## <a name="see-also"></a>Viz také:

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoring v jazyce C++ (VC blogu)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)
