---
title: Ukončení a odpojení | Dokumentace Microsoftu
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
- programs, termination events
- debug engines, detaching from programs
ms.assetid: 268c1e51-6363-45d1-964c-1ab99bdfa4f9
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b1641a9a44a3f37b07e8192169e7301153881484
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51773870"
---
# <a name="termination-and-detaching"></a>Ukončení a odpojení
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následující část popisuje normální ukončení.  
  
## <a name="discussion"></a>Diskuse  
 Po [IDebugLoadCompleteEvent2](../../extensibility/debugger/reference/idebugloadcompleteevent2.md) nebo [IDebugEntryPointEvent2](../../extensibility/debugger/reference/idebugentrypointevent2.md) rozhraní bude pokračovat, pokud neexistují žádné zarážky, výjimky, chyby za běhu nebo nekonečné smyčky v aplikaci k ladění, laděný program se spustí do konce. To je normální ukončení.  
  
 Je nutné odeslat [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) implementovat normální ukončení. To vyžaduje, aby implementace [IDebugProgramDestroyEvent2::GetExitCode](../../extensibility/debugger/reference/idebugprogramdestroyevent2-getexitcode.md) metody.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vlastního ladicího stroje](../../extensibility/debugger/creating-a-custom-debug-engine.md)

