---
title: 'Chyba: Nelze spustit ladění na webovém serveru | Microsoft Docs'
ms.custom: ''
ms.date: 05/23/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.http
- vwd.nonadmin.error.
dev_langs:
- CSharp
- VB
- FSharp
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e58f8152d5c927271161bbf9615b1dfe3944e6dd
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31478249"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Chyba: Nepodařilo se zahájit ladění na webovém serveru.

Když se pokusíte ladění aplikace ASP.NET na webovém serveru spuštěna, zobrazí tato chybová zpráva: `Unable to start debugging on the Web server`.

Této chybě dochází často, protože k chybě nebo konfigurace došlo ke změně vyžadující aktualizaci fondů aplikací, resetování služby IIS nebo obojí. Můžete resetovat IIS otevřením příkazového řádku se zvýšenými oprávněními a zadáním `iisreset`. 

## <a name="specificerrors"></a>Co je Podrobná chybová zpráva?

`Unable to start debugging on the Web server` Je obecná zpráva. Obvykle zprávu konkrétnější je zahrnutý v řetězec chyby a které mohou pomoci při identifikaci příčinu problému nebo vyhledejte další přesný opravu. Zde najdete několik běžných chybových zpráv, které se připojí k hlavní chybová zpráva:

- [Služba IIS není uveden web, který odpovídá spuštění adresy url](#IISlist)
- [Webový server není správně nakonfigurován.](#web_server_config)
- [Nelze se připojit k webovém serveru](#unabletoconnect)
- [Webový server neodpovídá včas](#webservertimeout)
- [Microsoft visual studio vzdálené ladění monitor(msvsmon.exe) nezdá se být spuštěn ve vzdáleném počítači](#msvsmon)
- [Vzdálený server vrátil chybu](#server_error)
- [Nelze spustit ladění ASP.NET](#aspnet)
- [Ladicí program nemůže připojit ke vzdálenému počítači](#cannot_connect)
- [V tématu nápovědy pro běžné chyby konfigurace. Spuštěná na webovou stránku mimo ladicí program může poskytnout další informace.](#see_help)

## <a name="IISlist"></a> Služba IIS není uveden web, který odpovídá spuštění adresy url

- Restartujte Visual Studio jako správce a opakujte ladění. (Některé scénáře ladění ASP.NET vyžadují zvýšená oprávnění).

    Chcete-li vždy spustit jako správce kliknutím pravým tlačítkem myši na ikonu zástupce sady Visual Studio, Visual Studio můžete nakonfigurovat výběr **vlastnosti > Upřesnit**a potom se rozhodnete vždy spustit jako správce.

## <a name="web_server_config"></a> Webový server není správně nakonfigurován.

- V tématu [Chyba: webový server není nakonfigurován správně](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a> Nelze se připojit k webovém serveru

- Jste si spuštění sady Visual Studio a webový server na stejném počítači a ladění pomocí **F5** (místo **připojit k procesu**)? Otevřete vlastnosti projektu a ujistěte se, že projekt je konfigurován pro připojení k webovému serveru správná a spustit adresu URL. (Otevřete **vlastnosti > Web > servery** nebo **vlastnosti > ladění** v závislosti na typu vašeho projektu. Pro projekt webové formuláře, otevřete **stránky vlastností > Možnosti spuštění > serveru**.)

- Jinak restartujte fond aplikací a pak restartujte službu IIS. Další informace najdete v tématu [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a> Webový server neodpovídá včas

- Resetování služby IIS a opakujte ladění. Více instancí ladicí program může připojit k procesu služby IIS. provést obnovení ukončí je. Další informace najdete v tématu [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a> Microsoft visual studio vzdálené ladění monitor(msvsmon.exe) nezdá se být spuštěn ve vzdáleném počítači

- Pokud ladíte ve vzdáleném počítači, ujistěte se, máte [nainstalovaná a spuštěná vzdáleného ladicího programu](../debugger/remote-debugging.md). Pokud zpráva uvádí brána firewall, ujistěte se, [opravte porty v bráně firewall](../debugger/remote-debugger-port-assignments.md) jsou otevřené, zvlášť pokud používáte firewall od jiného výrobce.
- Pokud používáte souboru HOSTITELŮ, ujistěte se, zda že je správně nakonfigurována. Například, pokud ladění pomocí **F5** (místo **připojit k procesu**), hostitele soubor musí obsahovat stejnou adresu URL projektu jako vlastnosti projektu, **vlastnosti > Web > servery**  nebo **vlastnosti > ladění**, v závislosti na typu vašeho projektu.

## <a name="server_error"></a> Vzdálený server vrátil chybu

Zkontrolujte vaše [souboru protokolu služby IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) dílčí kódy chyb a další informace a tuto službu IIS 7 [příspěvku na blogu](https://blogs.iis.net/tomkmvp/troubleshoot-a-403).

Kromě toho se tady jsou některé běžné kódy chyb a několik návrhů.
- (403) zakázán. Existuje mnoho možných příčin této chyby, proto zkontrolujte nastavení zabezpečení služby IIS pro webový server a souboru protokolu. Zajistěte, aby web.config serveru zahrnuje `debug=true` v elementu kompilace. Ujistěte se, zda vaše webové aplikace složka má správná oprávnění a konfiguraci fondu aplikací správnost (heslo může mít změnit). V tématu [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck). Pokud tato nastavení jsou správné a jsou místně ladění, taky ověřit, že se připojujete k správný typ serveru a adresu URL (v **vlastnosti > Web > servery** nebo **vlastnosti > ladění**, v závislosti na typu vašeho projektu).
- (503) server není k dispozici. Fond aplikací může mít zastavená kvůli změně chyby nebo konfigurace. Restartujte fond aplikací.
- (404) nebyl nalezen. Ujistěte se, že fond aplikací je nakonfigurován pro správnou verzi technologie ASP.NET.

## <a name="aspnet"></a> Nelze spustit ladění ASP.NET

- Restartujte fond aplikací a obnovení služby IIS. Další informace najdete v tématu [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).
- Při provádění přepíše adresu URL, otestovat základní web.config s přepisů žádné adresy URL. Najdete v článku **Poznámka** o adrese URL přepisování modulu v [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a> Ladicí program nemůže připojit ke vzdálenému počítači

Pokud ladíte místně, této chybě může dojít, protože Visual Studio je 32bitová aplikace, takže používá 64bitové verze vzdáleného ladicího programu k ladění 64bitových aplikací. Otevřete vlastnosti projektu a ujistěte se, že projekt je nakonfigurován pro připojení správné webový server a adresy URL. (Otevřete **vlastnosti > Web > servery** nebo **vlastnosti > ladění** v závislosti na typu vašeho projektu.)

Pokud používáte souboru HOSTITELŮ, ujistěte se také, zda že je správně nakonfigurována. Například soubor HOSTITELŮ musí obsahovat stejnou adresu URL projektu jako vlastnosti projektu, **vlastnosti > Web > servery** nebo **vlastnosti > ladění**, v závislosti na typu vašeho projektu.

## <a name="see_help"></a> V tématu nápovědy pro běžné chyby konfigurace. Spuštěná na webovou stránku mimo ladicí program může poskytnout další informace.

- Pracujete s Visual Studio a webový server na stejném počítači? Otevřete vlastnosti projektu a ujistěte se, že projekt je konfigurován pro připojení k webovému serveru správná a spustit adresu URL. (Otevřete **vlastnosti > Web > servery** nebo **vlastnosti > ladění** v závislosti na typu vašeho projektu.)

- Pokud to nepomůže, nebo vzdáleně ladíte, postupujte podle kroků v [Zkontrolujte konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).

##  <a name="vxtbshttpservererrorsthingstocheck"></a> Zkontrolujte konfiguraci služby IIS

Po převzetí kroky popsané v tomto poli se problém vyřešit a před dalším pokusem o ladění můžete také obnovit službu IIS. Můžete to udělat tak, že otevřete příkazový řádek se zvýšenými oprávněními a zadáním `iisreset`. 

* Zastavte a restartujte fondů aplikací IIS, a opakujte. 

    Fond aplikací může mít zastavit v důsledku chyby. Nebo může vyžadovat další změny konfigurace, která jste provedli, zastavte a restartujte fond aplikací.
    
    > [!NOTE]
    > Pokud udržuje zastavení fondu aplikací, musíte odinstalovat modul přepisování adres URL z ovládacích panelů. Znovu nainstalujte ji pomocí instalačního programu webové platformy (WebPI). Tomuto problému může dojít po upgradu důležité systém.

* Zkontrolujte konfiguraci fondu aplikací, se v případě potřeby opravte a potom opakujte.

    Fond aplikací může být nakonfigurován pro verzi technologie ASP.NET, která neodpovídá projektu sady Visual Studio. Aktualizovat verzi technologie ASP.NET ve fondu aplikací a restartujte ji. Podrobné informace najdete v tématu [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    Navíc pokud se změnila oprávnění hesla, musíte je aktualizovat v fond aplikací nebo Web.  Ve fondu aplikací, aktualizujte přihlašovací údaje v **Upřesnit nastavení > Model procesu > Identity**. Pro webový server, aktualizujte přihlašovací údaje v **základní nastavení > připojte se jako...** . Restartujte fond aplikací.
    
* Zkontrolujte, že složce webové aplikace má správná oprávnění.

    Zkontrolujte poskytnout IIS_IUSRS IUSR, nebo v přidružené konkrétního uživatele [fond aplikací](/iis/manage/configuring-security/application-pool-identities) číst a spouštět oprávnění pro složku webové aplikace. Vyřešte problém a restartujte fond aplikací.

* Ujistěte se, že je nainstalována správná verze technologie ASP.NET ve službě IIS.

    Tento problém může způsobit neodpovídající verze technologie ASP.NET ve službě IIS a v projektu sady Visual Studio. Musíte nastavit framework verze v souboru web.config. Instalace technologie ASP.NET ve službě IIS, použijte [instalačního programu webové platformy (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Další informace naleznete v [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) nebo pro ASP.NET Core [hostitele v systému Windows pomocí služby IIS](https://docs.asp.net/en/latest/publishing/iis.html).
  
* Řešení chyb při ověřování, pokud používáte pouze IP adresa

     Ve výchozím nastavení IP adresy jsou považovány za součást Internetu a ověřování protokolem NTLM není provést přes Internet. Pokud váš webový server je konfigurován ve službě IIS vyžadují ověřování, toto ověřování se nezdaří. Chcete-li tento problém, můžete zadat název vzdáleného počítače místo IP adresy.
     
## <a name="other-causes"></a>Další příčiny

Pokud konfigurace služby IIS není příčinou problému, proveďte následující kroky:

- Restartujte Visual Studio s oprávněními správce a pokus opakujte.

    Některé ASP.NET ladění scénáře, jako je třeba použití nástroje nasazení webu vyžadují zvýšená oprávnění pro Visual Studio.
    
- Pokud používáte systém více instancí sady Visual Studio, otevřete projekt v sadě Visual Studio jedna instance (s oprávněními správce) a akci opakujte.

- Pokud používáte souboru HOSTITELŮ pomocí místní adresy, zkuste použít adresu zpětné smyčky místo počítače IP adresu.

    Pokud nepoužíváte místní adresy, ujistěte se, soubor HOSTITELŮ obsahuje stejnou adresu URL projektu jako vlastnosti projektu, **vlastnosti > Web > servery** nebo **vlastnosti > ladění**, v závislosti na vaší Typ projektu.

## <a name="more-troubleshooting-steps"></a>Další postup řešení potíží

* Vyvolat localhost stránku v prohlížeči na serveru.

     Pokud služba IIS není nainstalována správně, měli byste obdržet chyby při zadávání `http://localhost` v prohlížeči.
     
     Další informace o nasazení do služby IIS najdete v tématu [IIS 8.0 pomocí technologie ASP.NET 3.5 a technologii ASP.NET 4.5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) a pro ASP.NET Core [hostitele v systému Windows pomocí služby IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Vytvořte základní aplikace ASP.NET na serveru (nebo použijte soubor základní web.config).

    Pokud nelze získat aplikace pro práci s ladicím programem, zkuste vytvořit základní aplikace ASP.NET místně na serveru a zkuste ladění základní aplikace. (Můžete chtít použít výchozí šablony ASP.NET MVC.) Pokud ladíte základní aplikaci, která vám mohou pomoci zjistit, co je rozdíly mezi dvě konfigurace. Vyhledejte rozdíly v nastavení v souboru web.config, jako například pravidel přepisování adres URL.

## <a name="see-also"></a>Viz také  
 [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)