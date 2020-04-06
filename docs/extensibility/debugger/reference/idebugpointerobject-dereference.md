---
title: IDebugPointerObject::Dereference | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerObject::Dereference
helpviewer_keywords:
- IDebugPointerObject::Dereference method
ms.assetid: 196ec2cc-8569-4780-b217-23b24e7f50ca
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fe87d5db40ce663d84c9561e89a84e6fcb1684ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725573"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Získá objekt ukázal.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT DeReference( 
   DWORD          dwIndex,
   IDebugObject** ppObject
);
```

```csharp
int Dereference(
   uint             dwIndex,
   out IDebugObject ppObject
);
```

## <a name="parameters"></a>Parametry
`dwIndex`\
[v] Jednoduchý posun bajtu od začátku objektu, na který je odkazováno.

`ppObject`\
[out] Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) představující objekt, na který je odkazováno, plus posun, pokud existuje.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby. Vrátí E_FAIL pokud tento objekt neukazuje na jiný objekt.

## <a name="remarks"></a>Poznámky
 Objekt, na který je odkazováno, může být primitivní nebo složitější typ, například třída nebo struktura.

## <a name="see-also"></a>Viz také
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
