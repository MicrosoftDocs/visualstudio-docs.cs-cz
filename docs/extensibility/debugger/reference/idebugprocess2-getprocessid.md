---
title: 'IDebugProcess2:: GetProcessId – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcess2::GetProcessId
helpviewer_keywords:
- IDebugProcess2::GetProcessId
ms.assetid: d5b6f03c-d49d-4b83-b072-016ac3124f5f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df7b90d4096f651e0f055f9c92343df2a2712fe9
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894891"
---
# <a name="idebugprocess2getprocessid"></a>IDebugProcess2::GetProcessId
Získá identifikátor GUID tohoto procesu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetProcessId(
   GUID* pguidProcessId
);
```

```csharp
int GetProcessId(
   out Guid pguidProcessId
);
```

## <a name="parameters"></a>Parametry
`pguidProcessId`\
mimo Vrátí identifikátor GUID pro tento proces.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Globálně jedinečný identifikátor (GUID) identifikuje tento proces ze všech ostatních procesů spuštěných v systému.

## <a name="see-also"></a>Viz také
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
