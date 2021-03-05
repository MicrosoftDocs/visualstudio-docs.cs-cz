---
description: Získá vlastnosti programu.
title: 'IDebugProgram2:: GetDebugProperty – | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDebugProperty
helpviewer_keywords:
- IDebugProgram2::GetDebugProperty
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0114d0cf51769d6162563f6c60d51a3f031e19e2
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102159949"
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
mimo Vrátí objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) , který představuje vlastnosti programu.

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Vlastnosti vrácené touto metodou jsou specifické pro program. Pokud program potřebuje vrátit více než jednu vlastnost, pak objekt [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) vrácený touto metodou je kontejnerem dalších vlastností a volání metody [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) vrátí seznam všech vlastností.

 Program může vystavit libovolný počet a typ dalších vlastností, které mohou být popsány prostřednictvím `IDebugProperty2` rozhraní. Integrované vývojové prostředí (IDE) může zobrazit další vlastnosti programu prostřednictvím uživatelského rozhraní prohlížeče obecných vlastností.

## <a name="see-also"></a>Viz také
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)
