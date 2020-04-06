---
title: IDebugPortSupplier3::CanPersistPorts | Dokumenty společnosti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2bf436d788b517300bee9a13b66b0ca3747bcc43
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724458"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Tato metoda určuje, zda dodavatel portu může zachovat porty (zápisem na disk) mezi vyvolání ladicího programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametry
 Žádné.

## <a name="return-value"></a>Návratová hodnota
 `S_OK`pokud porty mohou být `S_FALSE` trvalé, nebo označit, že porty nelze trvalé.

## <a name="remarks"></a>Poznámky
 Pokud dodavatel portu může zachovat porty, by měl tak učinit, když je zničen a potom znovu načíst, když je vytvořena instance znovu.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
