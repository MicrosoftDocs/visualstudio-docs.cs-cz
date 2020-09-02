---
title: 'IDebugStackFrame2:: Enumproperties – | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f92db2c2fbafcd5be991281d7da4f594dcfb2c85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68164806"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vytvoří enumerátor pro vlastnosti přidružené k bloku zásobníku, například místní proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp#  
HRESULT EnumProperties (   
   DEBUGPROP_INFO_FLAGS      dwFieldSpec,  
   UINT                      nRadix,  
   REFIID                    refiid,  
   DWORD                     dwTimeout,  
   ULONG*                    pcelt,  
   IEnumDebugPropertyInfo2** ppEnum  
);  
```  
  
```csharp  
int EnumProperties (   
   enum_DEBUGPROP_INFO_FLAGS   dwFieldSpec,  
   uint                        nRadix,  
   ref Guid                    refiid,  
   uint                        dwTimeout,  
   out uint                    pcelt,  
   out IEnumDebugPropertyInfo2 ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwFieldSpec`  
 pro Kombinace příznaků z výčtu [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , která určuje, která pole ve výčtu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur mají být vyplněna.  
  
 `nRadix`  
 pro Číselná soustava, která se má použít při formátování číselných informací  
  
 `refiid`  
 pro Identifikátor GUID filtru používaného k výběru, které [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury mají být vyčísleny, například `guidFilterLocals` .  
  
 `dwTimeout`  
 pro Maximální doba (v milisekundách), po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.  
  
 `pcelt`  
 mimo Vrátí počet vlastností výčtového typu. To je stejné jako volání metody [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) .  
  
 `ppEnum`  
 mimo Vrátí objekt [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující seznam požadovaných vlastností.  
  
## <a name="return-value"></a>Návratová hodnota  
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.  
  
## <a name="remarks"></a>Poznámky  
 Vzhledem k tomu, že tato metoda umožňuje načtení všech vybraných vlastností jediným voláním, je rychlejší než při sekvenčním volání metod [GetDebugProperty –](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) .  
  
## <a name="see-also"></a>Viz také  
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)   
 [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)   
 [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)   
 [GetDebugProperty –](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
