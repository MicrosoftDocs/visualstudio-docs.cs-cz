---
title: IDebugField | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugField
helpviewer_keywords:
- IDebugField interface
ms.assetid: adecdd1c-b1b9-4027-92da-74cbe910636f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e2ff92f339568a6a20e2f85a0b2deae9c8db244f
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
ms.locfileid: "31116299"
---
# <a name="idebugfield"></a>IDebugField
Toto rozhraní představuje pole, který je popis symbolu nebo typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
IDebugField : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Poznámky pro implementátory  
 Toto rozhraní implementuje poskytovatele symbol jako základní třída pro všechna pole.  
  
## <a name="notes-for-callers"></a>Poznámky pro volající  
 Toto rozhraní je základní třídu pro všechna pole. Podle návratová hodnota [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md), toto rozhraní může vrátit více specializované rozhraní pomocí [QueryInterface](/cpp/atl/queryinterface). Kromě toho vrátí mnoho rozhraní `IDebugField` objekty z různých metod.  
  
## <a name="methods-in-vtable-order"></a>Metody v tabulce Vtable pořadí  
 Následující tabulka uvádí metody `IDebugField`.  
  
|Metoda|Popis|  
|------------|-----------------|  
|[GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)|Získá zobrazitelné informací o symbolu nebo typu.|  
|[GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md)|Získá druh typu pole.|  
|[GETTYPE –](../../../extensibility/debugger/reference/idebugfield-gettype.md)|Získá typ pole.|  
|[GetContainer](../../../extensibility/debugger/reference/idebugfield-getcontainer.md)|Získá kontejner pole.|  
|[Getaddress –](../../../extensibility/debugger/reference/idebugfield-getaddress.md)|Získá adresu pole.|  
|[GetSize](../../../extensibility/debugger/reference/idebugfield-getsize.md)|Získá velikost pole, v bajtech.|  
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugfield-getextendedinfo.md)|Získá rozšířené informace o pole.|  
|[Rovná](../../../extensibility/debugger/reference/idebugfield-equal.md)|Porovná dvě pole.|  
|[GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)|Získá nezávislé na typ informací o symbolu nebo typu.|  
  
## <a name="remarks"></a>Poznámky  
 Typ je ekvivalentní pro jazyk C `typedef`.  
  
 V následujícím příkladu jazyk C++ `weather` je typu třídy a `sunny` a `stormy` jsou symboly:  
  
```cpp  
class weather;  
weather sunny;  
weather stormy;  
```  
  
 Jestli pole představuje symbol nebo typ se dá určit pomocí volání [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) a prozkoumání [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) výsledek. Pokud `FIELD_KIND_TYPE` je nastaven bit, pole je typu a pokud `FIELD_KIND_SYMBOL` je nastaven bit, je symbol.  
  
## <a name="requirements"></a>Požadavky  
 Záhlaví: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Viz také  
 [Rozhraní poskytovatele symbolů ](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)