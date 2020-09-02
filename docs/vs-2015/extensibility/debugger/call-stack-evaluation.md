---
title: Vyhodnocení zásobníku volání | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], call stack evaluation
- call stacks, evaluation
ms.assetid: 373d6b49-0459-4cce-816e-05745a44fe49
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 15fecbc61fec8ba7aa62ca7d79cf11c56b7ce938
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68146405"
---
# <a name="call-stack-evaluation"></a>Vyhodnocení zásobníku volání
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

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
 [Řízení provádění a vyhodnocení stavu](../../extensibility/debugger/execution-control-and-state-evaluation.md)
