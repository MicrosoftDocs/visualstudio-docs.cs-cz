---
title: Vstup do režimu přerušení | Microsoft Docs
description: Přečtěte si o procesu, ke kterému dochází pro zarážku, ke které došlo ve funkci, běží na řádku zdrojového kódu na kurzoru nebo na zarážce.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- break mode
- debugging [Debugging SDK], entering break mode
ms.assetid: e9a8a241-cd21-4d4e-999a-283554c288b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6e8af8aa2765e199e8e278982669f68b3019b6c2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105097211"
---
# <a name="enter-break-mode"></a>Zadat režim přerušení
Následující informace popisují proces, ke kterému dochází, když je zjištěna zarážka po rozkrokování do funkce, spuštění na řádku zdrojového kódu, který obsahuje kurzor nebo je spuštěn na zarážku.

## <a name="break-mode-process"></a>Proces režimu přerušení

1. Ladicí stroj (DE) odesílá [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md), [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md)nebo jakoukoliv jinou událost zastavení, aby mohl IDE přejít do režimu přerušení.

2. Model SDM získá informace zásobníku volání z vlákna následujícím způsobem:

    - [IDebugThread2::EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

    - [IEnumDebugFrameInfo2::GetCount](../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)

    - [IEnumDebugFrameInfo2::Next](../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)

    - [IDebugStackFrame2:: GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) získat informace o zdrojovém kódu

    - [IDebugDocumentContext2:: GetName](../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md) pro získání názvu souboru

    - [IDebugDocumentContext2:: GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) Získá rozsah příkazu.

    - [IDebugStackFrame2:: GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md) získat informace o paměti

## <a name="see-also"></a>Viz také
- [Volání událostí ladicího programu](../../extensibility/debugger/calling-debugger-events.md)
