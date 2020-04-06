---
title: IDebugReference2::GetReferenceInfo | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetReferenceInfo
helpviewer_keywords:
- IDebugReference2::GetReferenceInfo
ms.assetid: ae611714-f114-4cf2-b5bb-37461e6ff289
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 4fa198a3ded56a0dd054cf225bfb6b10968d1da3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720418"
---
# <a name="idebugreference2getreferenceinfo"></a>IDebugReference2::GetReferenceInfo
Získá [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) strukturu, která popisuje odkaz. Vyhrazeno pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetReferenceInfo ( 
   DEBUGREF_INFO_FLAGS   dwFields,
   DWORD                 nRadix,
   DWORD                 dwTimeout,
   IDebugReference2**    rgpArgs,
   DWORD                 dwArgCount,
   DEBUG_REFERENCE_INFO* pReferenceInfo
);
```

```csharp
int GetReferenceInfo ( 
   enum_DEBUGREF_INFO_FLAGS  dwFields,
   uint                      nRadix,
   uint                      dwTimeout,
   IDebugReference2[]        rgpArgs,
   uint                      dwArgCount,
   DEBUG_REFERENCE_INFO[]    pReferenceInfo
);
```

## <a name="parameters"></a>Parametry
`dwFields`\
[v] Kombinace příznaků z [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md) výčtu, které určují pole, která mají být vyplněna ve struktuře [DEBUG_REFERENCE_INFO.](../../../extensibility/debugger/reference/debug-reference-info.md)

`nRadix`\
[v] Radix, který se použije při formátování všech číselných informací.

`dwTimeout`\
[v] Maximální doba v milisekundách čekání před návratem z této metody. Slouží `INFINITE` k čekání na neurčito.

`rgpArgs`\
[v] Pole [iDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) objekty. Vyhrazeno pro budoucí použití; nastavena na hodnotu null.

`dwArgCount`\
[v] Počet argumentů odkazu v `rgpArgs` poli. Vyhrazeno pro budoucí použití; nastavena na 0.

`pReferenceInfo`\
[out] Struktura [DEBUG_REFERENCE_INFO,](../../../extensibility/debugger/reference/debug-reference-info.md) která je vyplněna s popisem vlastnosti.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
- [DEBUGREF_INFO_FLAGS](../../../extensibility/debugger/reference/debugref-info-flags.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
