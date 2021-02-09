---
title: 'IDebugEngine2:: SetException | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngine2::SetException
helpviewer_keywords:
- IDebugEngine2::SetException
ms.assetid: e6f5ec48-09e8-4b9b-9dc9-55f8d883f1b7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1e2a6dbd5d5700d4d64625490c016da2d04af6d6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878939"
---
# <a name="idebugengine2setexception"></a>IDebugEngine2::SetException
Určuje způsob, jakým ladicí stroj (DE) zpracuje danou výjimku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetException( 
   EXCEPTION_INFO* pException
);
```

```csharp
int SetException( 
   EXCEPTION_INFO[] pException
);
```

## <a name="parameters"></a>Parametry
`pException`\
pro Struktura [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) , která popisuje výjimku a jak ji ladit.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Odpověď DE by mohla být poučena o zastavení programu, který vygeneroval výjimku, při první příležitosti, druhé pravděpodobnosti nebo vůbec ne.

## <a name="see-also"></a>Viz také
- [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)
- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)
