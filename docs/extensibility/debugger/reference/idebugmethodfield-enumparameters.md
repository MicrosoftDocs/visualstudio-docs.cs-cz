---
description: Vytvoří enumerátor pro parametry metody.
title: 'IDebugMethodField:: EnumParameters | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::EnumParameters
helpviewer_keywords:
- IDebugMethodField::EnumParameters method
ms.assetid: d77b1197-deb6-4144-8d1b-8b09949ccfac
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51b0ca4d799bc5943a1effd612947b5822730d37
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164991"
---
# <a name="idebugmethodfieldenumparameters"></a>IDebugMethodField::EnumParameters
Vytvoří enumerátor pro parametry metody.

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
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam parametrů metody. v opačném případě vrátí hodnotu null, pokud nejsou zadány žádné parametry.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo vrátí S_FALSE, pokud nejsou zadány žádné parametry. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Každý prvek je objekt [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , který představuje různé typy parametrů. Zavolejte metodu [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) pro každý objekt a určete přesně to, jaký druh parametru objekt představuje.

 Parametr obsahuje název své proměnné i jeho typ. Prvním parametrem metody třídy je obvykle ukazatel this.

 Pokud jsou vyžadovány pouze typy parametrů, zavolejte metodu [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md) .

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [EnumArguments](../../../extensibility/debugger/reference/idebugmethodfield-enumarguments.md)
