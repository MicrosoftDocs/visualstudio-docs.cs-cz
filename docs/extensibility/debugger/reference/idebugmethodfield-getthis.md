---
title: IDebugMethodField::GetThis | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b29252d1586d039084ec1d21f1fc4967aea68baf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727165"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Získá `this` (`Me` [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)]in ) ukazatel objektu obsahující metodu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametry
`ppClass`\
[out] Vrátí objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představující ukazatel "this".

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V jazycích orientovaných na objekt obvykle je implicitní ukazatel na aktuální konkretizace třídy. To to `this` je známé jako v Jazyce C#/C++ a jako `Me` v [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)].

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
