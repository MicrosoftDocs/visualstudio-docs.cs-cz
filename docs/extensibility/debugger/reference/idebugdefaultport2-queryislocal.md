---
description: Tato metoda určuje, zda je tento port na místním počítači.
title: 'IDebugDefaultPort2:: QueryIsLocal | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDefaultPort2::QueryIsLocal
helpviewer_keywords:
- IDebugDefaultPort2::QueryIsLocal
ms.assetid: 1a42e774-c6ed-419a-a0e3-cab5778652ca
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f732de2526aa71698b4c01a636dab541050015a5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102150637"
---
# <a name="idebugdefaultport2queryislocal"></a>IDebugDefaultPort2::QueryIsLocal
Tato metoda určuje, zda je tento port na místním počítači.

## <a name="syntax"></a>Syntax

```cpp
HRESULT QueryIsLocal(
   void
);
```

```csharp
int QueryIsLocal();
```

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK` , zda je tento port místní (na stejném počítači jako volající), nebo `S_FALSE` zda je port na jiném počítači.

## <a name="see-also"></a>Viz také
- [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md)
