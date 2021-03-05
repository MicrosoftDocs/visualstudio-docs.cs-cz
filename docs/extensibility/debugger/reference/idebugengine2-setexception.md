---
description: Určuje způsob, jakým ladicí stroj (DE) zpracuje danou výjimku.
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
ms.openlocfilehash: 543cccbbefd12accd75213f255f8e3b677cdea38
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102153934"
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
