---
title: Možnosti, textový Editor, C / C++, formátování | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Formatting.General
- VS.ToolsOptionsPages.Text_Editor.C%2fC%2b%2b.Formatting.General
dev_langs:
- C++
helpviewer_keywords:
- Text Editor Options dialog box, formatting
ms.assetid: cb6f1cbb-5305-48da-a8e8-33fd70775d46
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a8589696e669c83b65951d81d155033d45533710
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49237000"
---
# <a name="options-text-editor-cc-formatting"></a>Možnosti, textový editor, C/C++, formátování
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Umožňuje změnit výchozí chování editoru kódu při programování v jazyce C nebo C++.  
  
 Pro přístup k této stránce v **možnosti** dialogové okno, v levém podokně rozbalte **textový Editor**, rozbalte **C/C++** a potom klikněte na tlačítko **formátování** .  
  
> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="cc-options"></a>Možnost jazyka C/C++  
 **Povolit automatické popisky rychlé informace**  
 Povolí nebo zakáže funkci Rychlé informace technologie IntelliSense.  
  
## <a name="inactive-code"></a>Neaktivní kód  
 **Zobrazit bloky neaktivního kódu**  
 Kód, který je neaktivní kvůli `#ifdef` deklarace jsou pro vám pomůže ho rozpoznat odlišně zbarveny.  
  
 **Zakázat krytí neaktivního kódu**  
 Neaktivní kód lze poznat pomocí barvy místo průhlednosti.  
  
 **Míra průhlednosti neaktivního kódu v procentech**  
 Stupeň průhlednosti bloků neaktivního kódu lze přizpůsobit.  
  
## <a name="indentation"></a>Odsazení  
 **Odsadit složené závorky**  
 Můžete nakonfigurovat, jak mají zarovnávat složené závorky po stisknutí klávesy ENTER po zahájení bloku kódu, například funkce nebo `for` smyčky. Složené závorky mohou být buď zarovnány k prvnímu znaku bloku kódu, nebo odsazeny.  
  
 **Automaticky odsazovat při tabulátoru**  
 Můžete nastavit, co se stane s aktuálním řádkem kódu po stisknutí klávesy TAB. Buď se odsadí řádek, nebo se vloží tabulátor.  
  
## <a name="miscellaneous"></a>Různé  
 **Zobrazit komentáře v okně Seznam úloh**  
 Editor může v otevřených zdrojových souborech vyhledat přednastavená slova v komentářích. Vytvoří záznam v **seznamu úkolů** okno pro jakékoli nalezené.  
  
 **Zvýraznit odpovídající tokeny**  
 Když je kurzor vedle složené závorky, může editor zvýraznit protější složenou závorku, abyste snadněji viděli obsažený kód.  
  
## <a name="outlining"></a>Sbalování  
 **Po otevření souborů vstoupit do režimu sbalování**  
 Když v textovém editoru otevřete soubor, můžete povolit funkci sbalování. Další informace najdete v tématu [Osnova](../../ide/outlining.md). Při výběru této možnosti se funkce sbalování povolí při otevření souboru.  
  
 **Automatické sbalení bloků #pragma region**  
 Pokud je tato možnost automatické sbalování pro [direktivy pragma](http://msdn.microsoft.com/library/9867b438-ac64-4e10-973f-c3955209873f) je povolená. V režimu sbalování tak můžete rozbalit nebo sbalit bloky pragma region.  
  
 **Automatické sbalování bloků příkazu**  
 Při výběru této možnosti je povoleno automatické sbalování následujících příkazových konstrukcí:  
  
-   [if-else](http://msdn.microsoft.com/library/d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2)  
  
-   [switch – příkaz (C++)](http://msdn.microsoft.com/library/6c3f3ed3-5593-463c-8f4b-b33742b455c6)  
  
-   [while – příkaz (C++)](http://msdn.microsoft.com/library/358dbe76-5e5e-4af5-b575-c2293c636899)  
  
## <a name="see-also"></a>Viz také  
 [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)   
 [Používání atributu IntelliSense](../../ide/using-intellisense.md)



