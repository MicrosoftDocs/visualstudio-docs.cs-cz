---
title: 'IDebugReference2:: GetDerivedMostReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2::GetDerivedMostReference
helpviewer_keywords:
- IDebugReference2::GetDerivedMostReference
ms.assetid: 07253b74-7d39-48e0-8e85-ac8dfd919f6e
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ac8321bc571264d050f5f3559e840c3d169096d7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99909685"
---
# <a name="idebugreference2getderivedmostreference"></a>IDebugReference2::GetDerivedMostReference
Získá odkaz na nejvíce odvozeného odkazu. Vyhrazeno pro budoucí použití.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDerivedMostReference( 
   IDebugReference2** ppDerivedMost
);
```

```csharp
int GetDerivedMostReference( 
   out IDebugReference2 ppDerivedMost
);
```

## <a name="parameters"></a>Parametry
`ppDerivedMost`\
mimo Vrátí objekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) , který představuje vlastnost nejvíce odvozené.

## <a name="return-value"></a>Návratová hodnota
 Vždy vrátí hodnotu `E_NOTIMPL`.

## <a name="remarks"></a>Poznámky
 Například pokud tato vlastnost popisuje objekt, který implementuje, `ClassRoot` ale ve skutečnosti je vytvořena instance `ClassDerived` , která je odvozena z `ClassRoot` , pak tato metoda vrátí objekt [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) představující odkaz na `ClassDerived` objekt.

## <a name="see-also"></a>Viz také
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
