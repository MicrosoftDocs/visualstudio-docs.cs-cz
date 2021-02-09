---
title: 'IDebugProperty2:: GetDerivedMostProperty | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2f91b00d2f448aea2f187e37813782ce568ad859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916042"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Získá vlastnost s odvozenou vlastností.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDerivedMostProperty ( 
   IDebugProperty2** ppDerivedMost
);
```

```csharp
int GetDerivedMostProperty ( 
   out IDebugProperty2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametry
`ppDerivedMost`\
mimo Vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který představuje vlastnost nejvíce odvozené.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . jinak vrátí kód chyby. Vrátí, `S_GETDERIVEDMOST_NO_DERIVED_MOST` Pokud není k dispozici žádná odvozená vlastnost – k načtení.

## <a name="remarks"></a>Poznámky
 Například pokud tato vlastnost popisuje objekt, který implementuje, `ClassRoot` ale ve skutečnosti je vytvořena instance `ClassDerived` , která je odvozena z `ClassRoot` , pak tato metoda vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) popisující `ClassDerived` objekt.

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
