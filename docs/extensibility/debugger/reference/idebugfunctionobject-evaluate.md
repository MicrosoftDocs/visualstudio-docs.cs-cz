---
title: 'IDebugFunctionObject:: Evaluate | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94285bc0ca36d4a55c3cd3a3483f6e20f6914271
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99920976"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Volá funkci a vrátí výslednou hodnotu jako objekt.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
pro Pole objektů [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představujících vstupní parametry. Každý z těchto parametrů byl vytvořen pomocí jedné z `Create` metod v rozhraní [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

`dwParams`\
pro Počet parametrů v `ppParams` poli.

`dwTimeout`\
pro Určuje maximální dobu v milisekundách, po kterou se má čekat, než se vrátí z této metody. Použijte `INFINITE` k čekání na neomezenou dobu.

`ppResult`\
mimo Vrátí [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující hodnotu funkce jako objekt.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda nastaví a spustí volání funkce reprezentované objektem [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md) .

## <a name="see-also"></a>Viz také
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
