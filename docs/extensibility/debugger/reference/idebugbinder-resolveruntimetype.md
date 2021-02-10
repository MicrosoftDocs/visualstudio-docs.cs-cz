---
title: 'IDebugBinder:: ResolveRuntimeType | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder::ResolveRuntimeType
helpviewer_keywords:
- IDebugBinder::ResolveRuntimeType method
ms.assetid: 6456ab3e-1c03-4f3c-91f9-16797ab7f5e7
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: dad51c2741296f9d666a352a5e5a6aa0a3e9cf61
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938223"
---
# <a name="idebugbinderresolveruntimetype"></a>IDebugBinder::ResolveRuntimeType
Tato metoda určuje typ běhu objektu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT ResolveRuntimeType( 
   IDebugObject* pObject,
   IDebugField** ppResolved
);
```

```csharp
int ResolveRuntimeType(
   IDebugObject     pObject,
   out IDebugField  ppResolved
);
```

## <a name="parameters"></a>Parametry
`pObject`\
pro [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , který se má vyřešit.

`ppResolved`\
mimo Vrátí typ objektu jako objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Běhový typ objektu není vždy znám v době kompilace. Například pomocí polymorfismus lze argument předat funkci jako základní třídu, jako je například třída Button. Skutečný argument může být odvozenou třídou, jako je například třída přepínačů.

## <a name="see-also"></a>Viz také
- [IDebugBinder](../../../extensibility/debugger/reference/idebugbinder.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
