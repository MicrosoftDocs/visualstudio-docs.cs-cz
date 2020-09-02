---
title: 'Postupy: použití okna moduly | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696130"
---
# <a name="how-to-use-the-modules-window"></a>Postupy: Použití okna Moduly
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ZNAČTE
> Tato funkce není k dispozici pro ladění SQL nebo skriptu.  
  
 Okno **moduly** obsahuje seznam knihoven DLL a souborů exe používaných vaším programem a zobrazuje relevantní informace pro každý z nich.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Zobrazení okna moduly v režimu přerušení nebo v režimu spuštění  
  
- V nabídce **ladit** zvolte **okna**a pak klikněte na **moduly**.  
  
     Ve výchozím nastavení okno **moduly** seřadí moduly podle pořadí načítání. Můžete ale zvolit řazení podle libovolného sloupce.  
  
### <a name="to-sort-by-any-column"></a>Postup při řazení podle libovolného sloupce  
  
- Klikněte na tlačítko v horní části sloupce.  
  
     Pomocí místní nabídky můžete načíst symboly nebo zadat cestu k symbolu z okna **moduly** .  
  
## <a name="loading-symbols"></a>Načítání symbolů  
 V okně **moduly** vidíte, které moduly mají načteny symboly ladění. Tyto informace se zobrazí ve sloupci **stav symbolu** . Pokud se stav **přeskočil, loadingCannot najít nebo otevřít soubor PDB**nebo **načíst zakázané zahrnutím/vyloučením**, můžete ladicí program nasměrovat tak, aby stahoval symboly ze serverů veřejných symbolů společnosti Microsoft, nebo načíst symboly z adresáře symbolů v počítači. Další informace naleznete v tématu [určení symbolu (. pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) .  
  
#### <a name="to-load-symbols-manually"></a>Postup ručního načtení symbolů  
  
1. V okně **moduly** klikněte pravým tlačítkem myši na modul, pro který nejsou načteny symboly.  
  
2. Najeďte na **načíst symboly z** a pak klikněte na **Microsoft Symbol Servers** nebo **cesta k symbolu**.  
  
#### <a name="to-change-symbol-load-settings"></a>Změna nastavení načítání symbolů  
  
1. V okně **moduly** klikněte pravým tlačítkem na libovolný modul.  
  
2. Klikněte na **Nastavení symbolu**.  
  
     Nyní můžete změnit nastavení načítání symbolů, jak je popsáno v tématu [určení umístění symbolů a chování při načítání](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Změny se projeví až po restartování ladicí relace.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Změna chování při načítání symbolů pro určitý modul  
  
1. V okně **moduly** klikněte pravým tlačítkem na modul.  
  
2. Přejděte na **Nastavení automatického načítání symbolů** a pak klikněte na **vždycky načíst ručně** nebo **výchozí**. Změny se projeví až po restartování ladicí relace.  
  
## <a name="see-also"></a>Viz také  
 [Přerušení provádění](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Zobrazení dat v ladicím programu](../debugger/viewing-data-in-the-debugger.md)   
 [Zadání symbolu (.pdb) a zdrojových souborů](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
