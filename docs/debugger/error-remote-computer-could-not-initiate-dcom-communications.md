---
title: 'Chyba: Vzdálený počítač nemohl inicializovat komunikace modelu DCOM | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 111c8b010f9d1415e8e9e4e86e1401346f78702d
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471954"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Chyba: Vzdálený počítač nemohl inicializovat komunikace modelu DCOM.
Chyba DCOM došlo k chybě při pokusu o komunikaci s místní počítač vzdáleného počítače. Je na počítač, který je v místním počítači  
  
 spuštění sady Visual Studio. Této chybě může dojít z několika důvodů:  
  
-   Místní počítače je povolena brána firewall.  
  
-   Ověřování systému Windows ze vzdáleného počítače v místním počítači nefunguje.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud místní počítač povolíte bránu Windows Firewall, najdete v části [vzdálené ladění](../debugger/remote-debugging.md) pokyny o tom, jak nakonfigurovat bránu firewall pro místní ladění.  
  
2.  Test ověřování systému Windows tak, že zkusíte otevřete sdílené složky v místním počítači ze vzdáleného serveru.  
  
3.  Chcete-li obnovit ověřování systému Windows, zkuste restartování obou počítačů. Zkontrolujte protokoly událostí na místních i vzdálených počítačích pro chyby protokolu Kerberos a známé problémy, kontaktujte správce domény.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)