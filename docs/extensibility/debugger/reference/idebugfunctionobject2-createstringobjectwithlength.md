---
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
ms.openlocfilehash: 6dd46d7cc2d142b3c62ab7b1b2b9eb65b92d6754
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921029"
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
