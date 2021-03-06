---
description: Tato metoda vytvoří službu Vizualizátoru.
title: 'IEEVisualizerServiceProvider:: CreateVisualizerService | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService
helpviewer_keywords:
- IEEVisualizerServiceProvider::CreateVisualizerService method
ms.assetid: f366f7c9-358d-46c8-993f-32ff86539833
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6f8695b578b1a069fd8fe8fa2afdd3a7c21ccd92
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105086752"
---
# <a name="ieevisualizerserviceprovidercreatevisualizerservice"></a>IEEVisualizerServiceProvider::CreateVisualizerService
Tato metoda vytvoří službu Vizualizátoru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CreateVisualizerService(
   IDebugBinder*              binder,
   IDebugSymbolProvider*      pSymProv,
   IDebugAddress*             pAddress,
   IEEVisualizerDataProvider* dataProvider,
   IEEVisualizerService**     ppService
);
```

```csharp
int CreateVisualizerService(
   IDebugBinder binder,
   IDebugSymbolProvider      pSymProv,
   IDebugAddress             pAddress,
   IEEVisualizerDataProvider dataProvider,
   out IEEVisualizerService  ppService
);
```

## <a name="parameters"></a>Parametry
`binder`\
pro Objekt [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md) předaný do [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md).

`pSymProv`\
pro Objekt [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md) předaný do `IDebugParsedExpression::EvaluateSync` .

`pAddress`\
pro Objekt [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) předaný do `IDebugParsedExression::EvaluateSync` .

`dataProvider`\
pro Objekt implementující rozhraní [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md) (dodaný vyhodnocovacím filtrem výrazů).

`ppService`\
mimo Vytvořená služba.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 `binder`Parametry, `pSymProv` a `pAddress` byly všechny předány do `IDebugParsedExpression::EvaluateSync` metody. `CreateVisualizerService` má být volána pouze `IDebugParsedExpression::EvaluateSync` jako součást podpory vyhodnocovacího filtru výrazů pro vizualizace typu.

## <a name="see-also"></a>Viz také
- [IEEVisualizerServiceProvider](../../../extensibility/debugger/reference/ieevisualizerserviceprovider.md)
- [EvaluateSync](../../../extensibility/debugger/reference/idebugparsedexpression-evaluatesync.md)
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
