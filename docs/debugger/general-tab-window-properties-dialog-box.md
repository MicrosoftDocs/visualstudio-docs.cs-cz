---
title: Karta Obecné, dialogové okno Vlastnosti okna | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Window Properties dialog box, General Tab
ms.assetid: 19142c60-9b32-46ba-a556-b62fd77568c1
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f762d935edab5720ccd9add155dac3d0e5f2f186
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31480121"
---
# <a name="general-tab-window-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastnosti okna
Použití **Obecné** karta zobrazuje informace o vybrané okno. Chcete-li zobrazit [dialogové okno Vlastnosti okna](../debugger/window-properties-dialog-box.md), přesunout fokus na [zobrazení oken](../debugger/windows-view.md) okno. Vyberte libovolný uzel okno ve stromové struktuře, a potom vyberte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **Obecné** karty:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Popisek – okno**|Text v titulku okna, nebo obsažené v okně, pokud je ovládací prvek text.|  
|**Popisovač okna**|Jedinečné ID toto okno. Jsou opakovaně využívána popisovač okna; okno identifikují pouze po dobu jeho existence toto okno.|  
|**Procedury oken**|Virtuální adresa funkce procedury okna pro toto okno. Toto pole se také označuje, jestli je toto okno okno kódování Unicode a zda je rozčleněné.|  
|**rámeček**|Ohraničující obdélník pro okno. Velikost rámeček se také zobrazí. Jednotky jsou pixelů souřadnice obrazovky.|  
|**Rect – obnovená**|Ohraničující obdélník pro obnovené okno. Velikost rámeček se také zobrazí. Rect obnovené – se liší od obdélníku jenom v případě, že je maximalizovaný nebo minimalizovaná okna. Jednotky jsou pixelů souřadnice obrazovky.|  
|**Rect – klient**|Ohraničující obdélník pro klientské oblasti okna. Velikost rámeček se také zobrazí. Jednotky jsou pixelů relativně k levé horní části okna klientské oblasti.|  
|**Popisovač instance**|Popisovač instance aplikace. Instance popisovače nejsou jedinečné.|  
|**ID ovládacího prvku nebo obslužná rutina nabídky**|Pokud je toto okno se zobrazí podřízeného okna, zobrazí se ID ovládacího prvku popisek. ID ovládacího prvku je celé číslo, které identifikuje ID podřízeného okna ovládacího prvku. Pokud není okno se zobrazí podřízeného okna, se zobrazí popisek zpracování nabídky. Popisovač nabídky je celé číslo, které identifikuje popisovač nabídce přidružené k tomuto časovému období.|  
|**Uživatelská Data**|Data specifické pro aplikaci, která je připojena k tato struktura okno.|  
|**Okno bajtů**|Počet bajtů navíc, které jsou přidružené k tomuto časovému období. Význam těchto bajtů je určen podle aplikace. Rozbalte seznam zobrazíte bajtových hodnot ve formátu DWORD.|