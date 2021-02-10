---
title: 'IDebugExceptionEvent2:: CanPassToDebuggee | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
helpviewer_keywords:
- IDebugExceptionEvent2::CanPassToDebuggee
ms.assetid: ae4bbe0a-fbe1-49be-a310-ea64279a434b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 498b928d7e04fc97ec076cb67722b7947686c3a7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99933294"
---
# <a name="idebugexceptionevent2canpasstodebuggee"></a>IDebugExceptionEvent2::CanPassToDebuggee
Určuje, zda ladicí stroj (DE) podporuje možnost předávání této výjimky do programu laděného v okamžiku, kdy provádění pokračuje.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CanPassToDebuggee(
   void
);
```

```csharp
int CanPassToDebuggee();
```

## <a name="return-value"></a>Návratová hodnota
 Vrátí buď `S_OK` (výjimku lze předat programu) nebo `S_FALSE` (výjimku nelze předat).

## <a name="remarks"></a>Poznámky
 DE musí mít výchozí akci pro předání do laděného procesu. Rozhraní IDE může přijmout událost [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) a volat metodu [Continue](../../../extensibility/debugger/reference/idebugprocess3-continue.md) bez volání `CanPassToDebuggee` metody. Proto by měl mít příkaz DE výchozí případ pro předání výjimky.

## <a name="see-also"></a>Viz také
- [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md)
- [Pokračovat](../../../extensibility/debugger/reference/idebugprocess3-continue.md)
