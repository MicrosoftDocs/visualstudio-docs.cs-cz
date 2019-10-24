---
title: CaptureCurrentFrame | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b9967d776845088e707035c7b1c56855ac80af82
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736139"
---
# <a name="capturecurrentframe"></a>CaptureCurrentFrame
Zachycuje zbytek aktuálního rámce do souboru protokolu grafiky.

## <a name="syntax"></a>Syntaxe

```C++
void CaptureCurrentFrame();
```

## <a name="remarks"></a>Poznámky
 Pokud v současné době probíhá jiné zachycení – například zachytávání, které bylo spuštěno funkcí `BeginCapture` – potom toto zachycení je dokončeno a zaznamenáno do protokolu grafiky jako samostatný rámec. Ihned poté Diagnostika grafiky zahájí zachycení zbývajícího aktuálního rámce, který je také zaznamenán jako samostatný rámec. Konec aktuálního rámce je označen voláním k dispozici.

 Chcete-li zachytit snímek, je nutné připravit aplikaci pro zachycení a záznam informací o grafice – to znamená, že před voláním `CaptureCurrentFrame` je nutné volat metodu [init](init.md) prostřednictvím instance třídy `VsgDbg`.

## <a name="see-also"></a>Viz také:
- [Init](init.md)
- [BeginCapture](begincapture.md)