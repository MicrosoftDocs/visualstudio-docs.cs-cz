---
title: IDebugMethodField::EnumParameters | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 13df02cf5870e630c4aecb34e9295d218ba7a0eb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727193"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Vytvoří čítač výčtu pro parametry metody.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumParameters( 
   IEnumDebugFields** ppParams
);
```

```csharp
int EnumParameters(
   out IEnumDebugFields ppParams
);
```

## <a name="parameters"></a>Parametry
`ppParams`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam parametrů metody. v opačném případě vrátí hodnotu null, pokud neexistují žádné parametry.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo vrátí S_FALSE pokud neexistují žádné parametry. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek je [Objekt IDebugField](../../../extensibility/debugger/reference/idebugfield.md) představující různé typy parametrů. Volání [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) metoda na každý objekt přesně určit, jaký druh parametru objektu představuje.

 Parametr obsahuje název proměnné i typ. První parametr metody třídy je obvykle ukazatel "this".

 Pokud jsou potřeba pouze typy parametrů, zavolejte metodu [EnumArguments.](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
