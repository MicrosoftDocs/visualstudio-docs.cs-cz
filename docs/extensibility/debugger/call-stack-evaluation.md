---
title: Vyhodnocení zásobníku volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f59ce938d2b37c5967856dc64c9116fa9a695dbe
ms.sourcegitcommit: 0e5289414d90a314ca0d560c0c3fe9c88cb2217c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2018
ms.locfileid: "39151431"
---
# <a name="call-stack-evaluation"></a>Vyhodnocení zásobníku volání
Chcete-li zobrazit rámců zásobníku volání během režimu pozastavení, je nutné implementovat [EnumFrameInfo](../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) metody.  
  
## <a name="methods-for-evaluation"></a>Metody pro vyhodnocení  
 U jednoduchých ladicího stroje (DE) může být pouze jeden rámec zásobníku. Prozkoumat rámce zásobníku během režimu pozastavení, je nutné implementovat tyto metody [IDebugStackFrame2](../../extensibility/debugger/reference/idebugstackframe2.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetCodeContext](../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Získá kontext kódu pro blok zásobníku. Kontext kódu představuje aktuální ukazatel příkazu v bloku zásobníku.|  
|[GetDocumentContext](../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Získá kontext dokumentu pro rámce zásobníku. Kontext dokumentu představuje aktuální umístění ve zdrojovém kódu pro blok zásobníku. Vyžaduje se pro zobrazení zdrojového kódu, když se zastaví v programu.|  
  
 Tyto metody vyžadují provádění několika kontext související rozhraní a metody. Proto je nutné implementovat [GetDocumentContext](../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) metody a tyto metody [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md).  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetStatementRange](../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Získá rozsah souboru příkazů kontextu dokumentu.|  
  
 Výčet kontexty kódu, musí implementovat všechny metody [IEnumDebugCodeContexts2](../../extensibility/debugger/reference/ienumdebugcodecontexts2.md).  
  
## <a name="see-also"></a>Viz také:  
 [Ovládací prvek a stav zkušební spuštění](../../extensibility/debugger/execution-control-and-state-evaluation.md)