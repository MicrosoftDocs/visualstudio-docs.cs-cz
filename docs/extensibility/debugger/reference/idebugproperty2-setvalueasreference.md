---
title: 'IDebugProperty2:: SetValueAsReference | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsReference
helpviewer_keywords:
- IDebugProperty2::SetValueAsReference method
ms.assetid: 341b1b89-4ab8-4e1c-abe2-fb955df5c6b0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b2ed6cbf32d807734714f25453e33fe8bdd7fac0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99961791"
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
pro Pole argumentů předávaných metodě setter vlastnosti spravovaného kódu. Pokud metoda setter vlastnosti nepřijímá argumenty nebo pokud tento objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) neodkazuje na takové setter vlastnosti, `rgpArgs` měla by být hodnota null. Tento parametr je obvykle hodnota null.

`dwArgCount`\
pro Počet argumentů v `rgpArgs` poli.

`pValue`\
pro Odkaz ve formě objektu [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) na hodnotu, která má být použita k nastavení této vlastnosti.

`dwTimeout`\
pro Doba, která se má provést při nastavování hodnoty (v milisekundách) Typickou hodnotou je `INFINITE` . To má vliv na dobu, po kterou může jakékoli možné vyhodnocení trvat.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí `S_OK` . v opačném případě vrátí kód chyby, obvykle jeden z následujících:

|Chyba|Popis|
|-----------|-----------------|
|`E_SETVALUEASREFERENCE_NOTSUPPORTED`|Nastavení hodnoty z odkazu není podporováno.|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Hodnotu nelze nastavit, protože tato vlastnost odkazuje na metodu.|
|`E_SETVALUE_VALUE_IS_READONLY`|Hodnota je jen pro čtení a nelze ji nastavit.|
|`E_NOTIMPL`|Metoda není implementována.|

## <a name="see-also"></a>Viz také
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
