---
title: Možnosti, textový editor, C#, IntelliSense
ms.date: 11/04/2016
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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 87a167a75f3b06522da77d562b0137df89757975
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596213"
---
# <a name="options-text-editor-c-intellisense"></a>Možnosti, textový editor, C#, IntelliSense

Pomocí stránky možností **technologie IntelliSense** můžete upravit nastavení, která ovlivňují chování technologie IntelliSense pro c#. Chcete-li získat přístup k této stránce možností, zvolte**Možnosti** **nástrojů** > a pak zvolte **Text Editor** > **C#** > **IntelliSense**.

Stránka Možností **technologie IntelliSense** obsahuje následující možnosti:

## <a name="completion-lists"></a>Seznamy dokončení

- Zobrazit seznam dokončení po zadání znaku*

   Je-li vybrána tato možnost, technologie IntelliSense automaticky zobrazí seznam dokončení, když začnete psát. Pokud tato možnost není vybrána, je dokončení technologie IntelliSense stále k dispozici v nabídce **IntelliSense** nebo stisknutím **klávesctrl**+**space**.

- Zobrazit seznam dokončení po odstranění znaku

- Zvýraznění odpovídajících částí položek seznamu dokončení

- Zobrazit filtry položek dokončení

## <a name="snippets-behavior"></a>Chování výstřižků

- Nikdy nezahrnovat výstřižky

   Je-li vybrána tato možnost, technologie IntelliSense nikdy nepřidá aliasy pro fragmenty kódu jazyka C# do seznamu dokončení.

- Vždy obsahovat úryvky

   Je-li vybrána tato možnost, intelliSense přidá aliasy pro fragmenty kódu Jazyka C# do seznamu dokončení. V případě, že alias fragmentu kódu je stejný jako klíčové slovo, například [třída](/dotnet/csharp/language-reference/keywords/class), klíčové slovo je nahrazeno zástupcem. Další informace naleznete v [tématu C# Fragmenty kódu](../../ide/visual-csharp-code-snippets.md).

- Zahrnout výstřižky při zadání karty ?-Tab za identifikátorem

   Je-li vybrána tato možnost, přidá technologie IntelliSense aliasy pro fragmenty kódu jazyka C# do seznamu dokončení, kdy **?** + **Karta** je stisknuta za identifikátorem

## <a name="enter-key-behavior"></a>Zadat chování klíče

- Nikdy nepřidávat nový řádek při vstupu

   Určuje, že nový řádek se nikdy nepřidá automaticky po výběru položky v seznamu dokončení a stisknutí klávesy **Enter**.

- Pouze přidat nový řádek na enter po ukončení plně zadaný word

   Určuje, že pokud zadáte všechny znaky pro položku do seznamu dokončení a pak stisknete **Enter**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

   Pokud například zadáte `else` a pak stisknete **Enter**, v editoru se zobrazí následující:

   `else`

   `|`(umístění kurzoru)

   Pokud však zadáte `el` pouze a pak stisknete **Enter**, v editoru se zobrazí následující:

   `else|`(umístění kurzoru)

- Vždy přidat nový řádek při vstupu

   Určuje, že pokud do seznamu dokončení zadáte *některý* ze znaků položky a pak stisknete **Enter**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

## <a name="show-name-suggestions"></a>Zobrazit návrhy jmen

Provádí automatické dokončování názvů objektů pro členy, které jste nedávno vybrali.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
