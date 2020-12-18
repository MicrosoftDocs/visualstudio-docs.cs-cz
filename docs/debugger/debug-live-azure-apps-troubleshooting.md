---
title: Řešení potíží s laděním snímků | Microsoft Docs
ms.custom: ''
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 64ea7f1ea1f665f5180851e42814ad4e8c12c8c5
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668518"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Řešení potíží a známé problémy pro ladění snímků v aplikaci Visual Studio

Pokud kroky popsané v tomto článku problém nevyřeší, vyhledejte problém v [komunitě vývojářů](https://aka.ms/feedback/suggest?space=8) nebo nahlásit nový problém výběrem možnosti **help**  >  **Odeslat zpětnou vazbu**  >  **ohlásit problém** v aplikaci Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problém: "připojit Snapshot Debugger" narazí na chybu stavového kódu HTTP

Pokud se v okně **výstup** zobrazí následující chyba během pokusu o připojení, může se jednat o známý problém uvedený níže. Vyzkoušejte navrhovaná řešení a Pokud potíže přetrvávají, obraťte se na předchozí alias.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Neautorizováno

Tato chyba označuje, že volání REST vydané aplikací Visual Studio do Azure používá neplatné přihlašovací údaje. 

Proveďte tyto kroky:

* Ujistěte se, že váš účet přizpůsobení sady Visual Studio má oprávnění k předplatnému Azure a prostředku, ke kterému se připojujete. Rychlý způsob, jak to zjistit, je ověřit, jestli je prostředek k dispozici v dialogovém okně z okna **ladit**  >  **připojit Snapshot Debugger...**  >  **Prostředek Azure**  >  **Vyberte existující** nebo v Průzkumníku cloudu.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

Pokud jste na svém App Service povolili ověřování/autorizaci (EasyAuth), může dojít k chybě 401 s LaunchAgentAsync v chybové zprávě zásobníku volání. Ujistěte se prosím, že **akce, která se má provést, když je požadavek ověřený** , je nastavený tak, aby **povoloval anonymní žádosti (bez akce)** v Azure Portal a poskytoval authorization.jsv D:\Home\sites\wwwroot s následujícím obsahem. 

```
{
  "routes": [
    {
      "path_prefix": "/",
      "policies": {
        "unauthenticated_action": "RedirectToLoginPage"
      }
    },
    {
      "http_methods": [ "POST" ],
      "path_prefix": "/41C07CED-2E08-4609-9D9F-882468261608/api/agent",
      "policies": {
        "unauthenticated_action": "AllowAnonymous"
      }
    }
  ]
}
```

První postup efektivně zabezpečuje vaši doménu aplikace podobným způsobem jako při **přihlašování pomocí [IdentityProvider]**. Druhá trasa zveřejňuje koncový bod ladicího programu snímků AgentLaunch mimo ověřování, který provádí předdefinovanou akci spuštění agenta diagnostiky ladicího programu snímků *jenom v případě* , že je pro vaši službu App Service povolené rozšíření předinstalovaného serveru ladicího programu snímků. Další podrobnosti o authorization.jso konfiguraci najdete v tématu [autorizační pravidla URL](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html).

### <a name="403-forbidden"></a>(403) zakázáno

Tato chyba označuje, že oprávnění bylo odepřeno. To může být způsobeno mnoha různými problémy.

Proveďte tyto kroky:

* Ověřte, že váš účet Visual studia má platné předplatné Azure s nezbytným oprávněním Role-Based Access Control (RBAC) pro daný prostředek. V případě AppService se podívejte, jestli máte oprávnění k [dotazování](/rest/api/appservice/appserviceplans/get) plánu App Service hostování vaší aplikace.
* Ověřte, zda je časové razítko klientského počítače správné a aktuální. Servery s časovými razítky od více než 15 minut v časovém razítku požadavku obvykle vyvolávají tuto chybu.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="404-not-found"></a>(404) Nenalezeno

Tato chyba označuje, že web nebyl na serveru nalezen.

Proveďte tyto kroky:

* Ověřte, že je web nasazený a spuštěný na prostředku App Service, ke kterému se připojujete.
* Ověřte, že je web k dispozici na adrese https:// \<resource\> . azurewebsites.NET.
* Ověřte, že vaše správně běžící vlastní webová aplikace nevrátí stavový kód 404 při použití v https:// \<resource\> . azurewebsites.NET.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="406-not-acceptable"></a>(406) nepřijatelný

Tato chyba značí, že server nemůže reagovat na sadu typů v hlavičce Accept žádosti.

Proveďte tyto kroky:

* Ověřte, že je web k dispozici na adrese https:// \<resource\> . azurewebsites.NET.
* Ověřte, že se váš web nemigruje na nové instance. Snapshot Debugger používá pojem ARRAffinity pro směrování požadavků na konkrétní instance, které mohou tuto chybu způsobit občas.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="409-conflict"></a>(409) konflikt

Tato chyba označuje, že je požadavek v konfliktu s aktuálním stavem serveru.

Jedná se o známý problém, který nastane, když se uživatel pokusí připojit Snapshot Debugger k AppService, který povolil ApplicationInsights. ApplicationInsights nastaví AppSettings s jiným velikostí písmen než Visual Studio, což by způsobilo tento problém.

::: moniker range=">= vs-2019"
Toto jsme vyřešili v aplikaci Visual Studio 2019.
::: moniker-end

Proveďte tyto kroky:

::: moniker range="vs-2017"

* Ověřte v Azure Portal, že AppSettings pro ladicího programu snímků (SNAPSHOTDEBUGGER_EXTENSION_VERSION) a InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) jsou velká písmena. Pokud ne, aktualizujte nastavení ručně, což vynutí restartování lokality.
::: moniker-end
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="500-internal-server-error"></a>(500) vnitřní chyba serveru

