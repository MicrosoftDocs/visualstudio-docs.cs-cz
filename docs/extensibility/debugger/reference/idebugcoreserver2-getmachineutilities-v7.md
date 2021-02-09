---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3572390f6e047d0e06b645b6a364971fe4557ea8
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99904051"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Tato metoda načte nástroje počítače pro server.

> [!NOTE]
> Tato metoda je zastaralá: Nepoužívejte ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vždy `E_NOTIMPL` se vrátí, pokud je tato metoda volána). Je uchováván z historických důvodů.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametry
`ppUtil`\
mimo Vrátí `IDebugMDMUtil2_V7` rozhraní, které představuje informace o pomůckách počítače.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL` , která označuje, že metoda není implementována.

## <a name="remarks"></a>Poznámky
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] vždy vrátí `E_NOTIMPL` , pokud je tato metoda volána.

## <a name="see-also"></a>Viz také
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
