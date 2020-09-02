---
title: IDebugOutputStringEvent2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugOutputStringEvent2
helpviewer_keywords:
- IDebugOutputStringEvent2 interface
ms.assetid: 86596fd1-cecc-4813-8add-dc3d70068f9b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 844d93a6752538c6b7239b6c10688fdfbd98b401
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65695193"
---
# <a name="idebugoutputstringevent2"></a>IDebugOutputStringEvent2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Toto rozhraní je odesláno ladicím modulem (DE) do nástroje Session Debug Manager (SDM) pro výstup řetězce.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugOutputStringEvent2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 DE implementuje toto rozhraní k odeslání řetězce do okna **výstupu** rozhraní IDE. Rozhraní [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) musí být implementováno na stejném objektu jako toto rozhraní. SDM používá pro [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) přístup k rozhraní QueryInterface `IDebugEvent2` .  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 DE vytvoří a odešle tento objekt události pro odeslání řetězce do okna **výstup** . Událost se odesílá pomocí funkce zpětného volání [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) , která je dodána serverem SDM, když je připojená k laděnému programu.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 Následující tabulka ukazuje metodu `IDebugOutputStringEvent2` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetString](../../../extensibility/debugger/reference/idebugoutputstringevent2-getstring.md)|Načte zobrazitelnou zprávu.|  
  
## <a name="remarks"></a>Poznámky  
 Například v nespravovaném kódu může řetězec, který má být výstup, nacházet, pokud program, který ladíte, odesílá řetězec do `OutputDebugString` funkce Win32. Tento řetězec je zachycen nástrojem DE a odeslán do SDM jako `IDebugOutputStringEvent2` událost.  
  
 K odeslání zprávy, která vyžaduje reakci uživatele, použijte [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) .  
  
 K odeslání chybové zprávy, která nevyžaduje odpověď, použijte [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) .  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
