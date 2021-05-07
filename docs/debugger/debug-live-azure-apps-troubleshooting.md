---
title: Řešení potíží s laděním snímků | Microsoft Docs
description: Vysvětlení řešení potíží a známých problémů pro ladění snímků v aplikaci Visual Studio. Načtěte ICorProfiler, aniž by to způsobilo výpadek produkčního webu.
ms.custom: SEO-VS-2020
ms.date: 04/24/2019
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: aad883ac0c3f703b2d6a4e10d3a0ef2468cd8465
ms.sourcegitcommit: d4887ef2ca97c55e2dad9f179eec2c9631d91c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2021
ms.locfileid: "108798437"
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

První postup efektivně zabezpečuje vaši doménu aplikace podobným způsobem jako při **přihlašování pomocí [IdentityProvider]**. Druhá trasa zpřístupňuje koncový bod SnapshotDebugger AgentLaunch mimo ověřování, který provádí předdefinovanou  akci spuštění diagnostického agenta SnapshotDebugger pouze v případě, že je pro vaši službu App Service povolené předinstalované rozšíření webu SnapshotDebugger. Další podrobnosti o konfiguraci authorization.jsv tématu Pravidla autorizace [adres URL.](https://azure.github.io/AppService/2016/11/17/URL-Authorization-Rules.html)

### <a name="403-forbidden"></a>(403) Zakázáno

Tato chyba značí odepření oprávnění. Příčinou může být mnoho různých problémů.

Postupujte následovně:

* Ověřte, že Visual Studio účet má platné předplatné Azure s potřebnými oprávněními Role-Based Access Control (RBAC) pro prostředek. V případě služby AppService zkontrolujte, jestli máte oprávnění k [dotazování](/rest/api/appservice/appserviceplans/get) App Service plán hostující vaši aplikaci.
* Ověřte správnost a aktuální časové razítko klientského počítače. K této chybě obvykle dojde u serverů s časovými razítky o více než 15 minut od časového razítka požadavku.
* Pokud tato chyba přetrvává, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="404-not-found"></a>(404) Nenašlé

Tato chyba znamená, že se web na serveru nenašel.

Postupujte následovně:

* Ověřte, že máte na virtuálním počítači nasazený a spuštěný App Service, ke které se připojujete.
* Ověřte, že je web dostupný na https:// \<resource\> .azurewebsites.net
* Ověřte, že správně spuštěná vlastní webová aplikace nevrací stavový kód 404 při přístupu na adrese https:// \<resource\> .azurewebsites.net
* Pokud tato chyba přetrvává, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

### <a name="406-not-acceptable"></a>(406) Nepřijatelné

Tato chyba značí, že server nemůže reagovat na typ nastavený v hlavičce Accept požadavku.

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

Postupujte následovně:

* Zkuste několik minut počkat, než znovu připojíte Snapshot Debugger.
* Pokud tato chyba přetrvává, použijte jeden z kanálů zpětné vazby popsaných na začátku tohoto článku.

## <a name="issue-snappoint-does-not-turn-on"></a>Problém: Modul snappoint se nezapnout

Pokud se místo běžné ikony ![snappointu](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "Ikona upozornění snappointu") zobrazí ikona upozornění Ikona upozornění bodu snappoint s vaším snappointem, modul snappoint není zapnutý.

![Modul snappoint se nezapnout](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "Modul snappoint se nezapnout")

Postupujte následovně:

1. Ujistěte se, že máte stejnou verzi zdrojového kódu, která se použila k sestavení a nasazení vaší aplikace. Ujistěte se, že načítáte správné symboly pro vaše nasazení. Chcete-li to  provést, při ladění snímku zobrazte okno Moduly a ověřte, že ve sloupci Soubor symbolů se zobrazuje soubor .pdb načtený pro modul, který ladíte. Aplikace Snapshot Debugger pokusí automaticky stáhnout a použít symboly pro vaše nasazení.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problém: Symboly se nenačtou, když otevřu snímek.

Pokud se zobrazí následující okno, symboly se nenačtou.

![Symboly se nenačtou](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "Symboly se nenačtou")

Postupujte následovně:

- Klikněte na **Změnit nastavení symbolu...** na této stránce. V nastavení **> Symbol** přidejte adresář mezipaměti symbolů. Po nastavení cesty k symbolu restartujte ladění snímků.

   Symboly nebo soubory .pdb, které jsou k dispozici v projektu, musí odpovídat vašemu App Service nasazení. Většina nasazení (nasazení prostřednictvím sady Visual Studio, CI/CD s Azure Pipelines nebo Kudu atd.) publikuje soubory symbolů spolu s App Service. Nastavení adresáře mezipaměti symbolů umožní aplikaci Visual Studio používat tyto symboly.

   ![Nastavení symbolu](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Nastavení symbolů")

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

![Omezení snímkovací bod](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "Ohrocený modul snappoint")

Postupujte následovně:

- Snímky zachytají málo paměti, ale účtují se poplatek za potvrzení. Pokud Snapshot Debugger zjistí, že je váš server příliš zatížení paměti, nepořažuje snímky. Zaznamenané snímky můžete odstranit tak, že zastavíte Snapshot Debugger a budete to opakovat.

::: moniker range=">= vs-2019"
## <a name="issue-snapshot-debugging-with-multiple-versions-of-the-visual-studio-gives-me-errors"></a>Problém: Ladění snímků s několika verzemi Visual Studio mi dává chyby

Visual Studio 2019 vyžaduje novější verzi rozšíření Snapshot Debugger webu na vašem Azure App Service.  Tato verze není kompatibilní se starší verzí rozšíření webu Snapshot Debugger, které používá Visual Studio 2017.  Následující chyba se zobrazí, pokud se pokusíte připojit Snapshot Debugger v Visual Studio 2019 k Azure App Service, který dříve ladil Snapshot Debugger v Visual Studio 2017:

![Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2019](../debugger/media/snapshot-troubleshooting-incompatible-vs2019.png "Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2019")

Pokud naopak použijete Visual Studio 2017 k připojení Snapshot Debugger k Azure App Service, který předtím ladil Snapshot Debugger v Visual Studio 2019, zobrazí se následující chyba:

![Nekompatibilní Snapshot Debugger lokality Visual Studio 2017](../debugger/media/snapshot-troubleshooting-incompatible-vs2017.png "Nekompatibilní rozšíření Snapshot Debugger webu Visual Studio 2017")

Pokud chcete tento problém vyřešit, odstraňte následující nastavení aplikace v Azure Portal a znovu připojte Snapshot Debugger:

- INSTRUMENTATIONENGINE_EXTENSION_VERSION
- SNAPSHOTDEBUGGER_EXTENSION_VERSION
::: moniker-end

## <a name="issue-i-am-having-problems-snapshot-debugging-and-i-need-to-enable-more-logging"></a>Problém: Mám potíže s laděním snímků a potřebuji povolit další protokolování

### <a name="enable-agent-logs"></a>Povolení protokolů agenta

Pokud chcete povolit a zakázat protokolování agenta, Visual Studio přejděte na *Nástroje>Možnosti>Snapshot Debugger>Povolit protokolování agenta.* Poznámka: *Pokud je povolená také* možnost Odstranit staré protokoly agenta při spuštění relace, při každém úspěšném Visual Studio připojení se odstraní předchozí protokoly agenta.

Protokoly agenta najdete v následujících umístěních:

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
- Ladění snímků API Apps se v současné době nepodporuje.

## <a name="site-extension-upgrade"></a>Upgrade rozšíření lokality

Ladění snímků a Application Insights závisí na ICorProfileru, který se načte do procesu lokality a během upgradu způsobí problémy se zamykáním souborů. Tento proces doporučujeme, abyste zajistili, že nebude k dispozici žádný výseč v produkčním prostředí.

- Vytvořte slot [nasazení v](/azure/app-service/web-sites-staged-publishing) rámci App Service a nasaďte svůj web do slotu.
- Slot prohození slotu s produkčním prostředím z Průzkumníka Visual Studio nebo z Azure Portal.
- Zastavte lokalitu slotu. Bude to trvat několik sekund, než se proces w3wp.exe ze všech instancí vypne.
- Upgradujte rozšíření lokality slotu z webu Kudu nebo Azure Portal (*App Service Blade > Development Tools > Extensions > Update*).
- Spusťte web slotu. Doporučujeme navštívit web, abyste ho znovu zahřáli.
- Prohození slotu s produkčním prostředím

## <a name="see-also"></a>Viz také

- [Ladění v sadě Visual Studio](../debugger/index.yml)
- [Ladění živých ASP.NET aplikací pomocí Snapshot Debugger](../debugger/debug-live-azure-applications.md)
- [Živé ladění ASP.NET Azure Virtual Machines\Virtual Machines Scale Sets pomocí Snapshot Debugger](../debugger/debug-live-azure-virtual-machines.md)
- [Ladění živého ASP.NET Azure Kubernetes pomocí Snapshot Debugger](../debugger/debug-live-azure-kubernetes.md)
- [Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.yml)
