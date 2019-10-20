---
title: Možnosti, textový editor, C#IntelliSense | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Intellisense
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.Intellisense
helpviewer_keywords:
- IntelliSense [J#], options
- underlines, wavy
- IntelliSense [C#], options
- IntelliSense [C#], wavy underlines
- wavy underlines
- Text Editor Options dialog box, IntelliSense
ms.assetid: 3466dedb-e5f4-424c-8dd8-e4941b2f4fc2
caps.latest.revision: 30
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e3f4df9a7a885245e40f7e9fec1b0da207ada39
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662301"
---
# <a name="options-text-editor-c-intellisense"></a>Možnosti, textový editor, C#, IntelliSense
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Stránka vlastností **technologie IntelliSense** slouží k úpravě nastavení, která mají vliv na chování technologie IntelliSense C#pro vizuál. Na stránku vlastností **technologie IntelliSense** se dostanete tak, že v nabídce **nástroje** kliknete **C#** na **Možnosti** a potom kliknete do složky **textový editor** a kliknete na **IntelliSense.**

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Stránka vlastností **technologie IntelliSense** obsahuje následující vlastnosti:

## <a name="completion-lists"></a>Seznamy dokončení
 **Po zadání znaku zobrazit seznam dokončení** Když je vybraná tato možnost, IntelliSense po zahájení psaní automaticky zobrazí seznam dokončení. Pokud tato možnost není vybrána, je dokončení technologie IntelliSense stále k dispozici v nabídce **technologie IntelliSense** nebo stisknutí kombinace kláves CTRL + MEZERNÍK.

 **Umístit klíčová slova do seznamů dokončení** Je-li vybrána tato možnost, technologie C# IntelliSense přidá klíčová slova, například [Třída](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), do seznamu dokončení.

 **Umístit fragmenty kódu do seznamů dokončení** Pokud je vybrána tato možnost, technologie IntelliSense přidá aliasy pro C# fragmenty kódu do seznamu dokončení. V případě, že je alias fragmentu kódu stejný jako klíčové slovo, například [Třída](https://msdn.microsoft.com/library/b95d8815-de18-4c3f-a8cc-a0a53bdf8690), klíčové slovo je nahrazeno zástupcem. Další informace naleznete v tématu [vizuální C# fragmenty kódu](../../ide/visual-csharp-code-snippets.md).

## <a name="selection-in-completion-lists"></a>Výběr v seznamech dokončení
 **Potvrzeno zadáním následujících znaků:** Určuje všechny znaky, které spouštějí automatické dokončování technologie IntelliSense pro vybranou položku v seznamu dokončení po jejich zadání.

 **Potvrzené stisknutím mezerníku** Určuje, že se má při automatickém dokončování vybrané položky v seznamu pro doplňování použít akce stisknutí mezerníku.

 **Přidat nový řádek při zadání na konci plně zadaného slova** Určuje, že pokud zadáte všechny znaky pro položku v seznamu pro doplňování a stisknete ENTER, vytvoří se nový řádek automaticky a kurzor se přesune na nový řádek.

 Pokud například zadáte `else` a potom stisknete klávesu ENTER, zobrazí se v editoru následující:

 `else`

 `|` (umístění kurzoru)

 Pokud však zadáte pouze `el` a stisknete klávesu ENTER, zobrazí se v editoru následující:

 `else|` (umístění kurzoru)

## <a name="intellisense-member-selection"></a>Výběr členů IntelliSense
 **Předem vybere naposledy použité členy** . Je-li vybrána tato možnost, technologie IntelliSense předem vybere členy, které jste v poslední době vybrali v rozevíracím seznamu Členové okna pro automatické dokončování názvů objektů, během aktuální relace v integrovaném vývojovém prostředí (IDE). Historie naposledy použitých členů je mezi jednotlivými relacemi v integrovaném vývojovém prostředí vymazána. Další informace najdete v tématu [IntelliSense pro naposledy použité členy](../../misc/intellisense-for-most-recently-used-members.md).

## <a name="see-also"></a>Viz také
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md) [dokumentace k dokumentaci XML](https://msdn.microsoft.com/library/803b7f7b-7428-4725-b5db-9a6cff273199) [pomocí technologie IntelliSense](../../ide/using-intellisense.md)
