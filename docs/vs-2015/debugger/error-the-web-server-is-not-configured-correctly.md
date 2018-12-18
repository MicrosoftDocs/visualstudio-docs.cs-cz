---
title: 'Chyba: Webový server není nakonfigurován správně | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: ff3662b0e2494b740f6b7cc85e39c081b033da31
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758356"
---
# <a name="error-the-web-server-is-not-configured-correctly"></a>Chyba: Webový server není správně nakonfigurován.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Mezi možné příčiny této chyby patří:  
  
-   Došlo k pokusu o ladění aplikace .NET Web, který byl zkopírován do jiného počítače, ručně přejmenovat nebo přesunout.  
  
-   Nemají dostatek připojení služby IIS. Další informace o nasazení webu do služby IIS najdete v tématu [vytvořit webovou stránku](http://www.iis.net/learn/get-started/getting-started-with-iis/create-a-web-site).  
  
-   Pokud se pokoušíte ladit aplikaci ASP.NET, najdete [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html) pokyny k nasazení ke vzdálenému počítači se službou IIS 8 nebo novější, nebo [vzdálené ladění ASP.NET ve vzdáleném počítači7.5službyIIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) pokyny k nasazení na vzdálený počítač se systémem službu IIS 7.5.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



