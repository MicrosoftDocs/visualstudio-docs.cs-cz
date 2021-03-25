---
description: Tato metoda vrací počet typů argumentů přidružených k tomuto objektu.
title: 'IDebugBinder3:: GetTypeArgumentCount – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetTypeArgumentCount
helpviewer_keywords:
- IDebugBinder3::GetTypeArgumentCount method
ms.assetid: caf68de6-6f7c-4efd-b803-121347a5032e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: aa70a07273a0b4dfdf24219949b411f42b0ddc44
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054488"
---
# <a name="idebugbinder3gettypeargumentcount"></a>IDebugBinder3::GetTypeArgumentCount
Tato metoda vrací počet typů argumentů přidružených k tomuto objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetTypeArgumentCount(
   UINT* uCount
);
```

```csharp
int GetTypeArgumentCount(
   out uint uCount
);
```

## <a name="parameters"></a>Parametry
`uCount`\
mimo Počet typů argumentů přidružených k tomuto objektu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Hodnotu vrácenou touto metodou lze použít k přidělení pole pro použití s metodou [GetTypeArguments –](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md) .

## <a name="see-also"></a>Viz také
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [GetTypeArguments](../../../extensibility/debugger/reference/idebugbinder3-gettypearguments.md)
