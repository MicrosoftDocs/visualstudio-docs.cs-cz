---
title: Krokování v režimu pozastavení | Microsoft Docs
description: Přečtěte si o procesu, který nastane, když je ladicí program v režimu pozastavení. Ladicí program musí potom Procházet kód.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode, stepping
- stepping, in break mode
- debugging [Debugging SDK], stepping in break mode
ms.assetid: b08dc8ee-6c63-4462-a097-6f525cfbb35a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 80273bf470a3ed0c342e781085de6e991508451c
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/08/2020
ms.locfileid: "96845190"
---
# <a name="stepping-in-break-mode"></a>Krokování v režimu pozastavení
V následující části je popsán proces, který nastane, když je ladicí program v režimu pozastavení a musí procházet kód:

## <a name="stepping-process"></a>Proces krokování

1. Pro provedení kroku zavolejte [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) s argumenty [STEPKIND](../../extensibility/debugger/reference/stepkind.md) a [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) .

2. Po dokončení kroku odešlete [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako událost zastavení.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
