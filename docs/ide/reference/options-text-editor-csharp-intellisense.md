---
title: Možnosti, textový editor, C#, IntelliSense
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
helpviewer_keywords:
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 041b3c5d0a67d590bc409c21dd53d5d162b0a0b9
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52389254"
---
# <a name="options-text-editor-c-intellisense"></a>Možnosti, textový editor, C#, IntelliSense

Použití **IntelliSense** možnosti stránky pro úpravu nastavení, která ovlivňují chování technologie IntelliSense pro C#. Chcete-li získat přístup k této stránce Možnosti, zvolte **nástroje** > **možnosti**a klikněte na tlačítko **textový Editor**  >  **C#**  >  **IntelliSense**.

**IntelliSense** stránka možností obsahuje následující možnosti:

## <a name="completion-lists"></a>Seznamy dokončení

- Zobrazit seznam dokončení po zadání znaku *

   Pokud je vybraná tato možnost, IntelliSense zobrazí seznam pro doplňování automaticky při zadávání. Pokud není vybraná tato možnost, je stále k dispozici z dokončování IntelliSense **IntelliSense** nabídky nebo stisknutím klávesy **Ctrl**+**místo**.

- Zobrazit seznam dokončení po odstranění znaku

- Zvýraznit odpovídající části položek seznamu dokončení

- Zobrazovat filtry položek dokončení

## <a name="snippets-behavior"></a>Chování fragmentů

- Nikdy Nezahrnovat fragmenty

   Pokud je vybraná tato možnost, technologie IntelliSense nikdy Přidá aliasy pro C# fragmenty do seznamu dokončení kódu.

- Vždy zahrnovat fragmenty

   Pokud je vybraná tato možnost, technologie IntelliSense přidá do seznamu dokončení aliasy pro fragmenty kódu v C#. V případě, kdy alias fragment kódu je stejný jako klíčové slovo, například [třída](/dotnet/csharp/language-reference/keywords/class), klíčové slovo je nahrazena klávesovou zkratku. Další informace najdete v tématu [ C# fragmenty kódu](../../ide/visual-csharp-code-snippets.md).

- Zahrnovat fragmenty po?-je zadaný Tabulátor za identifikátor

   Pokud je vybraná tato možnost, technologie IntelliSense Přidá aliasy pro C# fragmenty kódu pro dokončení seznamu při **?** + **Kartu** stisknutí za identifikátor

## <a name="enter-key-behavior"></a>Chování klávesy ENTER

- Nikdy přidat nový řádek enter

   Určuje, že nový řádek nikdy přidán automaticky po výběru nějaké položky v seznamu dokončení a stisknutím klávesy **Enter**.

- Přidat nový řádek jenom enter po konci úplně napsaného slova

   Určuje, že pokud zadání všech znaků pro položku v seznamu dokončení a potom stiskněte klávesu **Enter**, se automaticky přidá nový řádek a kurzor se přesune na nový řádek.

   Pokud zadáte například `else` a potom stiskněte klávesu **Enter**, v editoru se zobrazí následující:

   `else`

   `|` (umístění kurzoru)

   Nicméně pokud zadáte pouze `el` a potom stiskněte klávesu **Enter**, v editoru se zobrazí následující:

   `else|` (umístění kurzoru)

- Vždy přidat nový řádek enter

   Určuje, že pokud zadáte *jakékoli* znaků pro položku v seznamu dokončení a poté stiskněte klávesu **Enter**, se automaticky přidá nový řádek a kurzor se přesune na nový řádek.

## <a name="show-name-suggestions"></a>Zobrazit název návrhy

Automatický objekt název dokončení provádí pro členy, které jste nedávno vybrali.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)