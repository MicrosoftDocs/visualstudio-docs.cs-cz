---
title: IDebugPointerObject::D ereference | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725573"
---
# <a name="idebugpointerobjectdereference"></a>IDebugPointerObject::Dereference
Načte objekt, na který se odkazuje.

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
pro Byl posunut jednoduchý bajt od začátku objektu, na který ukazuje.

`ppObject`\
mimo Vrátí objekt [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) , který představuje objekt odkazoval na znaménko plus (pokud existuje).

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí S_OK; v opačném případě vrátí kód chyby. Vrátí E_FAIL, pokud tento objekt neukazuje na jiný objekt.

## <a name="remarks"></a>Poznámky
 Objekt, na který ukazuje, může být primitivní nebo složitější typ, jako je třída nebo struktura.

## <a name="see-also"></a>Viz také
- [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md)
