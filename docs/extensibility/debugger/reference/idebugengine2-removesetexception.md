---
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29756b3be6d2c46d39b581dd3db0af61bfaa18f3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878926"
---
# <a name="idebugengine2removesetexception"></a>IDebugEngine2::RemoveSetException
Odstraní určenou výjimku, takže již není zpracována ladicím modulem.

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
pro Struktura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , která popisuje výjimku, která má být odebrána.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Odebraná výjimka musí být dříve nastavena dřívějším voláním metody [SetException](../../../extensibility/debugger/reference/idebugengine2-setexception.md) .

 Chcete-li odebrat všechny výjimky sady najednou, zavolejte metodu [RemoveAllSetExceptions](../../../extensibility/debugger/reference/idebugengine2-removeallsetexceptions.md) .

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