Tato chyba označuje, že lokalita je zcela mimo provoz, nebo Server nemůže zpracovat žádost. Snapshot Debugger pouze funkce spuštěné aplikace. [Application Insights Snapshot Debugger](/azure/azure-monitor/app/snapshot-debugger) poskytuje snapshotting na výjimky a může to být nejlepší nástroj podle vašich potřeb.

### <a name="502-bad-gateway"></a>(502) chybná brána

Tato chyba indikuje problém sítě na straně serveru a může být dočasná.

Proveďte tyto kroky:

* Před opětovným připojením Snapshot Debugger Zkuste počkat několik minut.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

## <a name="issue-snappoint-does-not-turn-on"></a>Problém: snímkovací bod se nezapne

Pokud se zobrazí výstražná ikona ![snímkovací bod výstražná ikona](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Ikona upozornění snímkovací bod") se svým snímkovací bod namísto normální ikony snímkovací bod, není tato snímkovací bod zapnutá.

![Snímkovací bod se nezapíná](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Snímkovací bod se nezapíná")

Proveďte tyto kroky:

1. Ujistěte se, že máte stejnou verzi zdrojového kódu, která se použila k sestavení a nasazení vaší aplikace. Ujistěte se, že načítáte správné symboly pro vaše nasazení. Provedete to tak, že zobrazíte okno **moduly** při ladění snímku a ověříte, že sloupec soubor symbolů zobrazuje soubor. pdb načtený pro modul, který ladíte. Snapshot Debugger se pokusí automaticky stáhnout a používat symboly pro vaše nasazení.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problém: symboly se při otevření snímku nenačte

Pokud se zobrazí následující okno, symboly se nenačte.

![Symboly se nečtou](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symboly se nečtou")

Proveďte tyto kroky:

- Klikněte na tlačítko **změnit nastavení symbolu...** odkaz na tuto stránku. V nastavení **ladění > symbol** Přidejte adresář mezipaměti symbolů. Po nastavení cesty k symbolu restartujte ladění snímků.

   Symboly nebo soubory. pdb, které jsou k dispozici ve vašem projektu, se musí shodovat s vaším nasazením App Service. Většina nasazení (nasazení prostřednictvím sady Visual Studio, CI/CD s Azure Pipelines nebo Kudu atd.) publikuje soubory symbolů spolu s App Service. Nastavení adresáře mezipaměti symbolů umožní aplikaci Visual Studio používat tyto symboly.

   ![Nastavení symbolu](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Nastavení symbolu")

- Případně, pokud vaše organizace používá symbolový server nebo zahodí symboly v jiné cestě, použijte nastavení symbolu pro načtení správných symbolů pro vaše nasazení.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problém: v Průzkumníkovi cloudu nejde zobrazit možnost připojit Snapshot Debugger

Proveďte tyto kroky:

- Ujistěte se, že je nainstalovaná součást Snapshot Debugger. Otevřete Instalační program pro Visual Studio a podívejte se na součást **Snapshot Debugger** v rámci úlohy Azure.
::: moniker range="< vs-2019"
- Ujistěte se, že je vaše aplikace podporovaná. V současné době jsou podporovány pouze aplikace ASP.NET (4.6.1 +) a ASP.NET Core (2.0 +) nasazené do Azure App Services.
::: moniker-end
::: moniker range=">= vs-2019"
- Ujistěte se, že je vaše aplikace podporovaná:
  - Aplikace Azure App Services – ASP.NET spuštěné v .NET Framework 4.6.1 nebo novějším.
  - Azure App Services – ASP.NET Core aplikací běžících na .NET Core 2,0 nebo novějších ve Windows.
  - Azure Virtual Machines (a sada škálování virtuálních počítačů) – aplikace ASP.NET spuštěné v .NET Framework 4.6.1 nebo novějším.
  - Azure Virtual Machines (a sada škálování virtuálních počítačů) – ASP.NET Core aplikace běžící na .NET Core 2,0 nebo novější ve Windows.
  - Služby Azure Kubernetes Services – ASP.NET Core aplikace běžící na .NET Core 2,2 nebo novější v Debian 9.
  - Služby Azure Kubernetes Services – ASP.NET Core aplikace běžící na .NET Core 2,2 nebo novější v alpské 3,8.
  - Služby Azure Kubernetes Services – ASP.NET Core aplikace běžící na .NET Core 2,2 nebo novější v Ubuntu 18,04.
::: moniker-end

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problém: v Diagnostické nástroje se zobrazují pouze omezené snímky

![Omezení snímkovací bod](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Omezení snímkovací bod")

Proveďte tyto kroky:

- Snímky zabírají málo paměti, ale mají poplatek za potvrzení. Pokud Snapshot Debugger zjistí, že je váš server v paměti zatížený, nepřejde na snímky. Již zachycené snímky můžete odstranit zastavením Snapshot Debugger relace a opětovným pokusem.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problém: ladění snímků pomocí více verzí sady Visual Studio obsahuje chyby

Visual Studio 2019 vyžaduje pro Azure App Service novější verzi rozšíření Snapshot Debugger webu.  Tato verze není kompatibilní se starší verzí rozšíření Snapshot Debugger webového serveru, kterou používá Visual Studio 2017.  Tato chyba se zobrazí, pokud se pokusíte připojit Snapshot Debugger v aplikaci Visual Studio 2019 k Azure App Service, která byla dříve Laděna Snapshot Debugger v aplikaci Visual Studio 2017:

![Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2019")

Naopak, pokud použijete Visual Studio 2017 k připojení Snapshot Debugger k Azure App Service, která byla dříve Laděna Snapshot Debugger v aplikaci Visual Studio 2019, zobrazí se následující chyba:

![Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2017")

Pokud to chcete opravit, odstraňte v Azure Portal následující nastavení aplikace a připojte Snapshot Debugger znovu:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problém: Mám problémy s laděním snímků a potřebuji povolit další protokolování.

### <a name="enable-agent-logs"></a>Povolit protokoly agentů

Pokud chcete povolit a zakázat protokolování agenta, otevřete Visual Studio. přejděte na *nástroje>možnosti>Snapshot Debugger>povolit protokolování agenta*. Poznámka: Pokud je povolena taky možnost *Odstranit staré protokoly agentů při spuštění relace* , budou se při každém úspěšném připojení sady Visual Studio odstraňovat předchozí protokoly agentů.

Protokoly agentů najdete v následujících umístěních:

- App Services:
  - Přejděte na web Kudu vašeho App Service (to znamená yourappservice.**SCM**. azurewebsites.NET) a přejděte na konzolu ladění.
  - Protokoly agentů jsou uloženy v následujícím adresáři: D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VIRTUÁLNÍ POČÍTAČ/VMSS:
  - Přihlaste se k VIRTUÁLNÍmu počítači, protokoly agentů jsou uložené takto: C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics \<Version> \ SnapshotDebuggerAgent_ *. txt
- AKS
  - Přejděte do následujícího adresáře:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Povolit protokoly profileru a instrumentace

Protokoly instrumentace najdete v následujících umístěních:

- App Services:
  - Protokolování chyb je automaticky odesláno do D:\Home\LogFiles\eventlog.xml, události jsou označeny pomocí `<Provider Name="Instrumentation Engine" />` nebo "produkčních zarážek".
- VIRTUÁLNÍ POČÍTAČ/VMSS:
  - Přihlaste se ke svému VIRTUÁLNÍmu počítači a otevřete Prohlížeč událostí.
  - Otevřete následující zobrazení: *protokoly Windows>aplikaci*.
  - *Filtrovat aktuální protokol* podle *zdroje událostí* pomocí *zarážek v produkčním* prostředí nebo *modulu instrumentace*.
- AKS
  - Protokolování modulu instrumentace na/TMP/diag/log.txt (nastavení MicrosoftInstrumentationEngine_FileLogPath v souboru Dockerfile)
  - ProductionBreakpoint protokolování na/TMP/diag/shLog.txt

## <a name="known-issues"></a>Známé problémy

- Ladění snímků s více klienty sady Visual Studio proti stejnému App Service není v současné době podporováno.
- Optimalizace Roslyn IL nejsou v ASP.NET Corech projektech plně podporované. U některých ASP.NET Core projektů možná nebudete moci zobrazit některé proměnné nebo použít některé proměnné v podmíněných příkazech.
- Speciální proměnné, jako například *$Function* nebo *$Caller*, nelze vyhodnotit v podmíněných příkazech nebo protokolovacích bodů pro projekty ASP.NET Core.
- Ladění snímků nefunguje na App Services, která má zapnuté [místní ukládání do mezipaměti](/azure/app-service/app-service-local-cache) .
- API Apps ladění snímků se momentálně nepodporuje.

## <a name="site-extension-upgrade"></a>Upgrade rozšíření webu

Ladění a Application Insights snímků závisí na ICorProfiler, který se načte do procesu lokality a způsobuje během upgradu problémy s uzamykáním souborů. Tento proces doporučujeme, abyste zajistili, že váš provozní web nebude mít čas mimo provoz.

- Vytvořte ve svém App Service [slot nasazení](/azure/app-service/web-sites-staged-publishing) a nasaďte svůj web do slotu.
- V aplikaci Visual Studio nebo z Azure Portal Proměňte slot s produkčním prostředím z Průzkumníka cloudu.
- Zastavte lokalitu slotu. Ukončení w3wp.exe procesu ze všech instancí bude trvat několik sekund.
- Upgradujte rozšíření lokality slotu z webu Kudu nebo z Azure Portal (*App Service okno > vývojové nástroje > rozšíření > aktualizace*).
- Spusťte lokalitu slotu. Doporučujeme, abyste web navštívili znovu.
- Zaměňte slot v produkčním prostředí.

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [Ladění živých aplikací ASP.NET pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Ladění živých ASP.NET počítačů Azure Virtual Machines\Virtual pro škálování pomocí Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Ladění Live ASP.NET Azure Kubernetes pomocí Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)
