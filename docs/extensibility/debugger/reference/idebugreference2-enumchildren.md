---
title: 'IDebugReference2:: EnumChildren | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::EnumChildren
helpviewer_keywords:
- IDebugReference2::EnumChildren
ms.assetid: 35b3c2f3-69f4-4013-b555-f847221f62e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d142f6c3715e2c3888c7ce60f349c50e84f7f16b
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909703"
---
# <a name="idebugreference2enumchildren"></a>IDebugReference2::EnumChildren
Získá seznam vybraných podřízených objektů odkazu. Vyhrazeno pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumChildren ( 
   DEBUGREF_INFO_FLAGS        dwFields,
   DWORD                      dwRadix,
   DBG_ATTRIB_FLAGS           dwAttribFilter,
   LPCOLESTR                  pszNameFilter,
   DWORD                      dwTimeout,
   IEnumDebugReferenceInfo2** ppEnum
);
```

```csharp
int EnumChildren ( 
   enum_DEBUGREF_INFO_FLAGS     dwFields,
   uint                         dwRadix,
   enum_DBG_ATTRIB_FLAGS        dwAttribFilter,
   string                       pszNameFilter,
   uint                         dwTimeout,
   out IEnumDebugReferenceInfo2 ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
pro Kombinace příznaků z výčtu [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) , která určuje, která pole ve výčtu [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) struktur mají být vyplněna.

`dwRadix`\
pro Číselná soustava, která se má použít při formátování číselných informací

`dwAttribFilter`\
pro Kombinace příznaků z výčtu [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md) , který se používá jako filtr v kombinaci s `pszNameFilter` parametrem pro výběr, které struktury mají být vyčísleny.

`pszNameFilter`\
pro Řetězec určující filtr, například "MyX", používaný v kombinaci s `dwAttribFilter` parametrem pro výběr struktury, které mají být vyčísleny.

`dwTimeout`\
pro Maximální doba (v milisekundách), po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

`ppEnum`\
mimo Vrátí objekt [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md) , který obsahuje seznam požadovaných podřízených vlastností.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DBG_ATTRIB_FLAGS](../../../extensibility/debugger/reference/dbg-attrib-flags.md)
- [IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)
