---
title: Zobrazení knihovny DLL a spustitelné soubory
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 2702eb38e895f5fa9021fae754ae1e4a9325cf18
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53066779"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>V okně moduly zobrazení knihovny DLL a spustitelné soubory (C#, C++, Visual Basic, F#)
 
Během ladění sady Visual Studio **moduly** okno obsahuje seznam a zobrazuje informace o knihovnách DLL a spustitelné soubory (*.exe* soubory) vaše aplikace používá. 

> [!NOTE]
> Okno modulů není k dispozici pro SQL nebo ladění skriptů. 
  
## <a name="use-the-modules-window"></a>Použití okna moduly

Chcete-li otevřít okno moduly během ladění, vyberte **ladění** > **Windows** > **moduly**. 
  
Ve výchozím nastavení **moduly** okno seřadí podle pořadí načítání modulů. Seřadit podle kteréhokoli sloupce okno, vyberte záhlaví v horní části sloupce.  
  
## <a name="load-symbols"></a>Načtení symbolů  

**Status symbolu** sloupec **moduly** okno zobrazuje, které moduly mají načíst symboly ladění. Pokud je stav **bylo vynecháno načítání symbolů**, **nejde najít nebo otevřít soubor PDB**, nebo **nastavení zahrnutí a vyloučení zakázalo načtení**, můžete ručně načíst symboly. Další informace o načtení a použití symboly, naleznete v tématu [zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Načtení symbolů ručně:**  

1. V **moduly** okna, klikněte pravým tlačítkem na modul pro symboly, které nebyly načteny. 
   
   - Vyberte **načíst informace o symbolech** podrobnosti o tom, proč se nenačetla symboly. 
   
   - Vyberte **načíst symboly** ručně načíst symboly.  
   
1. Pokud není načíst symboly, vyberte **nastavení symbolu** otevřít **možnosti** dialogového okna a zadejte nebo změňte umístění pro načítání symbolů. 
   
   Můžete stáhnout symboly z veřejné symbolové servery společnosti Microsoft nebo jiné servery nebo načíst symboly ze složky v počítači. Podrobnosti najdete v tématu [zadejte umístění symbolu a chování načítání](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).   

**Chcete-li změnit nastavení chování načítání symbolů:**  

1. V **moduly** okna, klikněte pravým tlačítkem na jakýkoli modul.  
   
1. Vyberte **Symbol nastavení**.  
  
1. Vyberte **načtení všech symbolů**, nebo vyberte které moduly chcete zahrnout nebo vyloučit.  
  
1. Vyberte **OK**. Změny se projeví v další relace ladění.  
  
**Chcete-li změnit chování pro konkrétní modul načítání symbolů:**  

1.  V **moduly** okna, klikněte pravým tlačítkem na modul.  

1.  V místní nabídce vyberte nebo zrušte výběr **vždy zatížení automaticky**. Změny se projeví v další relace ladění.  
  
## <a name="see-also"></a>Viz také:  
 [Pozastavení provádění](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)