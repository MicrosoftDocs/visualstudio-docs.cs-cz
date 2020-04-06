---
title: IDebugObject2::GetBackingFieldForProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::GetBackingFieldForProperty
helpviewer_keywords:
- IDebugObject2::GetBackingFieldForProperty method
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: b5b9fed9b071f34c119c8e4a5af12c1df7990f4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726239"
---
# <a name="idebugobject2getbackingfieldforproperty"></a>IDebugObject2::GetBackingFieldForProperty
Získá pole nebo proměnnou (pokud existuje), které mohou být podporu vlastnost reprezentované tímto objektem.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetBackingFieldForProperty(
   IDebugObject2** ppObject
);
```

```csharp
int GetBackingFieldForProperty(
   out IDebugObject2 ppObject
);
```

## <a name="parameters"></a>Parametry
`ppObject`\
[out] Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) popisující záložní pole.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Objekt [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) představuje vlastnost třídy spravovaného kódu, to znamená metodu s přistupujícím objektem get a/nebo set. Tyto vlastnosti obecně vyžadují proměnnou, která obsahuje hodnotu, s jakou vlastnost manipuluje. Tato proměnná se označuje jako záložní pole. Pokud pro objekt neexistuje žádné záložní pole, nezapomeňte vrátit hodnotu null: někteří volající nemusí věnovat pozornost vrácené hodnotě, ale `ppObject`místo toho se podívají, zda byla vrácena hodnota null v .

## <a name="see-also"></a>Viz také
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
