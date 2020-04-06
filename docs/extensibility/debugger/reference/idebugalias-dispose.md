---
title: IDebugAlias::Dispose | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df3a2ecc50063df8f90645b9ccaa72754c3728c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736553"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Označí tento alias pro odebrání.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parametry
 Žádné.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Jakmile je tato metoda volána, alias již není k dispozici.

## <a name="see-also"></a>Viz také
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
