---
title: Karta prostor, dialogové okno vlastností procesu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: c4de1866-7447-48f7-aa88-28ad92c0b930
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2cab2263da44ba46d7fbbe301f61e51b5308ba73
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51767449"
---
# <a name="space-tab-process-properties-dialog-box"></a>Karta Prostor, dialogové okno vlastností procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **místo** kartu prozkoumat adresního prostoru procesu. Pro zobrazení [dialogové okno vlastností procesu](../debugger/process-properties-dialog-box.md), přesunout fokus [zobrazení procesů](../debugger/processes-view.md) okno. Vyberte libovolný uzel procesu ve stromové struktuře a pak zvolte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **místo** kartu:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Zobrazit pro prostor označený jako**|Toto pole se seznamem použijte k výběru kategorie místa (obrázků, mapována, vyhrazená nebo nepřiřazené).|  
|**Spustitelný soubor – bajty**|Pro vybranou kategorii součet všech adresní prostor, který tento proces používá. Spustitelný soubor paměti je paměť, která mohou být provedeny programy, ale nemusí číst nebo zapisovat.|  
|**Exec – bajty jen pro čtení**|Pro vybranou kategorii součet všech adresní prostor v pomocí vlastnosti jen pro čtení, které tento proces používá. Exec – jen pro čtení paměti je paměť, která může být spuštěn, stejně jako čtení.|  
|**Exec-pro čtení a zápis bajtů**|Pro vybranou kategorii součet všech adresní prostor používané pro čtení i zápis vlastnosti, které tento proces používá. Exec-pro čtení a zápis paměti je paměť, která může aplikace také lze číst a upravovat.|  
|**Exec – zápis kopírování bajtů**|Pro vybranou kategorii součet všech adresní prostor, který může programy také lze číst a zapisovat. Tento typ ochrany se používá, když paměti musí být sdílen mezi procesy. Pokud procesy, které sdílení pouze přečíst paměť, pak budou používat stejnou paměť. Pokud sdílející proces vyžaduje oprávnění k zápisu, bude pro proces vytvořena kopie tuto paměť.|  
|**Bez přístupu – bajty**|Pro vybranou kategorii součet všech adresní prostor, který brání jeho použití procesu. Narušení přístupu se generuje, pokud je zápis nebo dojde k pokusu o čtení.|  
|**Bajty jen pro čtení**|Pro vybranou kategorii součet všech adresní prostor, který může být spuštěn, stejně jako čtení.|  
|**Bajty pro čtení i zápis**|Pro vybranou kategorii součet všech adresní prostor, který umožňuje čtení a zápis.|  
|**Bajty zápisu a kopírování**|Pro vybranou kategorii součet adresní prostor, který umožňuje sdílení paměti pro čtení, ale ne pro zápis. Pokud procesy čtou tuto paměť, můžou sdílet stejnou paměť. Ale při sdílení procesu chce mít přístup pro čtení a zápisu do této sdílené paměti, je vytvořena kopie, tato paměť pro zápis.|



