---
title: 'Chyba: webový server není správně nakonfigurován | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.remote.projnotconfigured
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: 875ba87f-c372-4126-8fe3-e33931cf26c0
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f5df9fb04849fce94d1a82748f2fc88f9577667
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297441"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Chyba: Webový server není správně nakonfigurován.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mezi možné příčiny této chyby patří:  
  
- Při pokusu o ladění webové aplikace .NET, která byla zkopírována do jiného počítače, ručně přejmenována nebo přesunuta.  
  
- Nemáte dostatečná připojení služby IIS. Další informace o nasazení webu do služby IIS najdete v tématu [Vytvoření](https://docs.microsoft.com/iis/get-started/getting-started-with-iis/create-a-web-site)webu.  
  
- Pokud se pokoušíte ladit aplikaci ASP.NET, přečtěte si téma [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html) , kde najdete pokyny k nasazení do vzdáleného počítače se službou IIS 8 nebo vyšší nebo [vzdáleného ladění ASP.NET na vzdáleném počítači se službou IIS 7,5](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) , kde najdete pokyny k nasazení do vzdáleného počítače se službou IIS 7,5.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
