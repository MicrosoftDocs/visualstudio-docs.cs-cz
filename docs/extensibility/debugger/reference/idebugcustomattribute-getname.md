---
title: Atribut IDebugCustomAttribute::GetName | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetName
helpviewer_keywords:
- IDebugCustomAttribute::GetName
ms.assetid: ba509cc5-5816-4925-a094-4c72d88c360c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 15d435d043d0e3863358628fa12016431a417918
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732770"
---
# <a name="idebugcustomattributegetname"></a>IDebugCustomAttribute::GetName
Získá název vlastní atribut.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetName( 
   BSTR* bstrName
);
```

```csharp
int GetName(
   out string bstrName
);
```

## <a name="parameters"></a>Parametry
`bstrName`\
[out] Vrátí řetězec obsahující název vlastního atributu.

## <a name="return-value"></a>Návratová hodnota
 Pokud je úspěšná, vrátí S_OK; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pojmenovaný vrácený touto metodou odpovídá názvu třídy použité k deklarování atributu. To nemusí přesně odpovídat názvu vlastní třídy atributu sám jako C# umožňuje "Atribut" přípona, která má být vynechána z názvu vlastního atributu při použití v deklaraci.

## <a name="see-also"></a>Viz také
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
