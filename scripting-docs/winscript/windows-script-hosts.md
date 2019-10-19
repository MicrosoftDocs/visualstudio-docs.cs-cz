---
title: Hostitelé Windows Script hostí | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Windows Script Host, implementing hosts
ms.assetid: 9d5f6471-b318-40f3-be01-d9cd0b1cdd47
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8468f578ee44487acd2575e81e01d65969110437
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72568809"
---
# <a name="windows-script-hosts"></a>Moduly Windows Script Host
Při implementaci programu Microsoft Windows Script Host můžete bezpečně předpokládat, že skriptovací stroj volá pouze rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) v kontextu základního vlákna, dokud hostitel provede následující:  
  
- Zvolí základní vlákno (obvykle vlákno, které obsahuje smyčku zpráv).  
  
- Vytvoří instanci skriptovacího stroje v základním vlákně.  
  
- Volá metody skriptovacího stroje pouze ze základního vlákna s výjimkou případů, kdy je to výslovně povoleno, jako v případě [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) a [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md).  
  
- Volá objekt pro odeslání skriptovacího stroje ze základního vlákna.  
  
- Zajistí, že se smyčka zpráv spustí v základním vlákně, pokud je k dispozici popisovač okna.  
  
- Zajišťuje, aby objekty v objektovém modelu hostitele byly pouze zdrojovými událostmi v základním vlákně.  
  
  Tato pravidla jsou automaticky následována všemi hostiteli s jedním vláknem. Výše popsaný model s omezením je záměrně uvolněn dostatečně, aby mohl hostitel přerušit zablokovaný skript voláním [IActiveScript:: InterruptScriptThread](../winscript/reference/iactivescript-interruptscriptthread.md) z jiného vlákna (iniciovaná obslužnou rutinou Ctrl + Break nebo like), nebo pro duplikaci skriptu v nové vlákno s použitím [IActiveScript:: Clone](../winscript/reference/iactivescript-clone.md).  
  
## <a name="remarks"></a>Poznámky  
 Žádná z těchto omezení se nevztahují na hostitele, který se rozhodne implementovat rozhraní [IActiveScriptSite](../winscript/reference/iactivescriptsite.md) s volnými vlákny a objektový model s volnými vlákny. Takový hostitel může používat rozhraní [IActiveScript](../winscript/reference/iactivescript.md) z libovolného vlákna bez omezení.  
  
## <a name="see-also"></a>Viz také:  
 [Skriptovací rozhraní systému Windows](../winscript/windows-script-interfaces.md)