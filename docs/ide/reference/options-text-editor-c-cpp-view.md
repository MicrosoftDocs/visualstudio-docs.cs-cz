---
title: Možnosti, textový editor, C/C++, zobrazení
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.View
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.View
- VS.ToolsOptionsPages.Text_Editor.C\C++.View
author: corob-msft
ms.author: corob
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: 95963245b15828f374e9812a9bb09d015b21a94b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278691"
---
# <a name="options-text-editor-cc-view"></a>Možnosti, textový editor, C/C++, zobrazení

Pomocí těchto stránek vlastností můžete změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.

Chcete-li získat přístup k této **Tools**stránce vlastností, zvolte  >  **Možnosti** nástroje, rozbalte **Text Editor**, pak **C/C++** a pak zvolte možnost **Zobrazit**.

## <a name="code-squiggles"></a>Vlnovky kódu

Můžete povolit nebo zakázat následující nastavení pro správu způsobu, jakým textový editor zpracovává vlnovky kódu pro jazyky C a C++:

- **Makra v vynechaných oblastech procházení** – definuje, jak zvýraznit makra, která jsou uvnitř vynechaných oblastí v databázi procházení, například makra, jejichž definice obsahují složené závorky.

- **Makra převoditelná na constexpr** – definuje, jak zvýraznit definice maker, které je možné převést na `constexpr` definice.

## <a name="inactive-code"></a>Neaktivní kód

- **Zobrazit neaktivní bloky** – neaktivní bloky preprocesoru jsou barevně odlišné.

- **Zakázat krytí neaktivního kódu** – plná barva namísto neprůhlednosti se používá pro neaktivní bloky kódu.

- **Neaktivní neprůhlednost kódu** – procento neprůhlednosti pro neaktivní bloky kódu.

## <a name="miscellaneous"></a>Různé

- Zobrazení **výčtu úkolů s komentářem** – vyhledá v otevřených zdrojových souborech tokeny vs a nahlásí je v okně seznam úkolů.

- **Zvýraznit odpovídající tokeny** – zvýrazněte uzavírací závorky nebo syntaxi, které odpovídají místu, kde je kurzor umístěný.

## <a name="outlining"></a>Sbalování

- **Povolit sbalení** – po otevření souboru zadejte režim sbalení.

- **Vytvoření osnovy oblastí pragma** – automatické `#pragma` bloky osnovy oblasti

- **Bloky příkazů osnovy** – automatické bloky příkazů osnovy.

## <a name="see-also"></a>Viz také

- [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)
- [Refaktoring v C++ (blog VC)](https://devblogs.microsoft.com/cppblog/all-about-c-refactoring-in-visual-studio-2015-preview/)
