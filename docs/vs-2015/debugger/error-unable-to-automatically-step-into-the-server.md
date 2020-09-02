---
title: 'Chyba: nepovedlo se automaticky krokovat na server | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- remote debugging, notification error
ms.assetid: 9a370ccc-d358-429c-b285-9b6c0649bc68
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c8dcb8fa757f1cccf2f3aef6c2520e0c61da0b9f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65682682"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Chyba: Automatické krokování s vnořením do serveru se nezdařilo.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chyba čtení:  
  
 Nelze automaticky krokovat se serverem. Ladicí program nebyl upozorněn před provedením vzdálené procedury.  
  
 K této chybě může dojít, když se pokoušíte Krokovat s vnořením do webové služby (viz [krokování do webové služby XML](https://msdn.microsoft.com/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Tato situace může nastat, kdykoli není [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] správně nastavena.  
  
 Možné příčiny:  
  
- Soubor web.config pro vaši [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikaci nenastaví ladění na "true" v (viz [režim ladění v aplikacích ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).  
  
- [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]Po instalaci sady Visual Studio byla nainstalována verze aplikace. [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] měla by být nainstalována před Visual Studio. Chcete-li tento problém vyřešit, opravte instalaci sady Visual Studio pomocí **ovládacích panelů**systému Windows, **programů a funkcí** .  
  
## <a name="see-also"></a>Viz také  
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
