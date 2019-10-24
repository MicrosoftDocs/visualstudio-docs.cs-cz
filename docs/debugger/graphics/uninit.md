---
title: Neinicializovat | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ef809b646a0af58e46b8c68dc5a8cf7633692bcc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734822"
---
# <a name="uninit"></a>UnInit
Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.

## <a name="syntax"></a>Syntaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Poznámky
 `UnInit` se nazývá automaticky, když je instance `VsgDbg` třídy zničena. Pokud instance `VsgDbg` aktivně nezaznamená informace o grafice, nemá to žádný vliv.

 Po volání `UnInit` pro instanci `VsgDbg` třídy lze vytvořit nový soubor protokolu grafiky voláním `Init` a finalizován voláním `UnInit`. Tento postup můžete opakovat tolikrát, kolikrát chcete použít stejnou instanci `VsgDbg` k vytvoření několika nezávislých souborů protokolu grafiky.

## <a name="see-also"></a>Viz také:
- [Init](init.md)