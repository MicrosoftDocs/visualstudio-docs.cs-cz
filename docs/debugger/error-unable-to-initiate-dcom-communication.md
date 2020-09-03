---
title: 'Chyba: nelze inicializovat komunikaci modelu DCOM | Microsoft Docs'
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ccd8b30fcba11d89e11227861c4582ff67f3a7e7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460023"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Chyba: Nelze inicializovat komunikaci modelu DCOM.
Při pokusu o komunikaci místního počítače se vzdáleným počítačem došlo k chybě modelu DCOM. To je způsobeno bránou firewall na vzdáleném serveru nebo přerušeným ověřováním systému Windows na vzdáleném počítači.

### <a name="to-correct-this-error"></a>Oprava této chyby

- Pokud má vzdálený počítač zapnutou bránu Windows Firewall, přečtěte si téma [vzdálené ladění](../debugger/remote-debugging.md) , kde najdete pokyny ke konfiguraci brány firewall pro místní ladění.

- Chcete-li obnovit ověřování systému Windows, zkuste oba počítače restartovat. Prověřte protokoly událostí v místních a vzdálených počítačích pro chyby protokolu Kerberos a požádejte správce domény o známé problémy.

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)