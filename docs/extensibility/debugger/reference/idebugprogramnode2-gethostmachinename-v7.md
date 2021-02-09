---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 843e5fdf91fe817681b95422474d3887de5756b0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898618"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7

> [!Note]
> Zastaralé. NEPOUŽÍVEJTE.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetHostMachineName_V7 (
   BSTR* pbstrHostMachineName
);
```

```csharp
int GetHostMachineName_V7 (
   out string pbstrHostMachineName
);
```

## <a name="parameters"></a>Parametry

`pbstrHostMachineName`\
mimo Vrátí název počítače, ve kterém je program spuštěn.

## <a name="return-value"></a>Návratová hodnota

Implementace by měla vždycky vracet `E_NOTIMPL` .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 tato metoda již není používána a měla by vždy vracet `E_NOTIMPL` .

## <a name="see-also"></a>Viz také

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
