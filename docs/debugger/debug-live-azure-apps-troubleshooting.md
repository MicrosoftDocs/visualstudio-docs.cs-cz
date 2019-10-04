---
title: Řešení potíží při ladění snímků | Dokumentace Microsoftu
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
ms.openlocfilehash: 27df4c097d829a4d28a77b9b1ad96eb389f4096c
ms.sourcegitcommit: dc12a7cb66124596089f01d3e939027ae562ede9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2019
ms.locfileid: "71962930"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Řešení potíží a známé problémy pro ladění snímků v sadě Visual Studio

Pokud kroky popsané v tomto článku problém nevyřeší, vyhledejte problém v [komunitě vývojářů](https://developercommunity.visualstudio.com/spaces/8/index.html) nebo nahlásit nový problém výběrem možnosti **help** > **Odeslat názor** > **ohlásit problém** v aplikaci Visual Studio.

## <a name="issue-attach-snapshot-debugger-encounters-an-http-status-code-error"></a>Problém: Při "připojení Snapshot Debugger" dojde k chybě stavového kódu HTTP

Pokud se v okně **výstup** zobrazí následující chyba během pokusu o připojení, může se jednat o známý problém uvedený níže. Vyzkoušejte navrhovaná řešení a Pokud potíže přetrvávají, obraťte se na předchozí alias.

`[TIMESTAMP] Error --- Unable to Start Snapshot Debugger - Attach Snapshot Debugger failed: System.Net.WebException: The remote server returned an error: (###) XXXXXX`

### <a name="401-unauthorized"></a>(401) Neautorizováno

Tato chyba označuje, že volání REST vydané aplikací Visual Studio do Azure používá neplatné přihlašovací údaje. Tato chyba může způsobit známou chybu v modulu Azure Active Directory Easy OAuth.

Proveďte tyto kroky:

* Ujistěte se, že váš účet přizpůsobení sady Visual Studio má oprávnění k předplatnému Azure a prostředku, ke kterému se připojujete. Rychlý způsob, jak to zjistit, je ověřit, jestli je prostředek k dispozici v dialogovém okně z **ladění** > **připojit Snapshot Debugger...**  > **prostředek Azure** > **Vyberte existující**nebo v Průzkumníku cloudu.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="403-forbidden"></a>(403) zakázáno

Tato chyba označuje, že oprávnění bylo odepřeno. To může být způsobeno mnoha různými problémy.

Proveďte tyto kroky:

* Ověřte, že váš účet sady Visual Studio má platné předplatné Azure s potřebnými oprávněními pro Access Control na základě rolí (RBAC) pro daný prostředek. V případě AppService se podívejte, jestli máte oprávnění k [dotazování](https://docs.microsoft.com/rest/api/appservice/appserviceplans/get) plánu App Service hostování vaší aplikace.
* Ověřte, zda je časové razítko klientského počítače správné a aktuální. Servery s časovými razítky od více než 15 minut v časovém razítku požadavku obvykle vyvolávají tuto chybu.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="404-not-found"></a>(404) Nenalezeno

Tato chyba označuje, že web nebyl na serveru nalezen.

Proveďte tyto kroky:

* Ověřte, že je web nasazený a spuštěný na prostředku App Service, ke kterému se připojujete.
* Ověřte, že je web k dispozici na adrese https://@no__t -0resource\>.azurewebsites.net
* Ověřte, že vaše správně běžící vlastní webová aplikace nevrátí stavový kód 404 při použití https://@no__t -0resource\>.azurewebsites.net
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="406-not-acceptable"></a>(406) nepřijatelný

Tato chyba značí, že server nemůže reagovat na sadu typů v hlavičce Accept žádosti.

Proveďte tyto kroky:

* Ověřte, že je web k dispozici na adrese https://@no__t -0resource\>.azurewebsites.net
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

* Ověřte v Azure Portal, že AppSettings pro ladicího programu snímků (SNAPSHOTDEBUGGER_EXTENSION_VERSION) a InstrumentationEngine (INSTRUMENTATIONENGINE_EXTENSION_VERSION) jsou velkými písmeny. Pokud ne, aktualizujte nastavení ručně, což vynutí restartování lokality.
::: moniker-end
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="500-internal-server-error"></a>(500) vnitřní chyba serveru

Tato chyba označuje, že lokalita je zcela mimo provoz, nebo Server nemůže zpracovat žádost. Snapshot Debugger pouze funkce spuštěné aplikace. [Application Insights Snapshot Debugger](https://docs.microsoft.com/azure/azure-monitor/app/snapshot-debugger) poskytuje snapshotting na výjimky a může to být nejlepší nástroj podle vašich potřeb.

### <a name="502-bad-gateway"></a>(502) chybná brána

Tato chyba indikuje problém sítě na straně serveru a může být dočasná.

Proveďte tyto kroky:

* Před opětovným připojením Snapshot Debugger Zkuste počkat několik minut.
* Pokud tato chyba nadále zůstává zachována, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

## <a name="issue-snappoint-does-not-turn-on"></a>Problém: Snímkovací bod se nezapíná

Pokud se zobrazí výstražná ikona ![snímkovací bod výstražná ikona](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "snímkovací bod výstražná ikona") s vaší snímkovacích bodů namísto ikonu regulární snímkovací bod, pak snímkovací bod není zapnuté.

![Snímkovací bod nezapne](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "snímkovací bod nezapne")

Proveďte tyto kroky:

1. Ujistěte se, že máte stejnou verzi zdrojového kódu, která se použila k sestavení a nasazení vaší aplikace. Ujistěte se, že se načítají správné symbolů pro vaše nasazení. Pokud chcete to provést, podívejte se **moduly** okno při ladění snímků a ověřit soubor symbolů sloupci zobrazí soubor .pdb načtené pro modul, který ladíte. Snapshot Debugger se pokusí automaticky stáhnout a použít symbolů pro vaše nasazení.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problém: Po otevření snímku se symboly nenačte

Pokud se zobrazí následující okno, symboly se nenačetl.

![Symboly se nenačtou](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symboly nenačtou.")

Proveďte tyto kroky:

- Klikněte na tlačítko **změnit nastavení symbolů...** odkaz na této stránce. V **ladění > symboly** nastavení, přidejte adresář mezipaměti symbolů. Restartujte ladění snímků po nastavení cesty k symbolu.

   Nasazení služby App Service musí odpovídat symboly nebo soubory PDB, k dispozici ve vašem projektu. Většině nasazeních (nasazení prostřednictvím sady Visual Studio, CI/CD s kanály Azure nebo Kudu, atd.) budou soubory symbolů podél publikovat do služby App Service. Adresář mezipaměti symbolů nastavení umožní sadě Visual Studio používat tyto symboly.

   ![Symbol nastavení](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symbol nastavení")

- Případně pokud vaše organizace používá server symbolů nebo sníží symboly v jinou cestu, použijte nastavení symbolu načtení správné symbolů pro vaše nasazení.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problém: V Průzkumníkovi cloudu nejde zobrazit možnost připojit Snapshot Debugger

Proveďte tyto kroky:

- Ujistěte se, že je nainstalovaná komponenta Snapshot Debugger. Otevřete instalační program sady Visual Studio a zkontrolujte **Snapshot Debugger** komponenta v úloze Azure.
::: moniker range="< vs-2019"
- Zajistěte, aby že vaše aplikace je podporovaná. V současné době pouze technologie ASP.NET (4.6.1+) a podporují aplikace ASP.NET Core (2.0 +) nasazené do služby Azure App Services.
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

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problém: V Diagnostické nástroje se zobrazují jenom omezené snímky

![Omezený snímkovací bod](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "omezený snímkovací bod")

Proveďte tyto kroky:

- Snímky spotřebovávat málo paměti, ale máte poplatek za potvrzení. Pokud ladicí program snímků zjistí, že je server v paměti v případě velkého zatížení, nepořizuje snímky. Zastavuje se relace ladicího programu snímků a zkusit to znovu, můžete odstranit již zachycené snímky.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problém: Ladění snímků pomocí více verzí sady Visual Studio obsahuje chyby

Visual Studio 2019 vyžaduje pro Azure App Service novější verzi rozšíření Snapshot Debugger webu.  Tato verze není kompatibilní se starší verzí rozšíření Snapshot Debugger webového serveru, kterou používá Visual Studio 2017.  Tato chyba se zobrazí, pokud se pokusíte připojit Snapshot Debugger v aplikaci Visual Studio 2019 k Azure App Service, která byla dříve Laděna Snapshot Debugger v aplikaci Visual Studio 2017:

![Nekompatibilní Snapshot Debugger rozšíření webu Visual studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "nekompatibilní Snapshot Debugger rozšíření webu Visual Studio 2019")

Naopak, pokud použijete Visual Studio 2017 k připojení Snapshot Debugger k Azure App Service, která byla dříve Laděna Snapshot Debugger v aplikaci Visual Studio 2019, zobrazí se následující chyba:

![Nekompatibilní Snapshot Debugger rozšíření webu Visual studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "nekompatibilní Snapshot Debugger rozšíření webu Visual Studio 2017")

Pokud to chcete opravit, odstraňte v Azure Portal následující nastavení aplikace a připojte Snapshot Debugger znovu:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problém: Mám potíže s laděním snímků a potřebuji povolit další protokolování

### <a name="enable-agent-logs"></a>Povolit protokoly agentů

Pokud chcete povolit a zakázat protokolování agenta, otevřete Visual Studio. přejděte na *nástroje > možnosti > Snapshot Debugger > povolit protokolování agenta*. Poznámka: Pokud je povolena taky možnost *Odstranit staré protokoly agentů při spuštění relace* , budou se při každém úspěšném připojení sady Visual Studio odstraňovat předchozí protokoly agentů.

Protokoly agentů najdete v následujících umístěních:

- App Services:
  - Přejděte na web Kudu vašeho App Service (to znamená yourappservice. **SCM**. azurewebsites.NET) a přejděte na konzolu ladění.
  - Protokoly agentů jsou uloženy v následujícím adresáři:  D:\home\LogFiles\SiteExtensions\DiagnosticsAgentLogs\
- VM/VMSS:
  - Přihlaste se k VIRTUÁLNÍmu počítači a protokoly agentů se ukládají takto:  C:\WindowsAzure\Logs\Plugins\Microsoft.Azure.Diagnostics.IaaSDiagnostics\<Version>\SnapshotDebuggerAgent_*.txt
- AKS
  - Přejděte do následujícího adresáře:/tmp/diag/AgentLogs/*

### <a name="enable-profilerinstrumentation-logs"></a>Povolit protokoly profileru a instrumentace

Protokoly instrumentace najdete v následujících umístěních:

- App Services:
  - Protokolování chyb je automaticky odesláno do D:\Home\LogFiles\eventlog.xml, události jsou označeny `<Provider Name="Instrumentation Engine" />` nebo "produkčními zarážkami".
- VM/VMSS:
  - Přihlaste se ke svému VIRTUÁLNÍmu počítači a otevřete Prohlížeč událostí.
  - Otevřete následující zobrazení: *Protokoly Windows > aplikaci*.
  - *Filtrovat aktuální protokol* podle *zdroje událostí* pomocí *zarážek v produkčním* prostředí nebo *modulu instrumentace*.
- AKS
  - Protokolování modulu instrumentace na/TMP/diag/log.txt (nastavení MicrosoftInstrumentationEngine_FileLogPath v souboru Dockerfile)
  - ProductionBreakpoint protokolování na/tmp/diag/shLog.txt

## <a name="known-issues"></a>Známé problémy

- Ladění snímků s více klienty sady Visual Studio na stejné služby App Service se momentálně nepodporuje.
- Optimalizace Roslyn IL nejsou plně podporovány v projektech ASP.NET Core. Pro některé projekty ASP.NET Core nebudete moci zobrazit některé proměnné nebo použití proměnných podmíněné příkazy.
- Speciální proměnné, jako například *$FUNCTION* nebo *$CALLER*, nelze vyhodnotit v podmíněné příkazy nebo protokolovací body pro projekty ASP.NET Core.
- Ladění snímků nefunguje v App Service, které mají [místní ukládání do mezipaměti](/azure/app-service/app-service-local-cache) zapnuté.
- Snímek ladění aplikace API se momentálně nepodporuje.

## <a name="site-extension-upgrade"></a>Upgrade rozšíření webu

Ladění snímků a Application Insights závisí na ICorProfiler, který načte do procesu lokality a způsobí, že soubor zamykání problémy při upgradu. Doporučujeme, abyste tento postup Ujistěte se, že neexistuje žádný dolů čas na produkční lokality.

- Vytvoření [Slot nasazení](/azure/app-service/web-sites-staged-publishing) ve službě App Service a nasaďte svůj web do slotu.
- Prohodit s produkčním slotu z Průzkumníku cloudu v sadě Visual Studio nebo z webu Azure portal.
- Zastavte Slot webu. Bude to trvat několik sekund ukončit vypnutí procesu w3wp.exe lokality ze všech instancí.
- Upgrade rozšíření webu slotu z webu kudu nebo na webu Azure portal (*okno App Service > vývojářské nástroje > Rozšíření > aktualizace*).
- Spusťte Slot webu. Doporučujeme navštívit web znovu zahřívání.
- Přepnout Slot s produkčním prostředí.

## <a name="see-also"></a>Viz také:

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [Ladění živé aplikace v ASP.NET pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md)
- [Ladění živých ASP.NET počítačů Azure Virtual Machines\Virtual pro škálování pomocí Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Ladění Live ASP.NET Azure Kubernetes pomocí Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)
