---
description: Načte primitivní typ, který je spojen s tímto polem.
title: 'IDebugPrimitiveTypeField:: GetPrimitiveType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetPrimitiveType
- IDebugPrimitiveTypeField::GetPrimitiveType
ms.assetid: a186c922-bbfe-478c-a744-b21eb4672d8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c731ff93dae4bf605933263ffc1ca6bbef45431b
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071711"
---
# <a name="idebugprimitivetypefieldgetprimitivetype"></a>IDebugPrimitiveTypeField::GetPrimitiveType
Načte primitivní typ, který je spojen s tímto polem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetPrimitiveType (
   DWORD* pdwType
);
```

```csharp
int GetPrimitiveType (
   out uint pdwType
);
```

## <a name="parameters"></a>Parametry
`pdwType`\
mimo Hodnota z [výčtu CorElementType –](/dotnet/framework/unmanaged-api/metadata/corelementtype-enumeration) , která představuje primitivní typ.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí `S_FALSE` .

## <a name="see-also"></a>Viz také
- [IDebugPrimitiveTypeField](../../../extensibility/debugger/reference/idebugprimitivetypefield.md)
