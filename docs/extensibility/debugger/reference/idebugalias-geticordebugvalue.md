---
description: Načte spravované rozhraní kódu, které představuje hodnotu přidruženou k tomuto aliasu.
title: 'IDebugAlias:: GetICorDebugValue | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ad6cd04d077245d3e893099aab8820ddc8ccf559
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105095911"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Načte spravované rozhraní kódu, které představuje hodnotu přidruženou k tomuto aliasu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parametry
`ppUnk`\
[out] `IUnknown` rozhraní, které představuje hodnotu přidruženou k tomuto aliasu. Toto rozhraní se může dotazovat na `ICorDebugValue` rozhraní.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Tato metoda se vztahuje pouze na spravované hodnoty ( `ICorDebugValue` je rozhraní dostupné v .NET Framework a je definováno v sadě .NET Framework SDK v souboru cordebug. idl).

## <a name="see-also"></a>Viz také
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
