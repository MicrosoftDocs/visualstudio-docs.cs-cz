---
title: AddMessage | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 41a71a69c916bf2fff30b2dee8784d5d9997436b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62896352"
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