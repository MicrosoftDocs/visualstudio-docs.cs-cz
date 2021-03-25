---
title: Ukončení programu | Microsoft Docs
description: Tento článek popisuje, jak rozhraní IDE používá ladicí stroj k ukončení jednoho programu s jedním vláknem.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, termination events
- debugging [Debugging SDK], terminating a program
ms.assetid: eedda0a3-5e05-44fe-841d-a2f4866ac72d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: db67e0a391f40fc17a80e616e10aa46a600337a4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057855"
---
# <a name="terminating-a-program"></a>Ukončení programu
Následující část popisuje ukončení jednoho programu s jedním vláknem.

## <a name="termination-process"></a>Ukončení procesu

1. DE pošle [IDebugThreadDestroyEvent2](../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) s platným [IDebugThread2](../../extensibility/debugger/reference/idebugthread2.md).

2. DE pošle [IDebugProgramDestroyEvent2](../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) s platným [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md).

   Rozhraní IDE přejde do režimu návrhu. Modul ladění nebo běhové prostředí volá [IDebugPortNotify2:: RemoveProgramNode](../../extensibility/debugger/reference/idebugportnotify2-removeprogramnode.md) , aby bylo možné program odebrat z portu.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
