---
title: IEEVisualizerDataProvider::SetObjectForVisualizer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer
helpviewer_keywords:
- IEEVisualizerDataProvider::SetObjectForVisualizer method
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab63f1e74e0cd3ac64a4d7e7687a9136075b41a7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80718075"
---
# <a name="ieevisualizerdataprovidersetobjectforvisualizer"></a>IEEVisualizerDataProvider::SetObjectForVisualizer
Tato metoda změní objekt, který představuje vizualizér.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetObjectForVisualizer(
   IDebugObject*  pNewObject,
   BSTR*          error,
   IDebugObject** pException
);
```

```csharp
int SetObjectForVisualizer(
   IDebugObject     pNewObject,
   out string       error,
   out IDebugObject pException
);
```

## <a name="parameters"></a>Parametry
`pNewObject`\
[v] Objekt nastavit.

`error`\
[out] Pokud došlo k chybě nastavení objektu, tento řetězec obsahuje chybovou zprávu.

`pException`\
[out] Pokud došlo k chybě, tento objekt obsahuje informace o výjimce.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Je na implementátorovi, aby zjistil, jak jsou vráceny informace o chybě. Je však možné, že někteří volající mohou pouze hledat, pokud byl vrácen objekt výjimky, aby věděl, že došlo k chybě, takže tato metoda by měla vždy vrátit objekt výjimky, pokud došlo k chybě. Chybový řetězec by měl být také zadán v případě, že volající chce využít.

## <a name="see-also"></a>Viz také
- [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
