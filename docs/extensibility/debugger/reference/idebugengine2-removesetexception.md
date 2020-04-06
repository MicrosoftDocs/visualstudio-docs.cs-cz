---
title: IDebugEngine2::RemoveSetException | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0e811ce2e387c299ff3655799bf35185c1d2029b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730919"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Odebere zadanou výjimku, takže již není zpracována ladicím strojem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT RemoveSetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int RemoveSetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametry
`pException`\
[v] EXCEPTION_INFO [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) struktura, která popisuje výjimku, která má být odebrána.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Odebraná výjimka musí být dříve nastavena dřívějším voláním metody [SetException.](../../../extensibility/debugger/reference/idebugengine2-setexception.md)

 Chcete-li odebrat všechny výjimky sady najednou, zavolejte metodu [RemoveAllSetExceptions.](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md)

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
