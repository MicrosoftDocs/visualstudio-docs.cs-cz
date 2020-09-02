---
title: 'Chyba: nelze inicializovat komunikaci modelu DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_server_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 2a7b27e6-2526-4f32-bc4d-eaee447f24ec
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: fff1c56915fe4a06d66bdb08ce60219642933b1b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682535"
---
# <a name="error-unable-to-initiate-dcom-communication"></a>Chyba: Nelze inicializovat komunikaci modelu DCOM.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o komunikaci místního počítače se vzdáleným počítačem došlo k chybě modelu DCOM. To je způsobeno bránou firewall na vzdáleném serveru nebo přerušeným ověřováním systému Windows na vzdáleném počítači.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Pokud má vzdálený počítač zapnutou bránu Windows Firewall, přečtěte si téma [Nastavení vzdálených nástrojů na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) , kde najdete pokyny ke konfiguraci brány firewall pro místní ladění.  
  
- Chcete-li obnovit ověřování systému Windows, zkuste oba počítače restartovat. Prověřte protokoly událostí v místních a vzdálených počítačích pro chyby protokolu Kerberos a požádejte správce domény o známé problémy.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)
