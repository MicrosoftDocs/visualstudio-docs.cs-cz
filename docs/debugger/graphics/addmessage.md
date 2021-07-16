---
title: AddMessage – | Microsoft Docs
description: Pomocí metody AddMessage třídy VsgDbg přidejte vlastní zprávu do diagnostiky grafiky Head-Up Display (HUD).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1046b7d8a71efb7d628302041a83fb9d20138a29
ms.sourcegitcommit: aeed3eb503d0b282537b073ebae8c028c4fef750
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/15/2021
ms.locfileid: "114232853"
---
# <a name="addmessage"></a>AddMessage
Přidá vlastní zprávu do diagnostiky grafiky *HUD* (head-up display).

## <a name="syntax"></a>Syntaxe

```C++
void AddMessage(
  wchar_t const * szMessage
);
```

#### <a name="parameters"></a>Parametry
 `szMessage` Zpráva, která má být přidána do hud.

## <a name="remarks"></a>Poznámky
 Diagnostika grafiky HUD se zobrazí v levém horním rohu aplikace, která běží pod diagnostikou grafiky. Zobrazuje běhové informace o aplikaci a o zachytávání informací grafiky a zprávy, které jsou přidány voláním této funkce.

 Pokud chcete přidat zprávu do hlavní třídy (HUD), nemusíte aktivně zachytávání grafických informací – to znamená, že zprávu je možné přidat prostřednictvím instance třídy, ale členská funkce Init se nesmí volat `VsgDbg` jako první. [](init.md) Zprávy se zobrazují jenom v hlavní oblasti (HUD) a nezaznamenají se v souboru protokolu grafiky.