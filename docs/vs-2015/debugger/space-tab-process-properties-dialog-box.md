---
title: Karta prostor, dialogové okno vlastností procesu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: de5df4c55feba8c9aaba0def7585029cc71426b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189429"
---
# <a name="space-tab-process-properties-dialog-box"></a>Karta Prostor, dialogové okno vlastností procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kartu **prostor** použijte k prohlédnutí adresního prostoru procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesuňte fokus do okna [zobrazení procesů](../debugger/processes-view.md) . Ve stromové struktuře vyberte libovolný uzel procesu a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .  
  
 Na kartě **prostor** jsou k dispozici následující nastavení:  
  
|Entry|Popis|  
|-----------|-----------------|  
|**Zobrazit pro prostor označený jako**|Pomocí tohoto seznamu můžete vybrat kategorii prostoru (obrázek, mapovaný, rezervovaný nebo nepřiřazený).|  
|**Spustitelné bajty**|Pro vybranou kategorii součet veškerého adresního prostoru, který tento proces používá. Spustitelná paměť je paměť, kterou můžou spouštět programy, ale nemusí se číst ani zapisovat.|  
|**Exec – bajty jen pro čtení**|Pro vybranou kategorii je součet veškerého adresního prostoru používaného ve vlastnostech jen pro čtení, které tento proces používá. Exec – paměť, která je jen pro čtení, je paměť, kterou lze spustit i číst.|  
|**Exec – bajty pro čtení i zápis**|Pro vybranou kategorii je součet všech používaných adresního prostoru s vlastnostmi pro čtení i zápis, které tento proces používá. Exec – paměť pro čtení i zápis je paměť, kterou můžou spouštět programy a také číst a upravovat.|  
|**Exec – zapsat bajty kopírování**|V případě vybrané kategorie se jedná o součet všech adresního prostoru, který mohou programy spouštět, a také čtení a zápis. Tento typ ochrany se používá v případě, že je potřeba sdílet paměť mezi procesy. Pokud se pouze procesy sdílení čtou do paměti, pak všechny použijí stejnou paměť. Pokud proces sdílení přeje přístup k zápisu, bude pro tento proces vytvořen kopie této paměti.|  
|**Bez přístupu – bajty**|Pro vybranou kategorii součet veškerého adresního prostoru, který brání procesu v jeho používání. Při pokusu o zápis nebo čtení se vygeneruje porušení přístupu.|  
|**Bajty jen pro čtení**|Pro vybranou kategorii součet všech adresního prostoru, který lze spustit, a také čtení.|  
|**Bajty pro čtení i zápis**|Pro vybranou kategorii součet všech adresního prostoru, který umožňuje čtení a zápis.|  
|**Bajty zápisu a kopírování**|Pro vybranou kategorii součet všech adresního prostoru, který umožňuje sdílení paměti pro čtení, ale nikoli pro zápis. Když procesy čtou tuto paměť, můžou sdílet stejnou paměť. Pokud ale proces sdílení chce mít k této sdílené paměti přístup pro čtení a zápis, vytvoří se kopie této paměti pro zápis.|
