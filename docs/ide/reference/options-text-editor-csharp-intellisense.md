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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596213"
---
# <a name="options-text-editor-c-intellisense"></a>Možnosti, textový editor, C#, IntelliSense

Stránka možnosti **technologie IntelliSense** slouží k úpravě nastavení, která mají vliv na chování technologie C#IntelliSense pro. Chcete-li získat přístup k této stránce Možnosti, zvolte **nástroje** > **Možnosti**a pak zvolte **C#** **textový editor** >  > **IntelliSense**.

Stránka možnosti **technologie IntelliSense** obsahuje následující možnosti:

## <a name="completion-lists"></a>Seznamy dokončení

- Zobrazit seznam dokončení po zadání znaku *

   Když je vybraná tato možnost, IntelliSense po zahájení psaní automaticky zobrazí seznam dokončení. Pokud tato možnost není vybrána, bude dokončování technologie IntelliSense stále k dispozici v nabídce **technologie IntelliSense** nebo stisknutí klávesy **CTRL**+**MEZERNÍK**.

- Po odstranění znaku zobrazit seznam dokončení

- Zvýraznit vyhovující části položek seznamu dokončení

- Zobrazit filtry položek dokončení

## <a name="snippets-behavior"></a>Chování fragmentů kódu

- Nikdy Nezahrnovat fragmenty

   Je-li vybrána tato možnost, technologie IntelliSense nikdy nepřidá aliasy pro C# fragmenty kódu do seznamu dokončení.

- Vždy zahrnout fragmenty kódu

   Pokud je vybrána tato možnost, technologie IntelliSense přidá aliasy pro C# fragmenty kódu do seznamu dokončení. V případě, že je alias fragmentu kódu stejný jako klíčové slovo, například [Třída](/dotnet/csharp/language-reference/keywords/class), klíčové slovo je nahrazeno zástupcem. Další informace naleznete v tématu [ C# fragmenty kódu](../../ide/visual-csharp-code-snippets.md).

- Zahrnout fragmenty kódu při zadání?-Tab po identifikátoru

   Pokud je vybrána tato možnost, technologie IntelliSense přidá aliasy pro C# fragmenty kódu do seznamu dokončení při stisknutí klávesy TAB na **kartě** **?** +po identifikátoru.

## <a name="enter-key-behavior"></a>Chování klávesy ENTER

- Nikdy Nepřidávat nový řádek při zadání

   Určuje, že se nový řádek nikdy nepřidá automaticky po výběru položky v seznamu pro dokončení a stisknutím klávesy **ENTER**.

- Přidat nový řádek při stisknutí ENTER po konci plně zadaného slova

   Určuje, že pokud zadáte všechny znaky pro položku v seznamu pro doplňování a potom stisknete klávesu **ENTER**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

   Pokud například zadáte `else` a potom stisknete klávesu **ENTER**, zobrazí se v editoru následující:

   `else`

   `|` (umístění kurzoru)

   Pokud však zadáte pouze `el` a stisknete klávesu **ENTER**, zobrazí se v editoru následující:

   `else|` (umístění kurzoru)

- Vždy přidat nový řádek při zadání

   Určuje, že pokud zadáte *některý* ze znaků pro položku v seznamu pro doplňování a stisknete klávesu **ENTER**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

## <a name="show-name-suggestions"></a>Zobrazit návrhy názvů

Provede automatické dokončování názvů objektů pro členy, které jste naposledy vybrali.

## <a name="see-also"></a>Viz také:

- [Obecné, Prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Používání atributu IntelliSense](../../ide/using-intellisense.md)
