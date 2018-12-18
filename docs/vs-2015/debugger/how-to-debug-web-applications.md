---
title: 'Postupy: ladění webových aplikací | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Web services, debugging
- ASP.NET Web Forms, debugging
- ASP.NET, debugging Web applications
- debugging ASP.NET Web applications, during development
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d2a5110a6801aafb6eaf98cb4fb4164b045b2408
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793630"
---
# <a name="how-to-debug-web-applications"></a>Postupy: Ladění webových aplikací
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../includes/vstecasp-md.md)] je primární technologie pro vývoj webových aplikací v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Ladicí program poskytuje výkonné nástroje pro ladění [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace místně nebo na vzdáleném serveru. Toto téma popisuje, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] projektu během vývoje. Informace o tom, jak ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] webové aplikace, které už jsou nasazené na provozním serveru, najdete v článku [ladění nasazené webové aplikace](../debugger/debugging-deployed-web-applications.md).  
  
 Chcete-li ladit [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace:  
  
-   Musíte mít požadovaná oprávnění. Další informace najdete v tématu [požadavky na systém](../debugger/aspnet-debugging-system-requirements.md).  
  
-   [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] musí být povoleno ladění v **vlastnosti projektu**.  
  
-   Konfigurační soubor aplikace (Web.config) musí být nastaven na režim ladění. Ladění způsobí, že režim [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] generuje dynamicky generované soubory a umožňují připojení k ladicímu programu [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Tuto hodnotu nastaví automaticky při spuštění ladění, pokud jste vytvořili projekt ze šablony webových projektů.  
  
-   Další informace najdete v tématu [postupy: povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### <a name="to-debug-a-web-application-during-development"></a>Chcete-li ladit webové aplikace během vývoje  
  
1.  Na **ladění** nabídky, klikněte na tlačítko **Start** pro zahájení ladění webové aplikace.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sestavení projektu webové aplikace, nasadí aplikaci v případě potřeby spustí vývojový Server ASP.NET, Jestliže ladíte místně a připojí se k [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] pracovní proces.  
  
2.  Pomocí ladicího programu a zrušte zarážky kroku a provádět jiné operace ladění, jako byste to udělali pro každou aplikaci.  
  
     Další informace najdete v tématu [základy ladicího programu](../debugger/debugger-basics.md).  
  
3.  Na **ladění** nabídky, klikněte na tlačítko **Zastavit ladění** ukončení relace ladění nebo na **souboru** klikněte na tlačítko nabídky v aplikaci Internet Explorer **Zavřít**.  
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md)   
 [Ladění aplikací ASP.NET a AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Postupy: Povolení ladění pro aplikace ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)



