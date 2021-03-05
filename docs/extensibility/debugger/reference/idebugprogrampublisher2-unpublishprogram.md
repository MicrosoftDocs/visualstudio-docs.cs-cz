---
description: Vytvoří program, který se nebude ladit.
title: 'IDebugProgramPublisher2:: UnpublishProgram | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2::UnpublishProgram
helpviewer_keywords:
- IDebugProgramPublisher2::UnpublishProgram
ms.assetid: 627e7d38-b2ac-4873-9a40-37ff7f47cd1d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7160b3bd3b954b722828542e8eead4fc6fedebf5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102161258"
---
# <a name="idebugprogrampublisher2unpublishprogram"></a>IDebugProgramPublisher2::UnpublishProgram
Vytvoří program, který se nebude ladit.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT UnpublishProgram(
   IUnknown* pDebuggeeInterface
);
```

```csharp
int UnpublishProgram(
   object pDebuggeeInterface
);
```

## <a name="parameters"></a>Parametry
`pDebuggeeInterface`\
pro `IUnknown` Rozhraní pro program. Jedná se o stejnou hodnotu poskytnutou metodě [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) a jednoznačně identifikuje odebraný program (to znamená, že se používá jako soubor cookie).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Chcete-li zpřístupnit program pro moduly ladění a správce ladění relace, použijte metodu [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md) .

## <a name="see-also"></a>Viz také
- [IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)
- [PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)
