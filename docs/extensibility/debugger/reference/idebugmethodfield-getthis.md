---
title: 'IDebugMethodField:: getthis | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80727165"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Získá `this` ukazatel ( `Me` v [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) objektu, který obsahuje metodu.

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
mimo Vrátí objekt [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) představující "This" ukazatel.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 V objektově orientovaném jazyce je obvykle implicitní ukazatel na aktuální instanci třídy. To se označuje jako `this` v C#/c + + a jako `Me` v [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Viz také
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
