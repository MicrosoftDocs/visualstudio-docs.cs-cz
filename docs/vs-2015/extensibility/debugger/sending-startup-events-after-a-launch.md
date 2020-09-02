---
title: Posílání událostí po spuštění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], startup events
ms.assetid: 306ea0b4-6d9e-4871-8d8d-a4032d422940
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: caf36e6713e49bb1470cd720ba2d04f689abba43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64804199"
---
# <a name="sending-startup-events-after-a-launch"></a>Odesílání událostí spuštění po spuštění
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jakmile je ladicí stroj (DE) připojen k programu, pošle řada událostí po spuštění zpět do ladicí relace.  
  
 Události při spuštění odeslané zpět do ladicí relace zahrnují následující:  
  
- Událost vytvoření motoru.  
  
- Událost vytvoření programu  
  
- Události vytvoření vlákna a načtení modulu.  
  
- Událost dokončení zátěže, která je odeslána, když je kód načten a připraven ke spuštění, ale před provedením jakéhokoli kódu  
  
  > [!NOTE]
  > Po pokračování této události jsou inicializovány globální proměnné a spuštěny rutiny spuštění.  
  
- Je možné provést jiné události vytvoření vlákna a načtení modulu.  
  
- Událost vstupního bodu, která signalizuje, že program dosáhl svého hlavního vstupního bodu, jako je například **Main** nebo `WinMain` . Tato událost se obvykle neposílá, pokud se DE připojí k programu, který je už spuštěný.  
  
  Prostřednictvím kódu programu DE First pošle Správce ladění relace (SDM) rozhraní [IDebugEngineCreateEvent2](../../extensibility/debugger/reference/idebugenginecreateevent2.md) , které představuje událost vytvoření modulu, následovanou [IDebugProgramCreateEvent2](../../extensibility/debugger/reference/idebugprogramcreateevent2.md), která představuje událost vytvoření programu.  
  
  Obvykle následuje jedna nebo více událostí vytvoření vlákna [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) a události načtení modulu [IDebugModuleLoadEvent2](../../extensibility/debugger/reference/idebugmoduleloadevent2.md) .  
  
  Když je kód načten a připraven ke spuštění, ale před spuštěním jakéhokoli kódu, DE pošle událost SDM, která [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) načtení dokončí. Nakonec, pokud program ještě není spuštěný, nástroj DE pošle událost vstupního bodu [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) , která signalizuje, že program dosáhl svého hlavního vstupního bodu a je připravený na ladění.  
  
## <a name="see-also"></a>Viz také  
 [Řízení provádění](../../extensibility/debugger/control-of-execution.md)   
 [Úlohy ladění](../../extensibility/debugger/debugging-tasks.md)
