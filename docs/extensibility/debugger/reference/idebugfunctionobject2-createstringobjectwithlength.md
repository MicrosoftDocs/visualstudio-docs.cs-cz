---
description: Vytvoří objekt String, který má zadanou délku.
title: 'IDebugFunctionObject2:: CreateStringObjectWithLength | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- CreateStringObjectWithLength
- IDebugFunctionObject2::CreateStringObjectWithLength
ms.assetid: 1f43ec66-1615-4a4c-8b9d-e933f549f96d
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 637b9837cdc351e9f717a773302fbfe6f6588f46
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102149953"
---
# <a name="idebugfunctionobject2createstringobjectwithlength"></a>IDebugFunctionObject2::CreateStringObjectWithLength
Vytvoří objekt String, který má zadanou délku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateStringObjectWithLength (
   LPCOLESTR      pcstrString,
   UINT           uiLength,
   IDebugObject** ppObject
);
```

```csharp
int CreateStringObjectWithLength (
   string           pcstrString,
   uint             uiLength,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`pcstrString`\
pro Řetězcová hodnota objektu String.

`uiLength`\
pro Délka řetězce v bajtech

`ppObject`\
mimo Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , který představuje nově vytvořený objekt řetězce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
