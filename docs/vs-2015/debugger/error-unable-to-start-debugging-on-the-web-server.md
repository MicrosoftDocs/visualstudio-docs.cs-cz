---
title: 'Chyba: Nepodařilo se zahájit ladění na webovém serveru | Dokumentace Microsoftu'
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
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- IIS, debugging DLLs
- debugger, Web application errors
- unable to start debugging error
- security [debugger], Web applications
- debugging [Visual Studio], errors
- HTTP servers, debugging error
- security settings, checking for default Web sites
- errors [debugger], unable to start debugging
- debugging ASP.NET Web applications, unable to start debugging error
- remote debugging, errors
ms.assetid: f62e378a-3a99-4f78-9d97-8bb63a4da181
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 168aaff6e7165c0566b198dab22174b14dad9949
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51779291"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Chyba: Nepodařilo se zahájit ladění na webovém serveru.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o ladění aplikace ASP.NET běžící na webovém serveru, se může zobrazit tato chybová zpráva: Nepodařilo se zahájit ladění na webovém serveru.
  
V mnoha případech se této chybě dochází, protože IIS není správně nakonfigurovaný.

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Zkontrolujte konfiguraci služby IIS

Po provedení kroků pro řešení problému podrobné tady a před dalším pokusem o ladění, může být také potřeba resetovat služby IIS. Můžete to udělat tak, že otevřete příkazový řádek správce a zadáním `iisreset`, nebo to můžete provést ve Správci služby IIS. 

* Zastavit a restartovat aplikaci fondech, a opakujte.

    Fond aplikací se možná zastavil nebo jiné se provedené změny konfigurace můžou vyžadovat ukončení a restartování fondu aplikací.
    
    > [!NOTE]
    > Pokud udržuje zastavení fondu aplikací, budete muset z ovládacího panelu odinstalovat modul přepisování adres URL a poté jej znovu nainstalujte na webovou platformu instalačního programu (identitu pracovního procesu). Po upgradu na systém významné to můžou být problémy.

* Zkontrolujte konfiguraci fondu aplikací, opravte ji v případě potřeby a zkuste zopakovat.

    Pokud jste změnili heslo přihlašovacích údajů, budete muset aktualizovat ve fondu aplikací. Také pokud jste nedávno nainstalovali technologie ASP.NET, může být fond aplikací nakonfigurovaný pro nesprávné verze technologie ASP.NET. Tento problém vyřešit a restartuje fond aplikací.
    
* Zkontrolujte, že vaše webové aplikace složka má správná oprávnění.

    Ujistěte se, že poskytnete IIS_IUSRS nebo IUSR (nebo konkrétního uživatele přidružené k fondu aplikací), číst a spouštět práva ke složce webové aplikace. Tento problém vyřešit a restartuje fond aplikací.

* Pokud používáte soubor HOSTITELŮ pomocí místní adresy, použijte adresu zpětné smyčky místo jeho IP adresy.

* Vyvolejte localhost stránku v prohlížeči.

     Pokud služba IIS není správně nainstalovaná, by měl dojde k chybám při zadávání `http://localhost` v prohlížeči.
     
     Informace o nasazení do služby IIS najdete v tématu [vzdálené ladění ASP.NET ve vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) nebo pro ASP.NET Core, [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Ujistěte se, že je nainstalována správná verze technologie ASP.NET ve službě IIS.  Zobrazit [nasadit aplikaci ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) nebo pro ASP.NET Core, [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Vytvořte základní aplikaci v ASP.NET na serveru.

     Pokud to nejde s vaší aplikaci umožní pracovat s ladicím programem, zkuste vytvořit základní aplikaci ASP.NET místně na serveru a zkuste ladit základní aplikaci. Pokud ladíte základní aplikaci, který vám mohou pomoci identifikovat, čím se liší mezi dvěma konfiguracemi.
  
* Řešení chyb při ověřování, pokud používáte jenom IP adresy

     Ve výchozím nastavení IP adresy jsou považovány za součást Internetu a ověřování protokolem NTLM není Hotovo přes Internet. Pokud je váš web konfigurován ve službě IIS tak, aby vyžadovala ověření, toto ověření se nezdaří. Chcete-li tento problém, můžete zadat název vzdáleného počítače místo IP adresy.
     
## <a name="other-causes"></a>Další příčiny

Pokud používáte starší verzi sady Visual Studio:

- Restartujte sadu Visual Studio se zvýšenými oprávněními a zkuste to znovu.

    Chyba ve starších verzích (fixní později) vyžaduje zvýšená oprávnění v některé technologie ASP.NET ladění scénářů.
    
- Pokud běží více instancí sady Visual Studio, znovu otevřete projekt v jedné instanci sady Visual Studio a zkuste to znovu.
   
  
## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



