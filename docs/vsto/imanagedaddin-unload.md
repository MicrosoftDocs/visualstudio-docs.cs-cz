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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1ec01ebc32472e315fe2c905ecfd2cfef0f4bbe1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541008"
---
# <a name="imanagedaddinunload"></a>IManagedAddin::Unload
  Volá se těsně předtím, než se spravovaný doplněk VSTO uvolní.

## <a name="syntax"></a>Syntax

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
