---
title: Hostitelé Windows Script hostí | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51053dec1f8362aa9eef80e4867d2f92a06454cb
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835326"
---
# <a name="windows-script-hosts"></a>Moduly Windows Script Host
Při implementaci programu Microsoft Windows Script Host můžete bezpečně předpokládat, že skriptovací stroj volá pouze rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) v kontextu základního vlákna, dokud hostitel provede následující:  
  
- Zvolí základní vlákno (obvykle vlákno, které obsahuje smyčku zpráv).  
  
- Vytvoří instanci skriptovacího stroje v základním vlákně.  
  
- Volá metody skriptovacího stroje pouze ze základního vlákna s výjimkou případů, kdy je to výslovně povoleno, jako v případě [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) a [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md).  
  
- Volá objekt pro odeslání skriptovacího stroje ze základního vlákna.  
  
- Zajistí, že se smyčka zpráv spustí v základním vlákně, pokud je k dispozici popisovač okna.  
  
- Zajišťuje, aby objekty v objektovém modelu hostitele byly pouze zdrojovými událostmi v základním vlákně.  
  
  Tato pravidla jsou automaticky následována všemi hostiteli s jedním vláknem. Výše popsané modely s omezením jsou záměrně dostatečně volné, aby mohl hostitel přerušit zablokovaný skript voláním [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) z jiného vlákna (iniciovaná obslužnou rutinou Ctrl + Break nebo like), nebo pro duplikaci skriptu v novém vlákně pomocí [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Poznámky  
 Žádná z těchto omezení se nevztahují na hostitele, který se rozhodne implementovat rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) s volnými vlákny a objektový model s volnými vlákny. Takový hostitel může používat rozhraní [IActiveScript](../winscript/reference/iactivescript.md) z libovolného vlákna bez omezení.  
  
## <a name="see-also"></a>Viz také  
 [Skriptovací rozhraní systému Windows](../winscript/windows-script-interfaces.md)