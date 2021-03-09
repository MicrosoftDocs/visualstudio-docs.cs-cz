---
title: IManagedAddin::Unload
description: Volá se těsně předtím, než se spravovaný doplněk VSTO uvolní.
ms.date: 02/02/2017
ms.topic: interface
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Unload method
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: e45fd9e6385388b9c6bc32098cf59799618d511b
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102469707"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Volá se těsně předtím, než se spravovaný doplněk VSTO uvolní.

## <a name="syntax"></a>Syntaxe

```csharp
HRESULT Unload();
```

## <a name="return-value"></a>Vrácená hodnota
 Hodnota HRESULT, která označuje, zda byla metoda úspěšně dokončena.

## <a name="remarks"></a>Poznámky
 Tato metoda není volána aktuálními verzemi systém Microsoft Office. Tato metoda je vyhrazena pro budoucí použití.

## <a name="see-also"></a>Viz také
- [Rozhraní IManagedAddin –](../vsto/imanagedaddin-interface.md)
- [IManagedAddin::Load](../vsto/imanagedaddin-load.md)
