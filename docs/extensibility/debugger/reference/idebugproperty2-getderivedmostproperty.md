---
title: Vlastnost IDebugProperty2::GetDerivedMostProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::GetDerivedMostProperty
helpviewer_keywords:
- IDebugProperty2::GetDerivedMostProperty
ms.assetid: cc86b461-62d1-4340-8209-c65037fd8b02
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2086aded4361049d722ec36ba1d470ed8f7ac6e5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721503"
---
# <a name="idebugproperty2getderivedmostproperty"></a>IDebugProperty2::GetDerivedMostProperty
Získá odvozené nejvíce vlastnost vlastnost.

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
[out] Vrátí objekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který představuje vlastnost nejvíce odvozené.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby. Vrátí, `S_GETDERIVEDMOST_NO_DERIVED_MOST` pokud neexistuje žádná odvozená nejvíce vlastnost načíst.

## <a name="remarks"></a>Poznámky
 Například pokud tato vlastnost popisuje objekt, `ClassRoot` který implementuje, ale `ClassDerived` který je `ClassRoot`ve skutečnosti konkretizaci, která `ClassDerived` je odvozena od , pak tato metoda vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) popisující objekt.

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
