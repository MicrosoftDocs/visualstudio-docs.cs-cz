---
description: Tato metoda určuje, zda dodavatel portu může zachovat porty (jejich zápisem na disk) mezi voláními ladicího programu.
title: 'IDebugPortSupplier3:: CanPersistPorts | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 570409a114acbf19697b0eb3ef3e5496fdfde93a
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105071971"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
Tato metoda určuje, zda dodavatel portu může zachovat porty (jejich zápisem na disk) mezi voláními ladicího programu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT CanPersistPorts();
```

```csharp
int CanPersistPorts();
```

## <a name="parameters"></a>Parametry
 Žádné

## <a name="return-value"></a>Návratová hodnota
 `S_OK` Pokud je možné porty zachovat nebo je `S_FALSE` Označit, že porty nelze zachovat.

## <a name="remarks"></a>Poznámky
 Pokud dodavatel portu může zachovat porty, měl by tak učinit, když je zničený, a po opětovném vytvoření instance ho znovu načítat.

## <a name="see-also"></a>Viz také
- [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)
