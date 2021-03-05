---
description: Při pokusu o komunikaci se vzdáleným počítačem s místním počítačem došlo k chybě modelu DCOM.
title: Vzdálený počítač nemohl inicializovat komunikaci modelu DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 86d6c46f338d789d6b113551ac9d99c681290526
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146779"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Chyba: Vzdálený počítač nemohl inicializovat komunikace modelu DCOM.
Při pokusu o komunikaci se vzdáleným počítačem s místním počítačem došlo k chybě modelu DCOM. Místní počítač je počítač, který je

 se spuštěnou sadou Visual Studio. K této chybě může dojít z několika důvodů:

- Místní počítač má zapnutou bránu firewall.

- Ověřování systému Windows ze vzdáleného počítače na místní počítač nepracuje.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Pokud má místní počítač zapnutou bránu Windows Firewall, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md) , kde najdete pokyny ke konfiguraci brány firewall pro místní ladění.

2. Otestujte ověřování systému Windows tím, že se pokusíte otevřít sdílenou složku na místním počítači ze vzdáleného serveru.

3. Chcete-li obnovit ověřování systému Windows, zkuste oba počítače restartovat. Prověřte protokoly událostí v místních a vzdálených počítačích pro chyby protokolu Kerberos a požádejte správce domény o známé problémy.

## <a name="see-also"></a>Viz také
 [Vzdálené ladění](../debugger/remote-debugging.md)
