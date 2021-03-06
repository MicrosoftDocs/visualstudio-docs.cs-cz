---
description: Tato metoda změní objekt, který Vizualizér představuje.
title: 'IEEVisualizerDataProvider:: SetObjectForVisualizer | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df5cfd2acef1a2214d4692a49c742c26cd420ffa
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102227226"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Tato metoda změní objekt, který Vizualizér představuje.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametry
`pNewObject`\
pro Objekt, který chcete nastavit.

`error`\
mimo Pokud při nastavování objektu došlo k chybě, tento řetězec obsahuje chybovou zprávu.

`pException`\
mimo Pokud došlo k chybě, tento objekt obsahuje informace o výjimce.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Je až implementátor, který určí, jak se vrátí informace o chybě. Je však možné, že někteří volající mohou zjistit, zda došlo k chybě objektu výjimky, aby bylo známo, že došlo k chybě, takže tato metoda by měla vždy vracet objekt výjimky, pokud došlo k chybě. Řetězec chyby by měl být také dodán pro případ, že ho volající chce využít.

## <a name="see-also"></a>Viz také
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
