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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "75596213"
---
# <a name="options-text-editor-c-intellisense"></a>Možnosti, textový editor, C#, IntelliSense

Stránka možnosti **technologie IntelliSense** slouží k úpravě nastavení, která mají vliv na chování technologie IntelliSense v jazyce C#. Chcete-li získat přístup k této **Tools**stránce Možnosti, zvolte  >  **možnost**nástroje a pak zvolte **textový editor**  >  **C#**  >  **IntelliSense**.

Stránka možnosti **technologie IntelliSense** obsahuje následující možnosti:

## <a name="completion-lists"></a>Seznamy dokončení

- Zobrazit seznam dokončení po zadání znaku *

   Když je vybraná tato možnost, IntelliSense po zahájení psaní automaticky zobrazí seznam dokončení. Pokud tato možnost není vybrána, je dokončení technologie IntelliSense stále k dispozici v nabídce **technologie IntelliSense** nebo stisknutí klávesy **CTRL** + **Space**.

- Po odstranění znaku zobrazit seznam dokončení

- Zvýraznit vyhovující části položek seznamu dokončení

- Zobrazit filtry položek dokončení

## <a name="snippets-behavior"></a>Chování fragmentů kódu

- Nikdy Nezahrnovat fragmenty

   Je-li vybrána tato možnost, technologie IntelliSense nikdy nepřidá aliasy pro fragmenty kódu jazyka C# do seznamu dokončení.

- Vždy zahrnout fragmenty kódu

   Je-li vybrána tato možnost, technologie IntelliSense přidá do seznamu dokončení aliasy pro fragmenty kódu jazyka C#. V případě, že je alias fragmentu kódu stejný jako klíčové slovo, například [Třída](/dotnet/csharp/language-reference/keywords/class), klíčové slovo je nahrazeno zástupcem. Další informace naleznete v tématu [fragmenty kódu jazyka C#](../../ide/visual-csharp-code-snippets.md).

- Zahrnout fragmenty kódu při zadání?-Tab po identifikátoru

   Pokud je vybrána tato možnost, technologie IntelliSense přidá aliasy pro fragmenty kódu jazyka C# do seznamu dokončení, pokud **?** + Stisknutí klávesy **TAB** po identifikátoru

## <a name="enter-key-behavior"></a>Chování klávesy ENTER

- Nikdy Nepřidávat nový řádek při zadání

   Určuje, že se nový řádek nikdy nepřidá automaticky po výběru položky v seznamu pro dokončení a stisknutím klávesy **ENTER**.

- Přidat nový řádek při stisknutí ENTER po konci plně zadaného slova

   Určuje, že pokud zadáte všechny znaky pro položku v seznamu pro doplňování a potom stisknete klávesu **ENTER**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

   Pokud například zadáte `else` a stisknete klávesu **ENTER**, zobrazí se v editoru následující:

   `else`

   `|` (umístění kurzoru)

   Pokud však zadáte pouze příkaz `el` a stisknete klávesu **ENTER**, zobrazí se v editoru následující:

   `else|` (umístění kurzoru)

- Vždy přidat nový řádek při zadání

   Určuje, že pokud zadáte *některý* ze znaků pro položku v seznamu pro doplňování a stisknete klávesu **ENTER**, automaticky se přidá nový řádek a kurzor se přesune na nový řádek.

## <a name="show-name-suggestions"></a>Zobrazit návrhy názvů

Provede automatické dokončování názvů objektů pro členy, které jste naposledy vybrali.

## <a name="see-also"></a>Viz také

- [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
- [Pomocí technologie IntelliSense](../../ide/using-intellisense.md)
