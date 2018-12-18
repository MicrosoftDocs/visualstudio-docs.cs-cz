---
title: IDebugStopCompleteEvent2 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b64c9719c6d2975829451dbf11cf584f98805c1b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51780474"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ladicí stroj (DE) můžete odeslat této události volitelné správce ladění relace (SDM) po zastavení programu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto je nové rozhraní pro [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)]. Předchozí verze nepodporuje asynchronní zastavení.  
  
 [Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) je volán SDM ve scénářích pro více procesů nebo více programů. Pokud jeden program odešle událostí ukončení SDM, SDM požádá o další programy zastavit příliš.  
  
 Používá se k asynchronně informovat SDM, program se zastavila. To je užitečné pro interpret ladicí modul, kde někdy žádný kód běží uvnitř laděného programu, takže [Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nemůže být dokončena synchronně. Pokud ladicí stroj chce využívat tato asynchronní oznámení, musí vracet `S_ASYNC_STOP` z [Zastavit](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

