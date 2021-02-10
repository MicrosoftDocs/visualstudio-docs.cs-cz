---
title: 'IDebugBinder:: GetFunctionObject | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::GetFunctionObject
helpviewer_keywords:
- IDebugBinder::GetFunctionObject method
ms.assetid: 8fb789df-8f30-420d-8ca5-bb496a6738f1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f7128c97c60b5743ea9759a9449b82e4e909a686
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99939029"
---
# <a name="idebugbindergetfunctionobject"></a>IDebugBinder::GetFunctionObject
Tato metoda načte objekt [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , který slouží k vytvoření parametrů funkce.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetFunctionObject( 
   IDebugFunctionObject **ppFunction
);
```

```csharp
int GetFunctionObject(
   out IDebugFunctionObject ppFunction
);
```

## <a name="parameters"></a>Parametry
`ppFunction`\
mimo Vrátí rozhraní [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) , které se používá k vytvoření parametrů funkce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="see-also"></a>Viz také
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
