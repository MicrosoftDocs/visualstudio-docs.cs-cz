---
title: 'Postupy: serializace informací o symbolu | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4ea056c48525014fffad0243dfeb4dd40a8daa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687015"
---
# <a name="how-to-serialize-symbol-information"></a>Postupy: Serializace informací o symbolu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete serializovat symboly, které musíte mít k analýze aplikace. Serializace symbolů přidá symboly do souboru. vsp. Přidáním informací o symbolech do souboru. vsp mohou jiné analyzovat sestavu o výkonu bez přístupu k původním symbolům. Pokud symboly nejsou serializovány, je nutné mít k analýze souboru. vsp původní instrumentované soubory. exe a PDB.  
  
### <a name="to-automatically-serialize-symbol-information"></a>Automatické serializace informací o symbolech  
  
1. V nabídce **Tools** (Nástroje) klikněte na **Options** (Možnosti).  
  
     Zobrazí se dialogové okno **Možnosti** .  
  
2. Klikněte na **Nástroje pro sledování výkonu**.  
  
3. V části **Obecné nastavení**vyberte možnost **automaticky serializovat informace o symbolech**.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace relací výkonu](../profiling/configuring-performance-sessions.md)   
 [Postupy: odkazování na informace o symbolech Windows](../profiling/how-to-reference-windows-symbol-information.md)   
 [Postupy: ukládání analyzovaných souborů sestav](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
