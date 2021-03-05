---
description: Vytvoří enumerátor pro pole kontejneru.
title: 'IDebugContainerField:: Enumfields – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugContainerField::EnumFields
helpviewer_keywords:
- IDebugContainerField::EnumFields method
ms.assetid: 9e5e681b-ad49-4c62-bd95-4afa11d61a57
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 68ec12cd97318fc41b97c5a7701dff2346524101
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102143165"
---
# <a name="idebugcontainerfieldenumfields"></a>IDebugContainerField::EnumFields
Vytvoří enumerátor pro pole kontejneru.

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
pro Kombinace [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) konstant, které vyberou pole k vytvoření výčtu. Typy polí mohou popsat typy úložišť, jako je například třída nebo primitivní nebo konkrétní informace, jako například místní, parametr nebo "This" ukazatel.

`dwModifiersFilter`\
pro Kombinace [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) konstant, které vyberou pole k vytvoření výčtu. Modifikátory polí můžou být přístupová oprávnění, jako jsou veřejné nebo soukromé, nebo informace o úložišti, jako jsou virtuální, statické nebo konečné.

`pszNameFilter`\
pro Název pole, které se má vyčíslit Pokud mají být vrácena všechna pole, může to být hodnota null.

`nameMatch`\
pro Hodnota z výčtu [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md) , která určuje, zda se při hledání rozlišují malá a velká písmena.

`ppEnum`\
mimo Vrátí objekt [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) představující seznam polí. Vrátí hodnotu null, pokud nejsou žádná pole.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK nebo S_FALSE, pokud nejsou k dispozici žádná pole. V opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 `dwKindFilter`Parametry, `dwModifiersFilter` a `pszNameFilter` mohou být kombinovány, například pro výběr všech veřejných virtuálních metod s názvem "MyMethod".

## <a name="see-also"></a>Viz také
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
- [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
- [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md)
- [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)
- [NAME_MATCH](../../../extensibility/debugger/reference/name-match.md)
