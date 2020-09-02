---
title: IDebugStopCompleteEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugStopCompleteEvent2 interface
ms.assetid: ff3e89f4-61bb-489d-901c-447260100218
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a9c2a6a6e69bf47751706710801dd78c832ccd2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546915"
---
# <a name="idebugstopcompleteevent2"></a>IDebugStopCompleteEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ladicí stroj (DE) může poslat tuto volitelnou událost správci ladění relace (SDM), když se program zastaví.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugStopCompleteEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto je nové rozhraní pro [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] . Předchozí verze nepodporovaly asynchronní zastavování.  
  
 [Stop](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) se volá v modelu SDM ve scénářích s více procesy nebo s více programy. Když jeden program pošle událost zastavení do SDM, požadavky SDM na zastavení také vyžádají jiné programy.  
  
 Slouží k asynchronnímu informování SDM, že se program zastavil. To je užitečné pro ladicí stroj překladače, kde někdy v laděném programu není spuštěn žádný kód, takže [zastavení](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md) nelze dokončit synchronně. Pokud ladicí stroj chce použít toto asynchronní oznámení, musí se vrátit z jeho `S_ASYNC_STOP` [zastavení](../../../extensibility/debugger/reference/idebugengineprogram2-stop.md).  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll
