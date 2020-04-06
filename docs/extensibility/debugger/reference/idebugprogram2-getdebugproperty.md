---
title: IDebugProgram2::GetDebugProperty | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33bc10aadf25eb95414cc5fd334c572b2f270429
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80722891"
---
# <a name="idebugprogram2getdebugproperty"></a>IDebugProgram2::GetDebugProperty
Získá vlastnosti programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetDebugProperty( 
   IDebugProperty2** ppProperty
);
```

```csharp
int GetDebugProperty( 
   out IDebugProperty2 ppProperty
);
```

## <a name="parameters"></a>Parametry
`ppProperty`\
[out] Vrátí objekt [IDebugProperty2,](../../../extensibility/debugger/reference/idebugproperty2.md) který představuje vlastnosti programu.

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vlastnosti vrácené touto metodou jsou specifické pro program. Pokud program potřebuje vrátit více než jednu vlastnost, pak [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) objekt vrácený touto metodou je kontejner dalších vlastností a volání [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) metoda vrátí seznam všech vlastností.

 Program může vystavit libovolný počet a typ další vlastnosti, které lze popsat prostřednictvím `IDebugProperty2` rozhraní. IDE může zobrazit další vlastnosti programu prostřednictvím uživatelského rozhraní prohlížeče obecné vlastnosti.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
