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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0ed11d05e4351ac6ba76bc9aa10531a8a96ddf23
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105075403"
---
# <a name="stepping-in-break-mode"></a>Krokování v režimu pozastavení
V následující části je popsán proces, který nastane, když je ladicí program v režimu pozastavení a musí procházet kód:

## <a name="stepping-process"></a>Proces krokování

1. Pro provedení kroku zavolejte [IDebugProgram2:: Step](../../extensibility/debugger/reference/idebugprogram2-step.md) s argumenty [STEPKIND](../../extensibility/debugger/reference/stepkind.md) a [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) .

2. Po dokončení kroku odešlete [IDebugStepCompleteEvent2](../../extensibility/debugger/reference/idebugstepcompleteevent2.md) jako událost zastavení.

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
