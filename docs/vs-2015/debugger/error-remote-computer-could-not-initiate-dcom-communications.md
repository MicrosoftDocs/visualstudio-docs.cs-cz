---
title: 'Chyba: vzdálený počítač nemohl inicializovat komunikaci modelu DCOM | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.unmarshal_callback_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: bbba0766-2502-4ef1-a75d-bf1f0db39e37
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8ddec2bdec09da1f1175b59c94db31841a1453f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697342"
---
# <a name="error-remote-computer-could-not-initiate-dcom-communications"></a>Chyba: Vzdálený počítač nemohl inicializovat komunikace modelu DCOM.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o komunikaci se vzdáleným počítačem s místním počítačem došlo k chybě modelu DCOM. Místní počítač je počítač, který je  
  
 se spuštěnou sadou Visual Studio. K této chybě může dojít z několika důvodů:  
  
- Místní počítač má zapnutou bránu firewall.  
  
- Ověřování systému Windows ze vzdáleného počítače na místní počítač nepracuje.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Pokud má místní počítač zapnutou bránu Windows Firewall, přečtěte si téma [Nastavení vzdálených nástrojů na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) , kde najdete pokyny ke konfiguraci brány firewall pro místní ladění.  
  
2. Otestujte ověřování systému Windows tím, že se pokusíte otevřít sdílenou složku na místním počítači ze vzdáleného serveru.  
  
3. Chcete-li obnovit ověřování systému Windows, zkuste oba počítače restartovat. Prověřte protokoly událostí v místních a vzdálených počítačích pro chyby protokolu Kerberos a požádejte správce domény o známé problémy.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení nástrojů Remote Tools na zařízení](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
