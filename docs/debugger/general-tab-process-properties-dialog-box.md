---
title: Zpracování karta Obecné, dialogové okno Vlastnosti | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: 86f4d61d-a594-4aac-8960-c5279b4a10fd
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3dcefc8be643c74349102261725c4879c0e161cd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471697"
---
# <a name="general-tab-process-properties-dialog-box"></a>Karta Obecné, dialogové okno vlastností procesu
Použití **Obecné** a další informace o specifickém procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesunout fokus na [zobrazení procesů](../debugger/processes-view.md) okno. Vyberte libovolný uzel procesu ve stromové struktuře, a potom vyberte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **Obecné** karty:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Název modulu**|Název modulu.|  
|**ID procesu**|Jedinečný Identifikátor tohoto procesu. Čísla ID procesu jsou opakovaně využívána, takže identifikují proces pouze po dobu jeho existence tohoto procesu. Typ objektu procesu se vytvoří při spuštění programu. Všechny vláken v procesu sdílet stejnou adresní prostor a mít přístup ke stejným datům.|  
|**Základní prioritou**|Aktuální základní prioritu tohoto procesu. Vlákna v rámci procesu můžete vyvolat a snížit vlastní základní prioritu relativně k procesu základní prioritu.|  
|**Vlákna**|Počet vláken, které jsou momentálně aktivní v tomto procesu.|  
|**Čas procesoru**|Celkový čas procesoru strávené o tomto procesu a jeho vláken. Rovno uživatelského času plus privilegovaného času.|  
|**Uživatelský čas**|Kumulativní uplynulý čas, který tento proces vláken mít stráví provádění kódu v uživatelském režimu v jiných než nečinných vláken. Aplikace spouští v uživatelském režimu, stejně jako subsystémy například Správce oken a modulu grafiky.|  
|**Privilegovaného času**|Celkem uběhlý čas tento proces běžel v privilegovaném režimu v jiných než nečinných vláken. Vrstvy služby, rutiny vedení a jádra spustit v privilegovaném režimu. Ovladače zařízení pro většinu jiná zařízení než grafických adaptérů a tiskárny provést také v privilegovaném režimu. Některé práci, kterou Windows nemá pro vaši aplikaci se mohou objevit v jiných procesech subsystému kromě privilegovaného času.|  
|**Uplynulý čas**|Celkem uběhlý čas, který tento proces běžel.|