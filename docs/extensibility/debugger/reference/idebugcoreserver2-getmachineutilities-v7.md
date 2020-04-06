---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733148"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Tato metoda získá nástroje počítače pro server.

> [!NOTE]
> Tato metoda je zastaralá: nepoužívejte (vždy[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vrátí, `E_NOTIMPL` pokud je tato metoda volána). Je zachována z historických důvodů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametry
`ppUtil`\
[out] Vrátí `IDebugMDMUtil2_V7` rozhraní, které představuje informace o nástrojích počítače.

## <a name="return-value"></a>Návratová hodnota
 Vždy `E_NOTIMPL`vrátí , označující, že metoda není implementována.

## <a name="remarks"></a>Poznámky
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]vždy `E_NOTIMPL` vrátí, pokud je tato metoda volána.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
