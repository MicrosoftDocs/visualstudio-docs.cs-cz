---
title: UnInit – | Microsoft Docs
description: Pomocí metody UnInit() VsgDbg můžete dokončit a zavřít soubor protokolu grafiky a volné prostředky protokolování.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb87d210512a3f914384adb99d81695340b1ed5
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232476"
---
# <a name="uninit"></a>UnInit
Finalizuje soubor protokolu grafiky, zavře ho a uchová prostředky, které byly použity při aktivním zaznamenávání informací grafiky aplikací.

## <a name="syntax"></a>Syntax

```C++
void UnInit();
```

## <a name="remarks"></a>Poznámky
 `UnInit` je volána automaticky při zničení `VsgDbg` instance třídy. Pokud `VsgDbg` instance aktivně nenaznamuje informace grafiky, nemá to žádný vliv.

 Po zavolání instance třídy je možné vytvořit nový soubor protokolu grafiky voláním `UnInit` `VsgDbg` a `Init` finalizován voláním `UnInit` . Můžete to opakovat tolikrát, kolikrát chcete použít stejnou instanci k vytvoření několika nezávislých souborů `VsgDbg` protokolu grafiky.

## <a name="see-also"></a>Viz také
- [Init](init.md)