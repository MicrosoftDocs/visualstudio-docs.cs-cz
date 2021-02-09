---
title: 'IEnumDebugErrorBreakpoints2:: resetovat | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugErrorBreakpoints2::Reset
helpviewer_keywords:
- IEnumDebugErrorBreakpoints2::Reset
ms.assetid: d5b04bba-a8b9-4141-94fb-250c77f0534c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a40092cab58adda9b5b22f426ca7e82722dc3937
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99896982"
---
# <a name="ienumdebugerrorbreakpoints2reset"></a>IEnumDebugErrorBreakpoints2::Reset
Obnoví výčet na první prvek.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Reset(
   void
);
```

```csharp
int Reset();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Po volání této metody vrátí další volání metody [Next](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2-next.md) první prvek výčtu.

## <a name="see-also"></a>Viz také
- [IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)
