---
title: Možnosti, textový editor, C-C++, formátování | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ad06dfb32c301985eb4976f6c89c7be1e0e68da
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662332"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Umožňuje změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.

 Chcete-li získat přístup k této stránce, v dialogovém okně **Možnosti** rozbalte v levém podokně položku **textový editor**, rozbalte položku **C++C/** a klikněte na možnost **formátování**.

> [!NOTE]
> Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="cc-options"></a>Možnost jazyka C/C++
 **Povolit automatické rychlé popisy informací** Povolí nebo zakáže funkci rychlé informace technologie IntelliSense.

## <a name="inactive-code"></a>Neaktivní kód
 **Zobrazit neaktivní bloky kódu** Kód, který je neaktivní z důvodu deklarace `#ifdef`, jsou barevně odlišné, což vám usnadní jeho identifikaci.

 **Zakázat krytí neaktivního kódu** Neaktivní kód lze identifikovat pomocí barvy místo transparentnosti.

 **Neprůhlednost neaktivního kódu v procentech** Stupeň neprůhlednosti pro neaktivní bloky kódu je možné přizpůsobit.

## <a name="indentation"></a>Odsazení
 **Odsadit složené závorky** Můžete nakonfigurovat, jak se mají zarovnat složené závorky po stisknutí klávesy ENTER po zahájení bloku kódu, například funkce nebo smyčky `for`. Složené závorky mohou být buď zarovnány k prvnímu znaku bloku kódu, nebo odsazeny.

 **Automatické odsazení na kartě** Můžete nakonfigurovat, co se stane s aktuálním řádkem kódu při stisknutí klávesy TAB. Buď se odsadí řádek, nebo se vloží tabulátor.

## <a name="miscellaneous"></a>Různé
 Zobrazení **výčtu komentářů v okně seznam úkolů** Editor může vyhledat v komentářích otevřené zdrojové soubory pro přednastavená slova. Vytvoří položku v okně **seznam úkolů** pro všechna klíčová slova, která najde.

 **Zvýraznit tokeny** , které odpovídají Když je kurzor vedle složené závorky, může editor zvýraznit odpovídající závorku, aby bylo možné snadněji vidět obsažený kód.

## <a name="outlining"></a>Sbalování
 **Po otevření souborů přejít do režimu sbalení** Když do textového editoru přivedete soubor, můžete povolit funkci sbalení. Další informace najdete v tématu [popisujícím sbalení](../../ide/outlining.md). Při výběru této možnosti se funkce sbalování povolí při otevření souboru.

 **Automatické sbalení bloků #pragma oblasti** Je-li vybrána tato možnost, je povoleno automatické sbalení pro [direktivy pragma](https://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) . V režimu sbalování tak můžete rozbalit nebo sbalit bloky pragma region.

 **Automatické sbalení bloků příkazů** Pokud je vybrána tato možnost, je pro následující konstrukce příkazu povoleno automatické sbalení:

- [if-else](https://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)

- [switch – příkaz (C++)](https://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)

- [while – příkaz (C++)](https://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)

## <a name="see-also"></a>Viz také
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md) [pomocí technologie IntelliSense](../../ide/using-intellisense.md)
