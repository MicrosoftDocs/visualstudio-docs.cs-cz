---
title: IDebugProperty2::SetValueAsReference | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 73d00ccedc6985061448170735e9ebcaac42f530
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721254"
---
# <a name="idebugproperty2setvalueasreference"></a>IDebugProperty2::SetValueAsReference
Nastaví hodnotu této vlastnosti na hodnotu daného odkazu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT SetValueAsReference(
   IDebugReference2** rgpArgs,
   DWORD              dwArgCount,
   IDebugReference2*  pValue,
   DWORD              dwTimeout
);
```

```csharp
int SetValueAsReference(
   IDebugReference2[] rgpArgs,
   uint               dwArgCount,
   IDebugReference2   pValue,
   uint               dwTimeout
);
```

## <a name="parameters"></a>Parametry
`rgpArgs`\
[v] Pole argumentů předat setter vlastnosti spravovaného kódu. Pokud setter vlastnosti nepřijímá argumenty nebo pokud tento objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) neodkazuje na takový setter vlastnosti, `rgpArgs` by měla být hodnota null. Tento parametr je obvykle hodnota null.

`dwArgCount`\
[v] Počet argumentů v `rgpArgs` poli.

`pValue`\
[v] Odkaz ve formě objektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) na hodnotu, která má být nastavena tuto vlastnost.

`dwTimeout`\
[v] Jak dlouho trvat nastavit hodnotu, v milisekundách. Typickou hodnotou je `INFINITE`. To má vliv na dobu, po kterou může trvat případné vyhodnocení.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby, obvykle jednu z následujících možností:

|Chyba|Popis|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Nastavení hodnoty z odkazu není podporováno.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Hodnotu nelze nastavit, protože tato vlastnost odkazuje na metodu.|
|`E_SETVALUE_VALUE_IS_READONLY`|Hodnota je jen pro čtení a nelze ji nastavit.|
|`E_NOTIMPL`|Metoda není implementována.|

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
