---
title: Karta soubor stránky, dialogové okno vlastností procesu | Dokumentace Microsoftu
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
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ea94eb6382c5061311f07bcc5f57ec09d907d86
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744137"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Soubor stránky, dialogové okno vlastností procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použití **stránkovací soubor** kartu prozkoumat stránkovacího souboru procesu. Pro zobrazení [dialogové okno vlastností procesu](../debugger/process-properties-dialog-box.md), přesunout fokus [zobrazení procesů](../debugger/processes-view.md) okno. Vyberte libovolný uzel procesu ve stromové struktuře a pak zvolte **vlastnosti** z **zobrazení** nabídky.  
  
 Následující nastavení jsou k dispozici na **stránkovací soubor** kartu:  
  
|Položka|Popis|  
|-----------|-----------------|  
|**Bajty stránkovacího souboru**|Aktuální číslo stránky, které tento proces používá ve stránkovacím souboru. Stránkovací soubor uloží stránek využívané procesem, ale nejsou obsažené v jiných souborech. Stránkovací soubor je používán všechny procesy a nedostatečné místo ve stránkovacím souboru mohou způsobit chyby, zatímco jiné procesy jsou spuštěny.|  
|**Bajty stránkovacího souboru – Špička**|Maximální počet stránek, které tento proces se má použít ve stránkovacím souboru.|  
|**Chyby stránek**|Počet chyb stránek podle vlákna provádění v tomto procesu. Stránkování nastane, pokud vlákno odkazuje na stránku virtuální paměti, která není v jeho pracovního sadě v hlavní paměti. Díky tomu se na stránce nebudou načteny z disku Pokud je na seznamu a proto již do paměti, nebo pokud jej používá jiný proces se na stránce se sdílí.|



