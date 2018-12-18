---
title: Možnosti, textový Editor, C / C++, experimentální | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.C/C++.Experimental
- VS.ToolsOptionsPages.Text_Editor.C%2FC%2B%2B.Experimental
- VS.ToolsOptionsPages.Text_Editor.C\C++.Experimental
ms.assetid: b9e9dda2-350c-460d-b368-37d6c5342eee
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: aae8681bf9db0998c1d86ad00112d3228a76081d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49814412"
---
# <a name="options-text-editor-cc-experimental"></a>Možnosti, textový Editor, C/C++, experimentální
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Změnou tyto možnosti můžete změnit chování související se technologie IntelliSense a procházení databází, když programujete v jazyce C nebo C++.  
  
 Pro přístup k této stránce v **možnosti** dialogové okno, v levém podokně rozbalte **textový Editor**, rozbalte **C/C++** a klikněte na tlačítko **experimentální**.  
  
 Tyto funkce jsou dostupné v instalaci sady Visual Studio 2015 Update 1 RC.  
  
> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Zobrazit [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="browsingnavigation"></a>Procházení a navigace  
 **Zapnout nový databázový stroj**  
 Tím by měl automaticky urychlí naplnění databáze a urychlit všechny databázové operace (s bez ztráty přesnosti) pro operace, jako **přejít k definici** a **najít všechny odkazy**. (Pouze zavřete a znovu otevřete řešení, aby se změny projevily, není nutné restartovat Visual Studio)  
  
## <a name="intellisense"></a>IntelliSense  
 **Člen seznamu tečky na šipku**  
 Nahradí "." znaky->' Pokud se dá použít pro seznam členů.  
  
## <a name="refactoring"></a>Refaktoring  
 **Povolit extrakci funkce**  
 Extrahovat vybraný kód ke svojí funkci a nahraďte kód pomocí volání na tuto novou funkci. Chcete-li použít tuto funkci, klikněte pravým tlačítkem na vybraný kód a vyberte **rychlé akce**, nebo jednoduše stisknout klávesovou zkratku Ctrl + tečka [Ctrl +.] výchozí.  
  
 **Povolit změnit signaturu**  
 Přidat, změnit pořadí a odstranit parametrů funkce a šíří změny do všech lokalit volání. Přístup k této funkci, klikněte pravým tlačítkem na veškeré využití nad funkce a vyberte **rychlé akce**, nebo jednoduše stisknout klávesovou zkratku Ctrl + tečka [Ctrl +.] výchozí.  
  
## <a name="text-editor"></a>Textový editor  
 **Povolit rozbalení oborů**  
 Pokud je povoleno, je možné ohraničit vybraný text pomocí složených závorek zadáním "{" v textovém editoru.  
  
 **Povolit rozbalení prioritu**  
 Pokud je povoleno, je možné ohraničit vybraný text v závorkách zadáním "(" v textovém editoru.  
  
 Funkce editoru textu v Galerii Visual Studio, najdete v seznamu [tady](http://go.microsoft.com/fwlink/?LinkId=692016). Příkladem je [C++ rychlých oprav](https://visualstudiogallery.msdn.microsoft.com/be91feef-8dc3-4f7a-ac9f-f34e7ca5918f), která podporuje následující:  
  
- **Přidat chybějící #include** -navrhuje relevantní #include pro neznámý symboly ve vašem kódu  
  
- **Přidat direktivu using obor názvů/plnému symbol** – podobně jako předchozí položce, ale pro obory názvů  
  
- **Přidat chybějící středníkem**  
  
- **Nápověda MSDN** -prohledat knihovnu MSDN pro chybové zprávy  
  
  Můžete buď při najetí myší nad vlnovku pro získání žárovky, nebo použijte výchozí klávesovou zkratku Ctrl + tečka (Ctrl +.). Všimněte si, že pro klávesové zkratky, vaše blikající kurzor o nemusí být umístěna na konkrétní chyba nebo token může být jednoduše na stejném řádku jako chyba, která se má vyvolat návrhy pro všechno, co je na daném řádku.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností editoru pro konkrétní jazyk](../../ide/reference/setting-language-specific-editor-options.md)   
 [Refaktoring v jazyce C++ (VC blogu)](http://blogs.msdn.com/b/vcblog/archive/2014/11/14/all-about-c-refactoring-in-visual-studio-2015-preview.aspx)



