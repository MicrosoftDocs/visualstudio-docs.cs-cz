---
title: 'Chyba: nelze spustit ladění na webovém serveru | Microsoft Docs'
ms.date: 05/23/2018
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 706a20a00792e7c67b39535322fbd2530f2a2ad3
ms.sourcegitcommit: 8a96a65676fd7a2a03b0803d7eceae65f3fa142b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72588997"
---
# <a name="error-unable-to-start-debugging-on-the-web-server"></a>Chyba: Nepodařilo se zahájit ladění na webovém serveru.

Když se pokusíte ladit aplikaci ASP.NET běžící na webovém serveru, může se zobrazit tato chybová zpráva: `Unable to start debugging on the Web server`.

K této chybě dochází často, protože došlo k chybě nebo změně konfigurace, která vyžaduje aktualizaci fondů aplikací, obnovení IIS nebo obojího. Službu IIS můžete resetovat otevřením příkazového řádku se zvýšenými oprávněními a zadáním `iisreset`.

## <a name="specificerrors"></a>Jaká je podrobná chybová zpráva?

Zpráva `Unable to start debugging on the Web server` je obecná. V řetězci chyby je obvykle obsažena konkrétnější zpráva, která vám může pomoct identifikovat příčinu problému nebo vyhledat přesnější opravu. Tady je několik nejběžnějších chybových zpráv, které se připojují k hlavní chybové zprávě:

