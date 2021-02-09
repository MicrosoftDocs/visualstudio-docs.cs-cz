---
title: AddMessage | Microsoft Docs
description: Pomocí metody AddMessage třídy VsgDbg přidejte vlastní zprávu do diagnostiky grafiky Head-Up zobrazení (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: d9d51e4415d9707b2df4bb0912290d4f5aa7825f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874636"
---
# <a name="addmessage"></a>AddMessage
Přidá vlastní zprávu do *HUD* diagnostiky grafiky (zobrazení záhlaví).

## <a name="syntax"></a>Syntaxe

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametry
 `szMessage` Zpráva, která se má přidat do HUD

## <a name="remarks"></a>Poznámky
 HUD diagnostiky grafiky se zobrazí v levém horním rohu aplikace, která je spuštěná v rámci diagnostiky grafiky. Zobrazuje běhové informace o aplikaci a o zachycení informací o obrázcích a zprávy, které jsou přidány voláním této funkce.

 Chcete-li přidat zprávu do HUD, nemusíte aktivně zachytáváníovat grafické informace – to znamená, že zprávu lze přidat prostřednictvím instance `VsgDbg` třídy, ale členská funkce [init](init.md) nebude volána jako první. Zprávy se zobrazují pouze v HUD, nejsou zaznamenávány do souboru protokolu grafiky.