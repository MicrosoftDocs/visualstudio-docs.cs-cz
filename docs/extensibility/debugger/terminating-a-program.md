---
title: Ukončení programu | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 985b20fe75f8ceee3d434ac681b437c51baf85e8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80712513"
---
# <a name="terminating-a-program"></a>Ukončení programu
Následující část popisuje ukončení jednoho programu s jedním vláknem.

## <a name="termination-process"></a>Ukončení procesu

1. DE pošle [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) s platným [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. DE pošle [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) s platným [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Rozhraní IDE přejde do režimu návrhu. Modul ladění nebo běhové prostředí volá [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , aby bylo možné program odebrat z portu.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
