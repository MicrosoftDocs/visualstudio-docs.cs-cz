---
title: IDebugContainerField::EnumFields | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: afc461d52f81afc2c2e7127a90313bea7b9dacf3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733220"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Vytvoří čítač výčtu pro pole kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumFields( 
   FIELD_KIND         dwKindFilter,
   FIELD_MODIFIERS    dwModifiersFilter,
   LPCOLESTR          pszNameFilter,
   NAME_MATCH         nameMatch,
   IEnumDebugFields** ppEnum
);
```

```csharp
int EnumFields(
   enum_ FIELD_KIND      dwKindFilter,
   enum_ FIELD_MODIFIERS dwModifiersFilter,
   string                pszNameFilter,
   NAME_MATCH            nameMatch,
   out IEnumDebugFields  ppEnum
);
```

## <a name="parameters"></a>Parametry
`dwKindFilter`\
[v] Kombinace [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) konstant, které vybírají pole, která mají být vyčíslena. Typy polí mohou popisovat typy úložišť, například třídu nebo primitivní, nebo specifické informace, jako je například místní, parametr nebo "tento" ukazatel.

`dwModifiersFilter`\
[v] Kombinace [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) konstant, které vybírají pole, která mají být vyčíslena. Modifikátory polí mohou být přístupová oprávnění, například veřejné nebo soukromé, nebo informace o úložišti, například virtuální, statické nebo konečné.

`pszNameFilter`\
[v] Název pole, které má být výčtu. To může být nulová hodnota, pokud mají být vrácena všechna pole.

`nameMatch`\
[v] Hodnota z [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) výčtu, který řídí, zda hledání je malá a velká písmena nebo ne.

`ppEnum`\
[out] Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam polí. Vrátí hodnotu null, pokud neexistují žádná pole.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK nebo S_FALSE pokud neexistují žádná pole. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 `dwKindFilter`Parametry `dwModifiersFilter`, `pszNameFilter` a lze kombinovat, například pro výběr všech veřejných virtuálních metod s názvem "MyMethod".

## <a name="see-also"></a>Viz také
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
