---
title: 'Chyba: Nelze inicializovat komunikaci modelu DCOM | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.unmarshal_server_failed
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
ms.openlocfilehash: c34de251125b49c8b3d7aebf301468b9b1d0252a
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31471792"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Chyba: Nelze inicializovat komunikaci modelu DCOM.
Při pokusu o komunikaci s vzdálený počítač v místním počítači došlo k chybě DCOM. To je způsobeno brány firewall na vzdálený server nebo přerušená ověřování systému Windows ve vzdáleném počítači.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Pokud vzdálený počítač povolíte bránu Windows Firewall, najdete v části [vzdálené ladění](../debugger/remote-debugging.md) pokyny o tom, jak nakonfigurovat bránu firewall pro místní ladění.  
  
-   Chcete-li obnovit ověřování systému Windows, zkuste restartování obou počítačů. Zkontrolujte protokoly událostí na místních i vzdálených počítačích pro chyby protokolu Kerberos a známé problémy, kontaktujte správce domény.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)