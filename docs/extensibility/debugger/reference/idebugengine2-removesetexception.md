---
description: Odstraní určenou výjimku, takže již není zpracována ladicím modulem.
title: 'IDebugEngine2:: RemoveSetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::RemoveSetException
helpviewer_keywords:
- IDebugEngine2::RemoveSetException
ms.assetid: bdd25097-0e9d-4218-b417-0497ea48d2e8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b763291fccd39d46b32347d89df1a11e1b3d09f2
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095404"
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
