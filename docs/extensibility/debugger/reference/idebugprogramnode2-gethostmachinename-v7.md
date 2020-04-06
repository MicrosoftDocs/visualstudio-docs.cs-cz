---
title: IDebugProgramNode2::GetHostMachineName_V7 | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a8c328c83ebe52f842b1990debe07aed3fd764c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722080"
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
[out] Vrátí název počítače, ve kterém je program spuštěn.

## <a name="return-value"></a>Návratová hodnota

Implementace by měla `E_NOTIMPL`vždy vrátit .

## <a name="remarks"></a>Poznámky

> [!WARNING]
> Od sady Visual Studio 2005 se tato metoda `E_NOTIMPL`již nepoužívá a měla by vždy vrátit .

## <a name="see-also"></a>Viz také

- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
