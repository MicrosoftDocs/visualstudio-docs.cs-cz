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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734822"
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