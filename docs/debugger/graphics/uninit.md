---
title: Neinicializovat | Microsoft Docs
description: K finalizaci a zavření souboru protokolu grafiky a k uvolnění prostředků protokolování použijte metodu UnInit () VsgDbg.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1f79b39ced4f3285815412b9b231692868e5e00f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2020
ms.locfileid: "96996055"
---
# <a name="uninit"></a>UnInit
Dokončí soubor protokolu grafiky, zavře ho a uvolní prostředky, které se použily v době, kdy aplikace aktivně zapisovala informace o grafice.

## <a name="syntax"></a>Syntaxe

```C++
void UnInit();
```

## <a name="remarks"></a>Poznámky
 `UnInit` se nazývá automaticky `VsgDbg` , když je zničena instance třídy. Pokud `VsgDbg` instance aktivně nezaznamenává informace o grafice, nemá to žádný vliv.

 Po zavolání `UnInit` na instanci `VsgDbg` třídy lze nový soubor protokolu grafiky vytvořit voláním `Init` a finalizován voláním `UnInit` . Tento postup můžete opakovat tolikrát, kolikrát chcete stejnou `VsgDbg` instanci použít k vytvoření několika nezávislých souborů protokolu grafiky.

## <a name="see-also"></a>Viz také
- [For](init.md)