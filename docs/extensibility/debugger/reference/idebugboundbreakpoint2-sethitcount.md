---
title: IDebugBoundBreakpoint2::SetHitCount | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBoundBreakpoint2::SetHitCount
helpviewer_keywords:
- SetHitCount method
- IDebugBoundBreakpoint2::SetHitCount method
ms.assetid: 8145d875-26b1-4049-a2a2-e7d3d7f4735f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e82f12b12c9afbc24f9416ec2639a4b9768d8fd0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735412"
---
# <a name="idebugboundbreakpoint2sethitcount"></a>IDebugBoundBreakpoint2::SetHitCount
Nastaví počet přístupů pro vázanou zarážku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetHitCount( 
   DWORD dwHitCount
);
```

```csharp
int SetHitCount( 
   uint dwHitCount
);
```

## <a name="parameters"></a>Parametry
`dwHitCount`\
[v] Počet zásahů nastavený.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `E_BP_DELETED` pokud je nastaven stav vázaného `BPS_DELETED` objektu zarážky (část [BP_STATE](../../../extensibility/debugger/reference/bp-state.md) výčet).

## <a name="remarks"></a>Poznámky
 Počet přístupů je počet, kolikrát tato zarážka byla aktivována během aktuálního spuštění relace.

 Tato metoda je obvykle volána ladicí stroj aktualizovat aktuální počet přístupů na tuto zarážku.

## <a name="see-also"></a>Viz také
- [IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [BP_STATE](../../../extensibility/debugger/reference/bp-state.md)
