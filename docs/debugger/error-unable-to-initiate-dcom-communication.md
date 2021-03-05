---
description: Při pokusu o komunikaci místního počítače se vzdáleným počítačem došlo k chybě modelu DCOM.
title: Nelze inicializovat komunikaci modelu DCOM | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: e7cf87815f7d6a09242d2b361db904094fcfcdea
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146441"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Chyba: Nelze inicializovat komunikaci modelu DCOM.
Při pokusu o komunikaci místního počítače se vzdáleným počítačem došlo k chybě modelu DCOM. To je způsobeno bránou firewall na vzdáleném serveru nebo přerušeným ověřováním systému Windows na vzdáleném počítači.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Pokud má vzdálený počítač zapnutou bránu Windows Firewall, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md) , kde najdete pokyny ke konfiguraci brány firewall pro místní ladění.

- Chcete-li obnovit ověřování systému Windows, zkuste oba počítače restartovat. Prověřte protokoly událostí v místních a vzdálených počítačích pro chyby protokolu Kerberos a požádejte správce domény o známé problémy.

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)
