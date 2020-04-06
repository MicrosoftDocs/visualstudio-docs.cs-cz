---
title: IDebugStackFrame2::EnumProperties | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2::EnumProperties
helpviewer_keywords:
- IDebugStackFrame2::EnumProperties
ms.assetid: 334bb95e-c7e0-4008-9f06-8c3999e47ee8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f822f20cf4fb7a6fd5aa71b9cc1ec26bcd90e234
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719896"
---
# <a name="idebugstackframe2enumproperties"></a>IDebugStackFrame2::EnumProperties
Vytvoří čítač výčtu pro vlastnosti přidružené k rámečku zásobníku, jako jsou například místní proměnné.

## <a name="syntax"></a>Syntaxe

```cpp
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

## <a name="parameters"></a>Parametry
`dwFieldSpec`\
[v] Kombinace příznaků z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) výčtu, který určuje, která pole ve výčtu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury mají být vyplněny.

`nRadix`\
[v] Radix, který se použije při formátování všech číselných informací.

`refiid`\
[v] Guid filtru, který slouží k výběru [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury mají být `guidFilterLocals`uvedeny výčtu, například .

`dwTimeout`\
[v] Maximální doba v milisekundách čekání před návratem z této metody. Slouží `INFINITE` k čekání na neurčito.

`pcelt`\
[out] Vrátí počet vlastností, které jsou uvedeny. To je stejné jako volání [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md) metoda.

`ppEnum`\
[out] Vrátí objekt [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující seznam požadovaných vlastností.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vzhledem k tomu, že tato metoda umožňuje všechny vybrané vlastnosti, které mají být načteny s jedním voláním, je rychlejší než postupně volání [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) a [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metody.

## <a name="see-also"></a>Viz také
- [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
- [GetCount](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2-getcount.md)
- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
