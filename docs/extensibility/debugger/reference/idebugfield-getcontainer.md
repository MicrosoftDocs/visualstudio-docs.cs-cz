---
title: IDebugField::GetContainer | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1217a6f3a62f331fa09d9ed276640ef62cca8d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728904"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Tato metoda získá kontejner pole.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Parametry
`ppContainerField`\
[out] Vrátí kontejner jako reprezentované rozhraním [IDebugContainerField.](../../../extensibility/debugger/reference/idebugcontainerfield.md)

## <a name="return-value"></a>Návratová hodnota
 V případě `S_OK`úspěchu vrátí ; v opačném případě vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud toto pole nemá kontejner, `ppContainerField` vrácené bude hodnota null.

## <a name="see-also"></a>Viz také
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
