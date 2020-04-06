---
title: IDebugProperty2::EnumChildren | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d6d3908c469b489eb16e4662f7515ea624825e3b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721520"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Načte seznam podřízených položek vlastnosti.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumChildren ( 
   DEBUGPROP_INFO_FLAGS      dwFields,
   DWORD                     dwRadix,
   REFGUID                   guidFilter,
   DBG_ATTRIB_FLAGS          dwAttribFilter,
   LPCOLESTR                 pszNameFilter,
   DWORD                     dwTimeout,
   IEnumDebugPropertyInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGPROP_INFO_FLAGS   dwFields,
   uint                        dwRadix,
   ref Guid                    guidFilter,
   uint                        dwAttribFilter,
   string                      pszNameFilter,
   uint                        dwTimeout,
   out IEnumDebugPropertyInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[v] Kombinace příznaků z [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) výčtu, který určuje, která pole ve výčtu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktury mají být vyplněny.

`dwRadix`\
[v] Určuje radix, který se má použít při formátování jakýchkoli číselných informací.

`guidFilter`\
[v] GUID filtru použitého `dwAttribFilter` s `pszNameFilter` parametry a `DEBUG_PROPERTY_INFO` pro výběr podřízených dětech, které mají být uvedeny ve výčtu. Například `guidFilterLocals` filtry pro místní proměnné.

`dwAttribFilter`\
[v] Kombinace příznaků z [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) výčtu, který určuje, jaký typ objektů výčet, například `DBG_ATTRIB_METHOD` pro všechny metody, které mohou být podřízené této vlastnosti. Používá se v `guidFilter` `pszNameFilter` kombinaci s parametry a.

`pszNameFilter`\
[v] Název filtru použitého `guidFilter` s `dwAttribFilter` parametry a `DEBUG_PROPERTY_INFO` pro výběr podřízených dětech, které mají být uvedeny. Například nastavení tohoto parametru na filtry MyX pro všechny podřízené položky s názvem MyX.

`dwTimeout`\
[v] Určuje maximální dobu v milisekundách, po kterou se má čekat před návratem z této metody. Slouží `INFINITE` k čekání na neurčito.

`ppEnum`\
[out] Vrátí objekt [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující seznam podřízených vlastností.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
