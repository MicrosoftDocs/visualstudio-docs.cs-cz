---
title: Karta soubor stránky, dialogové okno vlastností procesu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Process properties for Windows NT
ms.assetid: daf41a06-8a55-48f6-95f5-49a8416bd308
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 24fdba37be2373623d94f03e45dc5e8a41a74b84
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192716"
---
# <a name="page-file-tab-process-properties-dialog-box"></a>Karta Soubor stránky, dialogové okno vlastností procesu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Použijte kartu **soubor stránky** k prohlédnutí stránkovacího souboru procesu. Chcete-li zobrazit [dialogové okno Vlastnosti procesu](../debugger/process-properties-dialog-box.md), přesuňte fokus do okna [zobrazení procesů](../debugger/processes-view.md) . Ve stromové struktuře vyberte libovolný uzel procesu a pak v nabídce **zobrazení** zvolte možnost **vlastnosti** .  
  
 Na kartě **soubor stránky** jsou k dispozici následující nastavení:  
  
|Entry|Popis|  
|-----------|-----------------|  
|**Bajty stránkovacího souboru**|Aktuální počet stránek, které tento proces používá ve stránkovacím souboru. Stránkovací soubor ukládá stránky dat, která proces používá, ale není obsažen v jiných souborech. Stránkovací soubor je používán všemi procesy a nedostatek místa ve stránkovacím souboru může způsobit chyby, pokud jsou spuštěné jiné procesy.|  
|**Bajty stránkovacího souboru ve špičce**|Maximální počet stránek, které tento proces použil ve stránkovacím souboru.|  
|**Chyby stránky**|Počet chyb stránek podle vláken spuštěných v tomto procesu. K chybě stránky dojde, když vlákno odkazuje na stránku virtuální paměti, která není v pracovní sadě v hlavní paměti. Proto se stránka z disku nenačte, pokud se nachází v pohotovostním seznamu, takže už je v hlavní paměti, nebo pokud ji používá jiný proces, se kterým se stránka sdílí.|
