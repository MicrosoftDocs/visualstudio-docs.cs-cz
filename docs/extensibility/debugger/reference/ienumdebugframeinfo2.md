---
title: IEnumDebugFrameInfo2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumDebugFrameInfo2
helpviewer_keywords:
- IEnumDebugFrameInfo2
ms.assetid: 994e30ad-435a-4f9e-9272-d96d9e01099c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 858250c3c951880cf905ea6ee150f1ff61008204
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31123915"
---
# <a name="ienumdebugframeinfo2"></a>IEnumDebugFrameInfo2
Vytvoří výčet toto rozhraní [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IEnumDebugFrameInfo2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Modul ladění (DE) implementuje toto rozhraní uvést seznam struktury, která popisuje aktuální zásobníku volání.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Visual Studio volání [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) k získání tohoto rozhraní vždy, když bod přerušení, dojde v programu laděné výjimky nebo zastavení.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IEnumDebugFrameInfo2`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md)|Načte zadaný počet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury v posloupnosti výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugframeinfo2-skip.md)|Přeskočí zadaný počet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury v posloupnosti výčtu.|  
|[Resetování](../../../extensibility/debugger/reference/ienumdebugframeinfo2-reset.md)|Návrat na začátek v sekvenci výčtu.|  
|[klonování](../../../extensibility/debugger/reference/ienumdebugframeinfo2-clone.md)|Vytvoří enumerátor, který obsahuje stav výčtu jako aktuální enumerátor.|  
|[GetCount –](../../../extensibility/debugger/reference/ienumdebugframeinfo2-getcount.md)|Získá počet [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury v enumerátor.|  
  
## <a name="remarks"></a>Poznámky  
 Visual Studio obdrží jako první krok pro zpracování zarážek, výjimky nebo uživatelem generovaný pozastavení na programu laděné toto rozhraní. Seznam [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) struktury představuje aktuální zásobníku volání, s aktuálním volání funkce na začátku seznamu a nejstarší funkce volání na konci tohoto seznamu. Každý `FRAMEINFO` představuje rámce zásobníku, kontext, ve kterém se vyhodnotí výrazy a prohlédl lokální proměnné.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Základní rozhraní](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md)   
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)