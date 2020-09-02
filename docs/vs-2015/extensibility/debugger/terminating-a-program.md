---
title: Ukončení programu | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f0b9ad248751af0885fa4edc0275be2ede5ddd9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421860"
---
# <a name="terminating-a-program"></a>Ukončení programu
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Následuje popis ukončení jednoho programu s jedním vláknem.  
  
## <a name="termination-process"></a>Ukončení procesu  
  
1. DE pošle [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) s platným [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).  
  
2. DE pošle [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) s platným [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).  
  
   Rozhraní IDE přejde do režimu návrhu. Modul ladění nebo běhové prostředí volá [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , aby bylo možné program odebrat z portu.  
  
## <a name="see-also"></a>Viz také  
 [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
