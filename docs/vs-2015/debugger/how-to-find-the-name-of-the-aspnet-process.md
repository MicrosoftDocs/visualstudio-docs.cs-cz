---
title: 'Postupy: hledání názvu procesu ASP.NET | Dokumentace Microsoftu'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ad3bea47bcde0da87bd185fac132c95f26ce4b0
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51793240"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Postupy: Hledání názvu procesu ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Připojit ke spuštěnému [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] aplikace, musíte znát název [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu:  
  
- Pokud používáte IIS 6.0 a IIS 7.0, je název w3wp.exe.  
  
- Pokud používáte starší verzi služby IIS, je název aspnet_wp.exe.  
  
  Pro aplikace vytvořené s použitím [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] nebo novější verze [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] kódu můžete jsou umístěny v systému souborů a spustit na serveru test WebDev.WebServer.exe. V takovém případě je nutné připojit k WebDev.WebServer.exe místo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] procesu. Tento scénář platí pouze pro místní ladění.  
  
  Starší aplikace ASP spustit uvnitř inetinfo.exe procesu služby IIS, když jsou spuštěné v rámci procesu.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Chcete-li zjistit, zda kód projektu je umístěn v systému souborů nebo ze služby IIS  
  
1.  V sadě Visual Studio, otevřete **Průzkumníka řešení** Pokud ještě není otevřený.  
  
2.  Vyberte nejvyšší uzel, který obsahuje název aplikace.  
  
3.  Pokud **vlastnosti** název okna obsahuje cestu k souboru, kód aplikace se nachází v systému souborů.  
  
     V opačném případě **vlastnosti** název okna bude obsahovat název webové stránky.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Chcete-li zjistit verzi služby IIS, pod kterým je aplikace spuštěná  
  
1.  Najít **nástroje pro správu** a spustíme ji. V závislosti na operačním systému, může to být ikonu uvnitř **ovládací panely**, nebo, který se zobrazí po kliknutí na položku nabídky **Start**.  
  
     Ve Windows XP **ovládací panely** může být v zobrazení kategorií nebo klasické zobrazení. V zobrazení kategorií, budete muset kliknout na **přepnout do klasického zobrazení** nebo **výkon a údržba** zobrazíte **nástroje pro správu** ikonu.  
  
2.  Z **nástroje pro správu**, spusťte Internetová informační služba. Zobrazí se dialogové okno konzoly MMC.  
  
3.  Pokud existuje více než jednom počítači, které jsou uvedené v levém podokně, vyberte ten, na kterém je umístěn do kódu aplikace.  
  
4.  Verze služby IIS **verze** sloupce v pravém podokně.  
  
## <a name="see-also"></a>Viz také  
 [Předpoklady pro vzdálené ladění webových aplikací](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Požadavky na systém](../debugger/aspnet-debugging-system-requirements.md)   
 [Příprava na ladění technologie ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Ladění webových aplikací a skriptu](../debugger/debugging-web-applications-and-script.md)



