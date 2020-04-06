---
title: IDebugExceptionEvent2::CanPassToDebuggee | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab57f599214cfbd7a1f5fcca15fa104b072d1d48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729868"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Určuje, zda ladicí modul (DE) podporuje možnost předání této výjimky programu, který je laděn při obnovení provádění.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Návratová hodnota
 Vrátí `S_OK` buď (výjimka může být předána programu) nebo `S_FALSE` (výjimka nemůže být předána).

## <a name="remarks"></a>Poznámky
 DE musí mít výchozí akci pro předávání ladicí. IDE může přijímat událost [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) a volat metodu [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) bez volání `CanPassToDebuggee` metody. Proto DE by měl mít výchozí případ pro předávání výjimky na nebo ne.

## <a name="see-also"></a>Viz také
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
