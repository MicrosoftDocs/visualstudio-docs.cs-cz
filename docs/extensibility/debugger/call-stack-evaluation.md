---
title: Vyhodnocení zásobníku volání | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b5557d7eae0ffe54b0f01f1f9e95935d71455229
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739176"
---
# <a name="call-stack-evaluation"></a>Vyhodnocení zásobníku volání
Chcete-li zobrazit rámce zásobníku zásobníku volání během režimu přerušení, je nutné implementovat metodu [EnumFrameInfo.](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)

## <a name="methods-for-evaluation"></a>Metody hodnocení
 Pro jednoduchý ladicí modul (DE) může existovat pouze jeden rámec zásobníku. Chcete-li prozkoumat rámec zásobníku během režimu přerušení, je nutné implementovat následující metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Získá kontext kódu pro rámec zásobníku. Kontext kódu představuje aktuální ukazatel instrukce v rámci zásobníku.|
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Získá kontext dokumentu pro rámec zásobníku. Kontext dokumentu představuje aktuální umístění ve zdrojovém kódu rámce zásobníku. Vyžadováno pro zobrazení zdrojového kódu při zastavení v programu.|

 Tyto metody vyžadují implementaci několika kontextových rozhraní a metod. Proto je nutné implementovat [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metodu a následující metody [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).

|Metoda|Popis|
|------------|-----------------|
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Získá rozsah příkazu souboru kontextu dokumentu.|

 Chcete-li vytvořit výčet kontextu kódu, je nutné implementovat všechny metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).

## <a name="see-also"></a>Viz také
- [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
