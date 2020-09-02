---
title: 'Postupy: hledání názvu procesu ASP.NET | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 53072013c1665687262d30f4a0c2720641c920be
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685960"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Postupy: Hledání názvu procesu ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li se připojit ke spuštěné [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikaci, je nutné znát název [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu:  
  
- Pokud používáte IIS 6,0 nebo IIS 7,0, název je w3wp.exe.  
  
- Pokud používáte starší verzi služby IIS, název je aspnet_wp.exe.  
  
  Pro aplikace sestavené pomocí [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] nebo novější verze [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] může být kód umístěn v systému souborů a spuštěn pod WebDev.WebServer.exe testovacího serveru. V takovém případě je nutné se místo procesu připojit k WebDev.WebServer.exe [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . Tento scénář se vztahuje pouze na místní ladění.  
  
  Starší aplikace ASP běží v procesu IIS inetinfo.exe, když jsou spuštěné vnitroprocesově.  
  
> [!NOTE]
> Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, v nabídce **nástroje** klikněte na položku **Nastavení importu a exportu** . Další informace naleznete v tématu [přizpůsobení nastavení vývoje v aplikaci Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Určení, zda se kód projektu nachází v systému souborů nebo službě IIS  
  
1. V aplikaci Visual Studio otevřete **Průzkumník řešení** , pokud ještě není otevřený.  
  
2. Vyberte nejvyšší uzel, který obsahuje název aplikace.  
  
3. Obsahuje-li název okna **vlastností** cestu k souboru, je kód aplikace umístěn v systému souborů.  
  
     V opačném případě bude název okna **vlastnosti** obsahovat název webu.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Určení verze služby IIS, pod kterou běží aplikace  
  
1. Vyhledejte **Nástroje pro správu** a spusťte je. V závislosti na operačním systému to může být ikona v **Ovládacích panelech**nebo záznam nabídky, který se zobrazí po kliknutí na tlačítko **Spustit**.  
  
     V systému Windows XP lze **Ovládací panely** zobrazit v zobrazení kategorií nebo v klasickém zobrazení. V zobrazení kategorií musíte kliknout na **Přepnout do klasického zobrazení** nebo **výkonu a údržby** , aby se zobrazila ikona **Nástroje pro správu** .  
  
2. V **nástrojích pro správu**spusťte Internetová informační služba. Zobrazí se dialogové okno MMC.  
  
3. Pokud je v levém podokně uveden více než jeden počítač, vyberte ten, na kterém se nachází kód aplikace.  
  
4. Verze služby IIS je ve sloupci **verze** v pravém podokně.  
  
## <a name="see-also"></a>Viz také  
 [Předpoklady pro vzdálené ladění webových aplikací](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)   
 [Příprava na ladění ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md)