- [Služba IIS neobsahuje seznam webů, které se shodují s adresou URL pro spuštění.](#IISlist)
- [Webový server není správně nakonfigurován.](#web_server_config)
- [Nelze se připojit k serveru webserver](#unabletoconnect)
- [Webový server neodpověděl včas.](#webservertimeout)
- [Zdá se, že sledování vzdáleného ladění sady Microsoft Visual Studio (Msvsmon. exe) na vzdáleném počítači neběží.](#msvsmon)
- [Vzdálený server vrátil chybu.](#server_error)
- [Nepovedlo se spustit ladění ASP.NET](#aspnet)
- [Ladicí program se nemůže připojit ke vzdálenému počítači.](#cannot_connect)
- [Běžné chyby konfigurace najdete v nápovědě. Spuštění webové stránky mimo ladicí program může poskytovat další informace.](#see_help)

## <a name="IISlist"></a>Služba IIS neobsahuje seznam webů, které se shodují s adresou URL pro spuštění.

- Restartujte aplikaci Visual Studio jako správce a opakujte ladění. (Některé scénáře ladění ASP.NET vyžadují zvýšená oprávnění.)

    Aplikaci Visual Studio můžete nakonfigurovat tak, aby se vždy spouštěla jako správce, a to tak, že kliknete pravým tlačítkem na ikonu zástupce Visual studia, zvolíte **vlastnosti > Upřesnit**a pak zvolíte, že se má vždycky spustit jako správce.

## <a name="web_server_config"></a>Webový server není správně nakonfigurován.

- Viz [Chyba: webový server není správně nakonfigurován](../debugger/error-the-web-server-is-not-configured-correctly.md).

## <a name="unabletoconnect"></a>Nelze se připojit k serveru webserver

- Používáte Visual Studio a webový server na stejném počítači a ladíte ho pomocí **F5** (místo **připojení k procesu**)? Otevřete vlastnosti projektu a ujistěte se, že je projekt nakonfigurován pro připojení ke správnému webovému serveru a adresu URL pro spuštění. (Otevřené **vlastnosti > serverech a vlastnostech webového >** **> ladit** v závislosti na typu projektu. V případě projektu webových formulářů otevřete **stránky vlastností > možnosti Start > Server**.)

- V opačném případě restartujte fond aplikací a pak obnovte IIS. Další informace najdete v tématu o [kontrole konfigurace služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="webservertimeout"></a>Webový server neodpověděl včas.

- Obnovte IIS a opakujte ladění. K procesu služby IIS může být připojeno více instancí ladicího programu; resetování je ukončí. Další informace najdete v tématu o [kontrole konfigurace služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="msvsmon"></a>Zdá se, že sledování vzdáleného ladění sady Microsoft Visual Studio (Msvsmon. exe) na vzdáleném počítači neběží.

- Pokud provádíte ladění na vzdáleném počítači, ujistěte se, že jste [nainstalovali a spouštíte vzdálený ladicí program](../debugger/remote-debugging.md). Pokud se zpráva zmiňuje o bráně firewall, ujistěte se, že jsou otevřené [správné porty brány firewall](../debugger/remote-debugger-port-assignments.md) , zejména pokud používáte bránu firewall jiného výrobce.
- Pokud používáte soubor hostitelů, ujistěte se, že je správně nakonfigurovaný. Například pokud ladění pomocí klávesy **F5** (místo **připojení k procesu**), musí soubor hostitelů zahrnovat stejnou adresu URL projektu jako ve vlastnostech projektu, **vlastnosti > serverech webového >** nebo **Vlastnosti > ladění**v závislosti na typ projektu.

## <a name="server_error"></a>Vzdálený server vrátil chybu.

V [souboru protokolu služby IIS](https://support.microsoft.com/help/943891/the-http-status-code-in-iis-7-0--iis-7-5--and-iis-8-0) vyhledejte chybové podkódy a další informace a tento [příspěvek blogu](https://blogs.iis.net/tomkmvp/troubleshoot-a-403)služby IIS 7.

Tady jsou některé běžné kódy chyb a několik návrhů.
- (403) zakázáno. Tato chyba obsahuje mnoho možných příčin, proto si prohlédněte soubor protokolu a nastavení zabezpečení služby IIS pro web. Ujistěte se, že web. config serveru obsahuje `debug=true` v elementu compilation. Přesvědčte se, zda má složka webové aplikace správná oprávnění a zda je konfigurace fondu aplikací správná (heslo bylo pravděpodobně změněno). Podívejte [se na téma ověření konfigurace služby IIS](#vxtbshttpservererrorsthingstocheck). Pokud jsou tato nastavení již správná a probíhá ladění místně, ověřte také, že se připojujete ke správnému typu serveru a adrese URL (v části **vlastnosti > webové > servery** nebo **Vlastnosti > ladění**v závislosti na typu projektu).
- (503) Server není k dispozici. Fond aplikací byl pravděpodobně zastaven z důvodu chyby nebo změny konfigurace. Restartujte fond aplikací.
- (404) Nenalezeno. Ujistěte se, že je fond aplikací nakonfigurovaný pro správnou verzi ASP.NET.

## <a name="aspnet"></a>Nepovedlo se spustit ladění ASP.NET

- Restartujte fond aplikací a obnovte službu IIS. Další informace najdete v tématu o [kontrole konfigurace služby IIS](#vxtbshttpservererrorsthingstocheck).
- Pokud provádíte přepsání adresy URL, otestujte základní soubor Web. config bez přepsání adresy URL. Podívejte se na **poznámku** o modulu URL přepisu v [konfiguraci služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="cannot_connect"></a>Ladicí program se nemůže připojit ke vzdálenému počítači.

Pokud provádíte ladění lokálně, otevřete vlastnosti projektu v aplikaci Visual Studio a ujistěte se, že je projekt nakonfigurován pro připojení ke správnému webovému serveru a adrese URL. (Otevřené **vlastnosti > servery nebo vlastnosti webového >** **> ladění** v závislosti na typu projektu.)

K této chybě může dojít při ladění místně, protože Visual Studio je 32 aplikace, takže používá 64 verzi vzdáleného ladicího programu k ladění 64 bitů aplikací. Zkontrolujte fond aplikací ve službě IIS a ujistěte se, že je **možnost povolit 32-bitové aplikace** nastavená na `true`, restartujte službu IIS a zkuste to znovu.

Také Pokud používáte soubor hostitelů, ujistěte se, že je správně nakonfigurován. Například soubor hostitelů musí zahrnovat stejnou adresu URL projektu jako ve vlastnostech projektu, **vlastnosti > serverech webového >** nebo **Vlastnosti > ladění**v závislosti na typu projektu.

## <a name="see_help"></a>Běžné chyby konfigurace najdete v nápovědě. Spuštění webové stránky mimo ladicí program může poskytovat další informace.

- Používáte aplikaci Visual Studio a webový server na stejném počítači? Otevřete vlastnosti projektu a ujistěte se, že je projekt nakonfigurován pro připojení ke správnému webovému serveru a adresu URL pro spuštění. (Otevřené **vlastnosti > servery nebo vlastnosti webového >** **> ladění** v závislosti na typu projektu.)

- Pokud to nefunguje nebo když ladíte vzdáleně, postupujte podle kroků v [podrobnostech konfigurace služby IIS](#vxtbshttpservererrorsthingstocheck).

## <a name="vxtbshttpservererrorsthingstocheck"></a>Ověřte konfiguraci služby IIS.

Po provedení kroků popsaných tady můžete problém vyřešit a před opakovaným pokusem o ladění může být potřeba resetovat službu IIS. Můžete to udělat tak, že otevřete příkazový řádek se zvýšenými oprávněními a zadáte `iisreset`.

* Zastavte a restartujte fondy aplikací IIS a pak to zkuste znovu.

    Fond aplikací byl pravděpodobně ukončen v důsledku chyby. Nebo jiná změna konfigurace, kterou jste provedli, může vyžadovat zastavení a restartování fondu aplikací.

    > [!NOTE]
    > Pokud fond aplikací zachovává zastavování, může být nutné odinstalovat modul přepisování adresy URL z ovládacích panelů. Můžete ji znovu nainstalovat pomocí instalačního programu webové platformy (WebPI). K tomuto problému může dojít po významném upgradu systému.

* Zkontrolujte konfiguraci fondu aplikací, v případě potřeby ho opravte a pak to zkuste znovu.

    Fond aplikací může být nakonfigurovaný pro verzi ASP.NET, která neodpovídá vašemu projektu sady Visual Studio. Aktualizujte verzi ASP.NET ve fondu aplikací a restartujte ji. Podrobné informace najdete v tématu [Služba IIS 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45).

    I když se změní přihlašovací údaje hesla, možná je budete muset aktualizovat ve fondu aplikací nebo na webu.  V části fond aplikací aktualizujte přihlašovací údaje v **rozšířeném nastavení > model procesu > identita**. U webu aktualizujte přihlašovací údaje v **nastavení základní > připojit jako...** . Restartujte fond aplikací.

* Ověřte, zda má složka webové aplikace správná oprávnění.

    Ujistěte se, že udělíte IIS_IUSRS, IUSR nebo konkrétního uživatele přidruženého k oprávněním ke čtení a spouštění [fondu aplikací](/iis/manage/configuring-security/application-pool-identities) pro složku webové aplikace. Opravte problém a restartujte fond aplikací.

* Ujistěte se, že je ve službě IIS nainstalovaná správná verze ASP.NET.

    Tyto potíže mohou způsobovat neshodné verze ASP.NET ve službě IIS a v projektu sady Visual Studio. Možná budete muset nastavit verzi architektury v souboru Web. config. K instalaci ASP.NET ve službě IIS použijte [instalační program webové platformy (WebPI)](https://www.microsoft.com/web/downloads/platform.aspx). Přečtěte si také téma [IIS 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) nebo, pro ASP.NET Core [hostitele ve Windows se službou IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Vyřešit chyby ověřování, pokud používáte pouze IP adresu

     Ve výchozím nastavení se IP adresy považují za součást Internetu a ověřování NTLM se přes Internet neprovádí. Pokud je váš web ve službě IIS nakonfigurovaný tak, aby vyžadoval ověření, toto ověření se nepovede. Chcete-li tento problém vyřešit, můžete místo IP adresy zadat název vzdáleného počítače.

## <a name="other-causes"></a>Jiné příčiny

Pokud konfigurace služby IIS problém nezpůsobuje, zkuste provést následující kroky:

- Restartujte Visual Studio s oprávněními správce a zkuste to znovu.

    Některé scénáře ladění ASP.NET, jako je například použití Nasazení webu, vyžadují zvýšená oprávnění pro Visual Studio.

- Pokud je spuštěno více instancí sady Visual Studio, znovu otevřete projekt v jedné instanci aplikace Visual Studio (s oprávněními správce) a zkuste to znovu.

- Pokud používáte soubor hostitelů s místními adresami, zkuste místo IP adresy počítače použít adresu zpětné smyčky.

    Pokud nepoužíváte místní adresy, ujistěte se, že váš soubor hostitelů obsahuje stejnou adresu URL projektu jako ve vlastnostech projektu, **vlastnosti > serverech webového >** nebo **Vlastnosti > ladění**v závislosti na typu projektu.

## <a name="more-troubleshooting-steps"></a>Další kroky pro řešení potíží

* Zobrazte stránku localhost v prohlížeči na serveru.

     Pokud služba IIS není nainstalovaná správně, měli byste při psaní `http://localhost` v prohlížeči získat chyby.

     Další informace o nasazení služby IIS najdete v tématu [iis 8,0 s použitím ASP.NET 3,5 a ASP.NET 4,5](/iis/get-started/whats-new-in-iis-8/iis-80-using-aspnet-35-and-aspnet-45) a, pro ASP.NET Core [hostitele ve Windows se službou IIS](https://docs.asp.net/en/latest/publishing/iis.html).

* Vytvořte na serveru základní aplikaci ASP.NET (nebo použijte základní soubor Web. config).

    Pokud nemůžete získat aplikaci pro práci s ladicím programem, zkuste vytvořit základní aplikaci ASP.NET místně na serveru a zkusit ladit základní aplikaci. (Možná budete chtít použít výchozí šablonu ASP.NET MVC.) Pokud můžete ladit základní aplikaci, která vám může pomáhat zjistit, jaké jsou rozdíly mezi těmito dvěma konfiguracemi. Vyhledejte rozdíly v nastaveních v souboru Web. config, jako jsou například pravidla pro přepis adres URL.

## <a name="see-also"></a>Viz také
- [Ladění webových aplikací: Chyby a řešení potíží](../debugger/debugging-web-applications-errors-and-troubleshooting.md)