---
title: Vyhodnocení zásobníku volání | Microsoft Docs
description: Přečtěte si o metodě EnumFrameInfo a o tom, jak ji implementovat pro zobrazení rámců zásobníku volání v průběhu režimu přerušení.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 223b1fff75c8fefdfed5bce5765d82fc5309738d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930730"
---
# <a name="call-stack-evaluation"></a>Vyhodnocení zásobníku volání
Aby bylo možné zobrazit rámce zásobníku volání během režimu přerušení, je nutné implementovat metodu [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) .

## <a name="methods-for-evaluation"></a>Metody pro vyhodnocení
 V případě jednoduchého ladicího stroje (DE) může existovat pouze jeden rámec zásobníku. Chcete-li prostudovat rámec zásobníku během režimu přerušení, je nutné implementovat následující metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Získá kontext kódu pro blok zásobníku. Kontext kódu představuje aktuální ukazatel instrukcí v rámci bloku zásobníku.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Získá kontext dokumentu pro blok zásobníku. Kontext dokumentu představuje aktuální umístění ve zdrojovém kódu pro blok zásobníku. Vyžaduje se pro zobrazení zdrojového kódu, když jste v programu zastavili.|

 Tyto metody vyžadují implementaci několika kontextových rozhraní a metod. Proto je nutné implementovat metodu [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) a následující metody [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Získá rozsah příkazů souboru kontextu dokumentu.|

 Chcete-li vytvořit výčet kontextů kódu, je nutné implementovat všechny metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
