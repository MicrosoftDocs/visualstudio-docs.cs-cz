---
title: IEEVisualizerServiceProvider::CreateVisualizerService | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e05677122b7d4e4eb025a9382ede1509374de894
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80717917"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Tato metoda vytvoří visualizer služby.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parametry
`binder`\
[v] Objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) předaný [hodnotě EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
[v] Objekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) byl `IDebugParsedExpression::EvaluateSync`předán společnosti .

`pAddress`\
[v] Objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) předán `IDebugParsedExression::EvaluateSync`.

`dataProvider`\
[v] Objekt implementující rozhraní [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (dodávaný vyhodnocením výrazu).

`ppService`\
[out] Vytvořená služba.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 `binder`Metodě `pSymProv`byly `pAddress` předány všechny parametry , a parametry. `IDebugParsedExpression::EvaluateSync` `CreateVisualizerService`má být volána `IDebugParsedExpression::EvaluateSync` pouze z jako součást podpory vyhodnocení výrazu pro vizualizéry typu.

## <a name="see-also"></a>Viz také
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
