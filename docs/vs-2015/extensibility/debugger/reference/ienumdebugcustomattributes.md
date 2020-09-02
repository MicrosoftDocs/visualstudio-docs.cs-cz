---
title: IEnumDebugCustomAttributes | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumCustomAttributes
helpviewer_keywords:
- IEnumDebugCustomAttributes interface
ms.assetid: 11aa768d-1852-44d6-9de3-17f9bafaded2
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7a0e1b361e99ef1e32a7dd327e531a1049f4009a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158077"
---
# <a name="ienumdebugcustomattributes"></a>IEnumDebugCustomAttributes
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří výčet vlastních atributů.  
  
## <a name="syntax"></a>Syntax  
  
```  
IEnumCustomAttributes : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Zprostředkovatel symbolů implementuje toto rozhraní pro podporu vlastních atributů (přes rozhraní [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md) ).  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 [EnumCustomAttributes –](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md) vrátí toto rozhraní.  
  
## <a name="methods-in-vtable-order"></a>Metody v pořadí vtable  
 V následující tabulce jsou uvedeny metody `IEnumDebugCustomAttributes` .  
  
|Metoda|Popis|  
|------------|-----------------|  
|[Další](../../../extensibility/debugger/reference/ienumdebugcustomattributes-next.md)|Načte zadaný počet vlastních atributů v sekvenci výčtu.|  
|[Přeskočit](../../../extensibility/debugger/reference/ienumdebugcustomattributes-skip.md)|Přeskočí zadaný počet vlastních atributů v sekvenci výčtu.|  
|[Reset](../../../extensibility/debugger/reference/ienumdebugcustomattributes-reset.md)|Obnoví posloupnost výčtu na začátek.|  
|[Klonování](../../../extensibility/debugger/reference/ienumdebugcustomattributes-clone.md)|Vytvoří enumerátor, který obsahuje stejný stav výčtu jako aktuální enumerátor.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcustomattributes-getcount.md)|Získá počet vlastních atributů v enumerátoru.|  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: SH. h  
  
 Obor názvů: Microsoft. VisualStudio. Debugger. Interop  
  
 Sestavení: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní poskytovatele symbolů](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [EnumCustomAttributes –](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)   
 [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
