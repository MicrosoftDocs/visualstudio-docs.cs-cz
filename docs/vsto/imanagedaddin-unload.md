---
title: IManagedAddin::Unload
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
ms.openlocfilehash: 7a36599259a38d0b9b8eb814a457b3625d593b03
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934595"
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
