---
title: 'Chyba: nepovedlo se automaticky krokovat na server | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.causality_no_server_response
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, notification error
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 34b298b299bb4911bfe64b362d94c3e90ecfa585
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72736878"
---
# <a name="error-unable-to-automatically-step-into-the-server"></a>Chyba: Automatické krokování s vnořením do serveru se nezdařilo.
Chyba čtení:

 Nelze automaticky krokovat se serverem. Ladicí program nebyl upozorněn před provedením vzdálené procedury.

 K této chybě může dojít, když se pokoušíte Krokovat s vnořením do webové služby (viz [krokování do webové služby XML](https://msdn.microsoft.com/library/8e67de38-bf5f-41cc-a457-1b88ce63d764)). Tato situace může nastat vždy, když [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] není správně nastavená.

 Možné příčiny:

- Soubor Web. config pro vaši aplikaci [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] nenastaví ladění na hodnotu "true" v (viz [režim ladění v aplikacích ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)).

- Po instalaci sady Visual Studio byla nainstalována verze [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]. [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] by se měla nainstalovat před Visual Studio. Chcete-li tento problém vyřešit, opravte instalaci sady Visual Studio pomocí **ovládacího panelu Windows > programy a funkce** .

## <a name="see-also"></a>Viz také:
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)