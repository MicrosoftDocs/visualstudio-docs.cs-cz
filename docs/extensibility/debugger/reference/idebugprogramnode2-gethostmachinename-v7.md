---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft Docs'
description: Toto je stará, zastaralá metoda pro získání názvu hostitelského počítače používaného před Visual Studio 2005.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 20d62c180848c4875fa3312e0194ebdb467a93ca
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053539"
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
