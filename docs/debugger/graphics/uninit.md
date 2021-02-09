---
title: Neinicializovat | Microsoft Docs
description: K finalizaci a zavření souboru protokolu grafiky a k uvolnění prostředků protokolování použijte metodu UnInit () VsgDbg.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 7cead2d7c1c98e4f481e6057c9ab79c8dc908683
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905016"
---
# <a name="uninit"></a>UnInit
Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.

## <a name="syntax"></a>Syntax

```C++
void UnInit();
```

## <a name="remarks"></a>Poznámky
 `UnInit` se nazývá automaticky `VsgDbg` , když je zničena instance třídy. Pokud `VsgDbg` instance aktivně nezaznamenává informace o grafice, nemá to žádný vliv.

 Po zavolání `UnInit` na instanci `VsgDbg` třídy lze nový soubor protokolu grafiky vytvořit voláním `Init` a finalizován voláním `UnInit` . Tento postup můžete opakovat tolikrát, kolikrát chcete stejnou `VsgDbg` instanci použít k vytvoření několika nezávislých souborů protokolu grafiky.

## <a name="see-also"></a>Viz také
- [For](init.md)