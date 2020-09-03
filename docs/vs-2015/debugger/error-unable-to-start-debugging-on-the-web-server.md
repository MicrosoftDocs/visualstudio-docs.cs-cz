---
title: 'Chyba: nelze spustit ladění na webovém serveru | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 0b0cbd7afe90b1dbc091263e3a2594c9ca739e1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185473"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Chyba: Nepodařilo se zahájit ladění na webovém serveru.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Když se pokusíte ladit aplikaci ASP.NET běžící na webovém serveru, může se zobrazit tato chybová zpráva: nelze spustit ladění na webovém serveru.
  
V mnoha případech k této chybě dochází, protože služba IIS není správně nakonfigurovaná.

## <a name="check-your-iis-configuration"></a><a name="vxtbshttpservererrorsthingstocheck"></a> Ověřte konfiguraci služby IIS.

Po přijetí kroků k vyřešení problému, který je zde popsán, a před opakovaným pokusem o ladění může být také nutné resetovat službu IIS. Můžete to udělat tak, že otevřete příkazový řádek správce a zadáte ho `iisreset` nebo ho můžete udělat ve Správci služby IIS. 

* Zastavte a restartujte fondy aplikací a pak to zkuste znovu.

    Je možné, že fond aplikací se zastavil nebo jiná změna konfigurace, kterou jste provedli, může vyžadovat zastavení a restartování fondu aplikací.
    
    > [!NOTE]
    > Pokud fond aplikací zachovává zastavování, může být nutné odinstalovat modul opětovného zápisu adresy URL z ovládacích panelů a pak ho znovu nainstalovat pomocí instalačního programu webové platformy (pracovního procesu). Může se jednat o problém po významném upgradu systému.

* Zkontrolujte konfiguraci fondu aplikací, v případě potřeby ho opravte a pak to zkuste znovu.

    Pokud se přihlašovací údaje hesla změnily, možná je budete muset aktualizovat ve fondu aplikací. I když jste nedávno nainstalovali ASP.NET, může být fond aplikací nakonfigurovaný pro špatnou verzi ASP.NET. Opravte problém a restartujte fond aplikací.
    
* Ověřte, zda má složka webové aplikace správná oprávnění.

    Ujistěte se, že udělujete IIS_IUSRS nebo IUSR (nebo konkrétního uživatele přidruženého k fondu aplikací) práva ke čtení a spouštění pro složku webové aplikace. Opravte problém a restartujte fond aplikací.

* Pokud používáte soubor hostitelů s místními adresami, zkuste místo IP adresy počítače použít adresu zpětné smyčky.

* Zobrazte stránku localhost v prohlížeči.

     Pokud služba IIS není nainstalovaná správně, měli byste při psaní `http://localhost` do prohlížeče získat chyby.
     
     Informace o nasazení do služby IIS najdete v tématu [vzdálené ladění ASP.NET na vzdáleném počítači IIS](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md) nebo pro ASP.NET Core [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Ujistěte se, že je ve službě IIS nainstalovaná správná verze ASP.NET.  Přečtěte si téma [nasazení aplikace v ASP.NET](../debugger/remote-debugging-aspnet-on-a-remote-iis-7-5-computer.md#BKMK_deploy_asp_net) nebo ASP.NET Core [publikování do služby IIS](https://docs.asp.net/en/latest/publishing/iis.html)).

* Vytvořte na serveru základní ASP.NET aplikaci.

     Pokud nemůžete získat aplikaci pro práci s ladicím programem, zkuste vytvořit základní aplikaci ASP.NET místně na serveru a zkusit ladit základní aplikaci. Pokud můžete ladit základní aplikaci, která vám může pomáhat zjistit, jaké jsou rozdíly mezi těmito dvěma konfiguracemi.
  
* Vyřešit chyby ověřování, pokud používáte pouze IP adresu

     Ve výchozím nastavení se IP adresy považují za součást Internetu a ověřování NTLM se přes Internet neprovádí. Pokud je váš web ve službě IIS nakonfigurovaný tak, aby vyžadoval ověření, toto ověření se nezdaří. Chcete-li tento problém vyřešit, můžete místo IP adresy zadat název vzdáleného počítače.
     
## <a name="other-causes"></a>Jiné příčiny

Pokud používáte starší verzi sady Visual Studio:

- Restartujte Visual Studio se zvýšenými oprávněními a zkuste to znovu.

    Chyba v novějších verzích (vyřešených později) vyžaduje zvýšená oprávnění v některých scénářích ladění ASP.NET.
    
- Pokud je spuštěno více instancí sady Visual Studio, znovu otevřete projekt v jedné instanci aplikace Visual Studio a akci opakujte.

## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
