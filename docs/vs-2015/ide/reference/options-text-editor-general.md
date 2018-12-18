---
title: Možnosti, textový Editor, obecné | Dokumentace Microsoftu
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
- VS.TOOLSOPTIONSPAGES.TEXT_EDITOR.SQL_SERVER_TOOLS.GENERAL
- VS.ToolsOptionsPages.Text_Editor.All_Languages.General
- VS.ToolsOptionsPages.Text_Editor.RDL_Expression.General
- VS.ToolsOptionsPages.Text_Editor.SQL.General
- vs.toolsoptionspages.text_editor
- VS.ToolsOptionsPages.Text_Editor.XML.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL80.General
- VS.ToolsOptionsPages.Text_Editor.CSS
- VS.ToolsOptionsPages.Text_Editor.Plain_Text.General
- VS.ToolsOptionsPages.Text_Editor.Visual_JSharp.General
- VS.ToolsOptionsPages.Text_Editor.SQL_Script.General
- VS.ToolsOptionsPages.Text_Editor.CSharp.General
- VS.ToolsOptionsPages.Text_Editor.All_Languages
- VS.ToolsOptionsPages.Text_Editor.T-SQL7.General
- VS.ToolsOptionsPages.Text_Editor.Basic.General
- VS.ToolsOptionsPages.Text_Editor.T-SQL.General
- vs.toolsoptionspages.text_editor.visual_jsharp
- VS.ToolsOptionsPages.Text_Editor.F#.Tabs
- VS.ToolsOptionsPages.Text_Editor.F#
- VS.ToolsOptionsPages.Text_Editor.PL/SQL.General
- VS.ToolsOptionsPages.Text_Editor.C/C++.General
- VS.ToolsOptionsPages.Text_Editor.Plain_Text
- VS.ToolsOptionsPages.Text_Editor.HTML
- VS.ToolsOptionsPages.Text_Editor.XAML.General
- VS.ToolsOptionsPages.Text_Editor
- VS.ToolsOptionsPages.Text_Editor.F#.General
- VS.ToolsOptionsPages.Text_Editor.XOML.General
- VS.ToolsOptionsPages.Text_Editor.SQL
- vs.toolsoptionspages.text_editor.c/c++
- VS.ToolsOptionsPages.Text_Editor.SQL_Script
- VS.ToolsOptionsPages.Text_Editor.T-SQL90.General
- VS.ToolsOptionsPages.Text_Editor.General
- VS.ToolsOptionsPages.Text_Editor.CSharp
helpviewer_keywords:
- Text Editor Options dialog box
- Code Editor
- Text Editor [Visual Studio]
- editors, global settings
ms.assetid: 4ac21e48-3243-4141-9058-7eaf12b3cde7
caps.latest.revision: 34
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 47fb93aebeecf50ae20616fc47033be60724cd45
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49257826"
---
# <a name="options-text-editor-general"></a>Možnosti, textový editor, obecné
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Toto dialogové okno umožňuje měnit globální nastavení pro [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] kódu a textovém editoru. Chcete-li zobrazit toto dialogové okno, klikněte na tlačítko **možnosti** na **nástroje** nabídky, rozbalte **textový Editor** složku a pak klikněte na tlačítko **Obecné**.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="settings"></a>Nastavení  
 Přetáhnout myší úpravy textu  
 Při výběru, umožňuje přesunout text jeho výběrem a přetažením myší do jiného umístění v rámci aktuálního dokumentu nebo libovolného otevřeného dokumentu.  
  
 Automatické zvýrazňování oddělovače  
 Pokud je vybráno, jsou zvýrazněny znaky oddělovače, které oddělují parametry nebo párů hodnot položky, jakož i odpovídající složené závorky.  
  
 Sledování změn  
 Pokud je vybrána editoru kódu, se zobrazí v okraj výběru označit kód, který se změnil, protože soubor byl uložen jako poslední svislé Žlutá čára. Při ukládání změn budou zelené svislé čáry.  
  
 Automatické rozpoznání kódování UTF-8 bez podpisu  
 Ve výchozím nastavení zjistí editoru kódování tak, že značky pořadí bajtů nebo znaková sada značky. Pokud ani nenajde v aktuálním dokumentu, editoru kódu se pokusí automaticky rozpoznat kódování UTF-8 naskenováním pořadí bajtů. Chcete-li zakázat automatické zjišťování kódování, zrušte zaškrtnutí tohoto políčka.  
  
## <a name="display"></a>Displej  
 Okraj výběru  
 Pokud je vybráno, zobrazí svislý okraj podél levého okraje editoru textová oblast. Můžete kliknout na tento okraj označit celý řádek textu, nebo klikněte a tažením vyberte po sobě jdoucích řádků textu.  
  
|Okraj výběru|Okraj výběru vypnuto|  
|-------------------------|--------------------------|  
|![HTMLpageSelectionMarginOn screenshot](../../ide/reference/media/vxselmaron.gif "vxSelmaron")|![Snímek obrazovky HTMLpageSelectionMarginOff](../../ide/reference/media/vxselmaroff.gif "vxSelmaroff")|  
  
 Okraj indikátoru  
 Pokud je vybráno, zobrazí svislý okraj mimo levého okraje editoru textová oblast. Po kliknutí na toto rozpětí, zobrazí ikonu a popis, který se vztahují na text. Zarážky nebo úloha klávesové zkratky seznamu se zobrazí v okraj indikátoru. Informace o okraj indikátoru nevytiskne.  
  
 Svislý posuvník.  
 Pokud je vybráno, zobrazí svislý posuvník, který umožňuje nahoru a dolů k zobrazení elementy, které spadají mimo oblast zobrazení editoru. Pokud svislé posuvníky nejsou k dispozici, můžete Page Up, Page Down a klíče kurzor posouvat.  
  
 Vodorovný posuvník  
 Pokud je vybráno, zobrazí vodorovný posuvník, který umožňuje ze strany na stranu přejděte do zobrazení elementy, které spadají mimo oblast zobrazení editoru. Pokud vodorovné posuvníky nedostupné, můžete přejít kurzor klíče.  
  
 Zvýraznit aktuální řádek  
 Pokud je vybráno, zobrazí šedé okolo řádek kódu, ve kterém se nachází kurzor.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti, textový Editor, všechny jazyky](../../ide/reference/options-text-editor-all-languages.md)   
 [Možnosti, textový Editor, všechny jazyky, karty](../../ide/reference/options-text-editor-all-languages-tabs.md)   
 [Možnosti, textový Editor, přípona souboru](../../ide/reference/options-text-editor-file-extension.md)   
 [Identifikování a přizpůsobení klávesových zkratek](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md)   
 [Vlastní nastavení editoru](../../ide/customizing-the-editor.md)   
 [Používání atributu IntelliSense](../../ide/using-intellisense.md)



