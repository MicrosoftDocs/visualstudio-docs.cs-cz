---
title: 'Postupy: serializace informací o symbolu | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8b608b41ea4fd1b5b7544604e8d04bed02361b06
ms.sourcegitcommit: bccb05b5b4e435f3c1f7c36ba342e7d4031eb398
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2018
ms.locfileid: "51220863"
---
# <a name="how-to-serialize-symbol-information"></a>Postupy: serializace informací o symbolu
Může serializovat symboly, které potřebujete k analýze vaší aplikace. Serializace symbolu přidá symboly. *vsp* souboru. Přidejte informace o symbolech pro. *vsp* souboru, ostatní analyzovat sestavu výkonu bez nutnosti přístupu k původní symboly. Pokud nejsou serializován symboly, musíte mít původní instrumentovány. *exe* a. *soubor PDB* souborů k analýze. *Vsp* souboru.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Automaticky serializovat informace o symbolech  
  
1.  Na **nástroje** nabídky, klikněte na tlačítko **možnosti**.  
  
     **Možnosti** se zobrazí dialogové okno.  
  
2.  Klikněte na tlačítko **nástroje pro měření výkonu**.  
  
3.  V části **obecné nastavení**vyberte **automaticky serializovat informace o symbolech**.  
  
## <a name="see-also"></a>Viz také:  
 [Konfigurace výkonnostních relací](../profiling/configuring-performance-sessions.md)   
 [Postupy: informace o symbolech Windows odkaz](../profiling/how-to-reference-windows-symbol-information.md)   
 [Postupy: uložení analyzovat soubory sestav](/previous-versions/visualstudio/visual-studio-2010/bb763106\(v\=vs.100\))