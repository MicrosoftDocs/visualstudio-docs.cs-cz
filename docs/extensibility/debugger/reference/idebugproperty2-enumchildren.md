---
title: 'IDebugProperty2:: EnumChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::EnumChildren
helpviewer_keywords:
- IDebugProperty2::EnumChildren
ms.assetid: cf79f666-65d1-417c-af7c-9271bac9a267
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68880945d7534985e1788ae3b1f1e3755f79eeda
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916167"
---
# <a name="idebugproperty2enumchildren"></a>IDebugProperty2::EnumChildren
Načte seznam podřízených objektů vlastnosti.

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
pro Kombinace příznaků z výčtu [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md) , která určuje, která pole ve výčtu [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) struktur mají být vyplněna.

`dwRadix`\
pro Určuje základ, který má být použit při formátování číselných informací.

`guidFilter`\
pro Identifikátor GUID filtru používaného s `dwAttribFilter` parametry a `pszNameFilter` pro výběr `DEBUG_PROPERTY_INFO` podřízených objektů, které mají být vyčísleny Například `guidFilterLocals` filtry pro místní proměnné.

`dwAttribFilter`\
pro Kombinace příznaků z výčtu [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , které určují typ objektů k zobrazení výčtu, například `DBG_ATTRIB_METHOD` pro všechny metody, které mohou být podřízeny této vlastnosti. Používá se v kombinaci s `guidFilter` `pszNameFilter` parametry a.

`pszNameFilter`\
pro Název filtru používaného s `guidFilter` `dwAttribFilter` parametry a pro výběr, které `DEBUG_PROPERTY_INFO` podřízené položky mají být vyčísleny. Například nastavení tohoto parametru na filtry "MyX" pro všechny podřízené položky s názvem "MyX".

`dwTimeout`\
pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

`ppEnum`\
mimo Vrátí objekt [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md) obsahující seznam podřízených vlastností.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [DEBUGPROP_INFO_FLAGS](../../../extensibility/debugger/reference/debugprop-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)
