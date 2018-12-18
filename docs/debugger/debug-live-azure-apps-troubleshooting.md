---
title: Řešení potíží při ladění snímků | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/07/2017
ms.technology: vs-ide-debug
ms.topic: troubleshooting
helpviewer_keywords:
- debugger
ms.assetid: 511a0697-c68a-4988-9e29-8d0166ca044a
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 82d8a310b86d5dc3c776243293a91f176025f897
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059824"
---
# <a name="troubleshooting-and-known-issues-for-snapshot-debugging-in-visual-studio"></a>Řešení potíží a známé problémy pro ladění snímků v sadě Visual Studio

Pokud problém nelze vyřešit pomocí postupu popsaného v tomto článku, obraťte se na snaphelp@microsoft.com.

## <a name="issue-snappoint-does-not-turn-on"></a>Problém: Snímkovacího bodu není možné zapnout

Pokud se zobrazí výstražná ikona ![snímkovací bod výstražná ikona](../debugger/media/snapshot-troubleshooting-snappoint-warning-icon.png "snímkovací bod výstražná ikona") s vaší snímkovacích bodů namísto ikonu regulární snímkovací bod, pak snímkovací bod není zapnuté.

![Snímkovací bod nezapne](../debugger/media/snapshot-troubleshooting-dont-turn-on.png "snímkovací bod nezapne")

Proveďte tyto kroky:

1. Ujistěte se, že máte stejnou verzi zdrojového kódu, který byl použit k vytvoření a nasazení vaší app.isua1. Ujistěte se, že se načítají správné symbolů pro vaše nasazení. Pokud chcete to provést, podívejte se **moduly** okno při ladění snímků a ověřit soubor symbolů sloupci zobrazí soubor .pdb načtené pro modul, který ladíte. Snapshot Debugger se pokusí automaticky stáhnout a použít symbolů pro vaše nasazení.

## <a name="issue-symbols-do-not-load-when-i-open-a-snapshot"></a>Problém: Symbolů se nenačetl při otevření snímku

Pokud se zobrazí následující okno, symboly se nenačetl.

![Symboly se nenačtou](../debugger/media/snapshot-troubleshooting-symbols-wont-load.png "symboly nenačtou.")

Proveďte tyto kroky:

- Klikněte na tlačítko **změnit nastavení symbolů...** odkaz na této stránce. V **ladění > symboly** nastavení, přidejte adresář mezipaměti symbolů. Restartujte ladění snímků po nastavení cesty k symbolu.

   Nasazení služby App Service musí odpovídat symboly nebo soubory PDB, k dispozici ve vašem projektu. Většině nasazeních (nasazení prostřednictvím sady Visual Studio, CI/CD s kanály Azure nebo Kudu, atd.) budou soubory symbolů podél publikovat do služby App Service. Adresář mezipaměti symbolů nastavení umožní sadě Visual Studio používat tyto symboly.

   ![Symbol nastavení](../debugger/media/snapshot-troubleshooting-symbol-settings.png "Symbol nastavení")

- Případně pokud vaše organizace používá server symbolů nebo sníží symboly v jinou cestu, použijte nastavení symbolu načtení správné symbolů pro vaše nasazení.

## <a name="issue-i-cannot-see-the-attach-snapshot-debugger-option-in-the-cloud-explorer"></a>Problém: nejde zobrazit možnost "Připojit Snapshot Debugger" v Průzkumníkovi cloudu

Proveďte tyto kroky:

- Ujistěte se, že je nainstalovaná komponenta Snapshot Debugger. Otevřete instalační program sady Visual Studio a zkontrolujte **Snapshot Debugger** komponenta v úloze Azure.
- Zajistěte, aby že vaše aplikace je podporovaná. V současné době pouze technologie ASP.NET (4.6.1+) a podporují aplikace ASP.NET Core (2.0 +) nasazené do služby Azure App Services.

## <a name="issue-i-only-see-throttled-snapshots-in-the-diagnostic-tools"></a>Problém: můžu zobrazit pouze omezené snímky v okně diagnostické nástroje

![Omezený snímkovací bod](../debugger/media/snapshot-troubleshooting-throttled-snapshots.png "omezený snímkovací bod")

Proveďte tyto kroky:

- Snímky spotřebovávat málo paměti, ale máte poplatek za potvrzení. Pokud ladicí program snímků zjistí, že je server v paměti v případě velkého zatížení, nepořizuje snímky. Zastavuje se relace ladicího programu snímků a zkusit to znovu, můžete odstranit již zachycené snímky.

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

[Ladění v sadě Visual Studio](../debugger/index.md)  
[Ladění živé aplikace v ASP.NET pomocí ladicího programu snímků](../debugger/debug-live-azure-applications.md)  
[Nejčastější dotazy k ladění snímků](../debugger/debug-live-azure-apps-faq.md)  
