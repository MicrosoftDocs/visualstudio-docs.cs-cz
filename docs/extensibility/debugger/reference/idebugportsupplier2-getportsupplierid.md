---
description: Získá identifikátor dodavatele portu.
title: 'IDebugPortSupplier2:: GetPortSupplierId | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier2::GetPortSupplierId
helpviewer_keywords:
- IDebugPortSupplier2::GetPortSupplierId
ms.assetid: 741d0829-0943-49bf-b56e-61e836043006
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a7fa298074f9942d2cf863a7e0e1e8ad71f86ed5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072101"
---
# <a name="idebugportsupplier2getportsupplierid"></a>IDebugPortSupplier2::GetPortSupplierId
Získá identifikátor dodavatele portu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPortSupplierId( 
   GUID* pguidPortSupplier
);
```

```csharp
HRESULT GetPortSupplierId( 
   out Guid pguidPortSupplier
);
```

## <a name="parameters"></a>Parametry
`pguidPortSupplier`\
mimo Vrátí identifikátor GUID dodavatele portu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md)
