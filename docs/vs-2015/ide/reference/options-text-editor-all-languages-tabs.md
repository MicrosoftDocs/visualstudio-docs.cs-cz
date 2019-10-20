---
title: Možnosti, textový editor, všechny jazyky, karty | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.ResJSON.Tabs
- VS.ToolsOptionsPages.Text_Editor.JavaScript.Tabs
- VS.ToolsOptionsPages.Text_Editor.All_Languages.Tabs
helpviewer_keywords:
- indents, Code Editor
- Code Editor, default behavior
- tabs, setting in Code Editor
- All Languages Text Editor Options dialog box
- editors, Code Editor
- Code Editor, indenting
- Code Editor, tabs
ms.assetid: 7e208e1d-5e3a-4bf7-a27b-4417e3e049c7
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4cb670ab52e321f15c5b009c66ca40623409f10a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662387"
---
# <a name="options-text-editor-all-languages-tabs"></a>Možnosti, textový editor, všechny jazyky, karty
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Toto dialogové okno umožňuje změnit výchozí chování editoru kódu. Tato nastavení platí také pro ostatní editory na základě editoru kódu, jako je například zobrazení zdroje v Návrháři HTML. Chcete-li zobrazit tyto možnosti, vyberte **Možnosti** v nabídce **nástroje** . V rámci složky **textový editor** rozbalte podsložku **všechny jazyky** a pak zvolte **karty**.

> [!CAUTION]
> Tato stránka nastaví výchozí možnosti pro všechny vývojové jazyky. Mějte na paměti, že při resetování možnosti v tomto dialogu dojde k výběru možností karet ve všech jazycích, ať už jsou vybrané volby. Chcete-li změnit možnosti textového editoru pouze pro jeden jazyk, rozbalte podsložku pro daný jazyk a vyberte její stránky možností.

 Pokud jsou na stránkách možností karet pro konkrétní programovací jazyky vybraná jiná nastavení, zobrazí se u různých možností **odsazení** zpráva nastavení odsazení pro jednotlivé textové formáty. a zpráva "nastavení tabulátoru pro jednotlivé textové formáty jsou v konfliktu." se zobrazí pro různé možnosti **tabulátoru** . Toto připomenutí se zobrazí například v případě, že je vybraná možnost **inteligentního odsazení** pro Visual Basic, ale pro vizuál C++se vybere **odsazení bloku** .

> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="indenting"></a>Odsazení
 Žádné, pokud je tato možnost vybrána, nové řádky nebudou odsazeny. Místo vložení se umístí do prvního sloupce nového řádku.

 Zablokovat, je-li vybrána tato možnost, jsou nové řádky automaticky odsazeny. Bod vložení se umístí na stejný výchozí bod jako předchozí řádek.

 Inteligentní – když je vybraná, nové řádky se umístí tak, aby odpovídaly kontextu kódu, pro další nastavení formátování kódu a konvence IntelliSense pro vývojový jazyk. Tato možnost není k dispozici pro všechny vývojové jazyky.

 Například řádky uzavřené mezi levou složenou závorkou ({) a pravou složenou závorkou (}) mohou být automaticky odsazeny o další zarážku tabulátoru z pozice zarovnaných složených závorek.

## <a name="tabs"></a>Karty
 Tab Size nastaví vzdálenost mezi zarážkami tabulátoru v mezerách. Výchozí hodnota je čtyři mezery.

 Odsazení velikosti nastaví velikost v mezerách automatického odsazení. Výchozí hodnota je čtyři mezery. Pro vyplnění zadané velikosti budou vloženy znaky tabulátoru, znaky mezery nebo obojí.

 Vložit mezery po výběru a odsadit operace vloží pouze mezery, nikoli znaky TABULÁTORu. Pokud je **Velikost odsazení** nastavená na 5, například, pak se při každém stisknutí klávesy TAB nebo **zvětšení odsazení** na panelu nástrojů **formátování** vloží pět znaků mezer.

 Ponechte záložky v případě, že jsou vybrané, operace odsazení vloží tolik znaků TABULÁTORu, kolik jich je možné. Každý znak TABULÁTORu vyplní počet mezer zadaný v poli **velikost tabulátoru**. Pokud **Velikost odsazení** není sudým násobkem **velikosti tabulátoru**, přidají se k vyplnění rozdílu znaky mezer.

## <a name="see-also"></a>Viz také
 [Možnosti, textový editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md) [Obecné, prostředí, dialogové okno Možnosti](../../ide/reference/general-environment-options-dialog-box.md)
