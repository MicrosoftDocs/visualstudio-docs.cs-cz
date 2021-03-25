---
description: Odstraní jedinečné ID přidružené k této vlastnosti, což znamená, že volající již nebude stojí k tomu, aby tuto vlastnost identifikoval jednoznačně ze všech ostatních vlastností.
title: IDebugProperty3::D estroyObjectID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty3::DestroyObjectID
helpviewer_keywords:
- IDebugProperty3::DestroyObjectID
ms.assetid: bd08f356-cc67-4717-98c9-c3d00cad2040
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 071af90af5fe22d6f6cfa662458be660edc5d39f
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105064823"
---
# <a name="idebugproperty3destroyobjectid"></a>IDebugProperty3::DestroyObjectID
Odstraní jedinečné ID přidružené k této vlastnosti, což znamená, že volající již nebude stojí k tomu, aby tuto vlastnost identifikoval jednoznačně ze všech ostatních vlastností.

## <a name="syntax"></a>Syntax

```cpp
HRESULT DestroyObjectID(
   void
);
```

```csharp
int DestroyObjectID();
```

## <a name="return-value"></a>Návratová hodnota
 V případě úspěchu vrátí. `S_OK` jinak vrátí kód chyby.

## <a name="remarks"></a>Poznámky
 Pokud ladicí stroj nemusí podporovat jedinečná ID pro vlastnost (protože je již nesleduje jednoznačně interně), může jednoduše vrátit `E_NOTIMPL` tuto metodu.

 Pokud volající chce ověřit, že je tato vlastnost jednoznačně identifikovaná mezi všemi ostatními vlastnostmi, vytvoří se jedinečné identifikátory s voláním metody [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md) .

## <a name="see-also"></a>Viz také
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [CreateObjectID](../../../extensibility/debugger/reference/idebugproperty3-createobjectid.md)
