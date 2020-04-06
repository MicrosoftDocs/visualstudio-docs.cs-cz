---
title: IDebugMethodField::EnumArguments | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumArguments
helpviewer_keywords:
- IDebugMethodField::EnumArguments method
ms.assetid: 3ab55488-2437-4ff6-a9ae-78ea6d7b23a8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: adbb1ea4c9172a5f1cee877d04b81aed938bf7a5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727258"
---
# <a name="idebugmethodfieldenumarguments"></a>IDebugMethodField::EnumArguments
Vytvoří čítač pro typ každého argumentu, který je nutný k volání metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumArguments( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumArguments(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam typů argumentů. Vrátí hodnotu null, pokud neexistují žádné argumenty.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné argumenty. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek je [Objekt IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující typy každého parametru. Volání [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) metoda načíst informace o typu každého parametru.

 Pokud je nutný název parametru spolu s typem, zavolejte metodu [EnumParameters.](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumParameters](../../../extensibility/debugger/reference/idebugmethodfield-enumparameters.md)
