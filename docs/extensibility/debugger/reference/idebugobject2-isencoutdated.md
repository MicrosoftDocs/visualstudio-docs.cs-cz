---
title: 'IDebugObject2:: IsEncOutdated | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 94f861e6a45b05c8db1b7e7e76815579f6568c69
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953380"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
Tato metoda určuje, zda je stav úpravy a pokračování tohoto objektu nebo nadřazeného kontejneru zastaralý. Filtr vlastního výrazu neimplementuje tuto metodu a vždy vrátí `E_NOTIMPL` .

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT IsEncOutdated(
   BOOL* pfEncOutdated
);
```

```csharp
int IsEncOutdated(
   out int pfEncOutdated
);
```

## <a name="parameters"></a>Parametry
`pfEncOutdated`\
mimo Nenulová ( `TRUE` ), pokud je stav úpravy a pokračování zastaralé, nula (), `FALSE` Pokud není.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

> [!NOTE]
> Filtr vlastního výrazu by měl vždycky vracet `E_NOTIMPL` .

## <a name="see-also"></a>Viz také
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
