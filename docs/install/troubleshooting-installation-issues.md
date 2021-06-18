---
title: Řešení potíží s instalací nebo upgradem
description: Někdy se může něco pokazit. Pokud vaše Visual Studio instalace nebo upgrade selže, může vám tato stránka pomoct.
ms.date: 06/24/2020
ms.custom: acquisition
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: e0bc092663cc0e100598f991ae1b2a18a4b94501
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2021
ms.locfileid: "112306862"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Řešení Visual Studio s instalací a upgradem

> [!IMPORTANT]
> Máte problém s instalací? Můžeme vám pomoct. Nabízíme možnost [**podpory instalačního chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině).

Tento průvodce odstraňováním potíží obsahuje podrobné pokyny, které by měly vyřešit většinu problémů s instalací.

## <a name="online-installations"></a>Instalace online

Následující kroky jsou optimalizované pro typickou online instalaci. Informace o problému, který ovlivňuje offline instalaci, najdete v tématu [Řešení potíží s offline instalací.](#offline-installations)

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 – Kontrola, jestli se jedná o známý problém

::: moniker range="vs-2017"

Existuje několik známých problémů s Instalační program pro Visual Studio, na které Microsoft pracuje na opravě. Pokud chcete zjistit, jestli existuje alternativní řešení vašeho problému, podívejte se do části [Známé problémy v poznámkách k verzi.](/visualstudio/releasenotes/vs2017-relnotes#-known-issues)

::: moniker-end

::: moniker range=">=vs-2019"

Existuje několik známých problémů s Instalační program pro Visual Studio, na které Microsoft pracuje na opravě. Pokud chcete zjistit, jestli existuje alternativní řešení vašeho problému, podívejte se do části [Známé problémy v poznámkách k verzi.](/visualstudio/releases/2019/release-notes#-known-issues)

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Krok 2 – Zkuste opravit Visual Studio

Opravuje mnoho běžných problémů s aktualizacemi. Další informace o tom, kdy a jak používat funkci opravy v nástroji Visual Studio najdete v tématu [Oprava Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Krok 3 : Kontrola s komunitou vývojářů

Vyhledejte chybovou zprávu pomocí [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8). Ostatní členové komunity mohli zdokumentovat řešení vašeho problému.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 4 – odstranění adresáře Instalační program pro Visual Studio, který opraví problémy s upgradem

Zaváděcí Instalační program pro Visual Studio je minimální odlehčený spustitelný soubor, který nainstaluje zbytek Instalační program pro Visual Studio. Odstranění Instalační program pro Visual Studio souborů a opětovné spuštění zaváděcího nástroje může vyřešit některá selhání aktualizací.

> [!NOTE]
> Provedením následujících akcí se přeinstalují Instalační program pro Visual Studio soubory a resetují metadata instalace.

::: moniker range="vs-2017"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte Instalační program pro Visual Studio. Adresář je obvykle `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Spusťte Instalační program pro Visual Studio bootstrapper. Zaváděcí nástroj můžete najít ve složce Stažené soubory s názvem, který se řídí `vs_[Visual Studio edition]__*.exe` vzorem. Pokud tuto aplikaci nenajdete, můžete si stáhnout bootstrapper tak, že kliknete  na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a kliknete na Stáhnout pro vaši edici Visual Studio. Potom spuštěním spustitelného souboru resetujte metadata instalace.
4. Zkuste aplikaci nainstalovat nebo Visual Studio znovu. Pokud se instalační program pořád nedaří, přejděte k dalšímu kroku.

::: moniker-end

::: moniker range=">=vs-2019"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte Instalační program pro Visual Studio. Adresář je obvykle `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Spusťte Instalační program pro Visual Studio bootstrapper. Zaváděcí nástroj můžete najít ve složce Stažené soubory s názvem, který se řídí `vs_[Visual Studio edition]__*.exe` vzorem. Pokud tuto aplikaci nenajdete, můžete si stáhnout bootstrapper tak, že kliknete  na stránku [Visual Studio stahování](https://visualstudio.microsoft.com/downloads) a kliknete na Stáhnout pro vaši edici Visual Studio. Potom spuštěním spustitelného souboru resetujte metadata instalace.
4. Zkuste aplikaci nainstalovat nebo Visual Studio znovu. Pokud se instalační program pořád nedaří, přejděte k dalšímu kroku.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Krok 5 – nahlášení problému

V některých situacích, například v situacích souvisejících s poškozenými soubory, může být třeba na problémy řešit případ od případu. Abychom vám pomohli, postupujte následovně:

::: moniker range="vs-2017"

1. Shromáždíte instalační protokoly. Podrobnosti [najdete v tématu Jak Visual Studio protokolů instalace.](#installation-logs)
2. Otevřete okno Instalační program pro Visual Studio a potom kliknutím na **Nahlásit problém** otevřete nástroj Visual Studio Feedback.
![Kartu můžete použít k tlačítku Poskytnout zpětnou vazbu a otevřít nástroj pro zpětnou vazbu.](media/report-a-problem.png)
3. Dejte svému problému název a uveďte relevantní podrobnosti. Kliknutím **na** Další přejděte do **části Přílohy** a připojte vygenerovaný soubor protokolu (obvykle je soubor v `%TEMP%\vslogs.zip` ).
4. Kliknutím **na Další** zkontrolujte sestavu problému a pak klikněte na **Odeslat.**

::: moniker-end

::: moniker range=">=vs-2019"

1. Shromáždíte instalační protokoly. Podrobnosti [najdete v tématu Jak Visual Studio protokolů instalace.](#installation-logs)
2. Otevřete okno Instalační program pro Visual Studio a potom kliknutím na **Nahlásit problém** otevřete nástroj Visual Studio Feedback.
![Kartu můžete použít k tlačítku Poskytnout zpětnou vazbu a otevřít nástroj pro zpětnou vazbu.](media/vs-2019/vs-installer-report-problem.png)
3. Dejte svému problému název a uveďte relevantní podrobnosti. Kliknutím **na** Další přejděte do **části Přílohy** a připojte vygenerovaný soubor protokolu (obvykle je soubor v `%TEMP%\vslogs.zip` ).
4. Kliknutím **na Další** zkontrolujte sestavu problému a pak klikněte na **Odeslat.**

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Krok 6 – InstallCleanup.exe odebrání instalačních souborů

Nakonec můžete odebrat všechny instalační [soubory Visual Studio](remove-visual-studio.md) informace o produktech.

1. Postupujte podle pokynů v tématu [Odebrání Visual Studio](remove-visual-studio.md).
2. Znovu spusťte zaváděcí nástroj popsaný v kroku 4 – odstranění adresáře [Instalační program pro Visual Studio a opravte problémy s upgradem.](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems)
3. Zkuste aplikaci nainstalovat nebo Visual Studio znovu.

### <a name="step-7---contact-us-optional"></a>Krok 7 – kontaktujte nás (volitelné)

Pokud vám žádný z předchozích kroků nepomáhou úspěšně nainstalovat [](https://visualstudio.microsoft.com/vs/support/#talktous) nebo upgradovat Visual Studio, kontaktujte nás s další pomocí možnosti podpory živého chatu (jenom v angličtině).

## <a name="offline-installations"></a>Offline instalace

Tady je tabulka známých problémů a některá alternativní řešení, která vám můžou pomoct při vytváření [offline](create-an-offline-installation-of-visual-studio.md) instalace a instalaci z místního rozložení.

| Problém       | Položka                   | Řešení |
| ----------- | ---------------------- | -------- |
| Uživatelé nemají přístup k souborům. | oprávnění (seznamy ACL) | Před sdílením offline instalace nezapomeňte oprávnění (seznamy ACL)  upravit tak, aby ostatním uživatelům udělili oprávnění ke čtení. |
| Nové úlohy, komponenty nebo jazyky se nedaří nainstalovat.  | `--layout`  | Ujistěte se, že máte přístup k internetu, pokud instalujete z částečného rozložení a vybíráte úlohy, komponenty nebo jazyky, které nebyly staženy dříve v tomto částečném rozložení. |

Další informace o řešení problémů s instalací sítě [najdete](create-a-network-installation-of-visual-studio.md)v tématu Řešení chyb souvisejících se sítí při instalaci nebo používání [nástroje Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Protokoly instalace

K řešení většiny problémů s instalací jsou potřeba instalační protokoly. Když odešlete problém pomocí funkce [Nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) v Instalační program pro Visual Studio, tyto protokoly se automaticky zahrnou do vaší sestavy.

Pokud se Podpora Microsoftu, budete možná muset zadat tyto instalační protokoly pomocí nástroje pro shromažďování protokolů Microsoft Visual Studio a [.NET Framework protokolů.](https://www.microsoft.com/download/details.aspx?id=12493) Nástroj pro shromažďování protokolů shromažďuje instalační protokoly ze všech komponent nainstalovaných Visual Studio, včetně .NET Framework, Windows SDK a SQL Server. Shromažďuje také informace o počítači, inventář Instalační služba systému Windows a informace protokolu událostí systému Windows pro Instalační program pro Visual Studio, Instalační služba systému Windows a obnovení systému.

Shromažďování protokolů:

1. [Stáhněte si nástroj](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otevřete příkazový řádek pro správu.
3. Spusťte `Collect.exe` z adresáře, kam jste nástroj uložili.
4. Výsledný soubor `vslogs.zip` vyhledejte ve svém `%TEMP%` adresáři, například `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Nástroj musí být spuštěný pod stejným uživatelským účtem, pod který byla neúspěšná instalace spuštěna. Pokud nástroj používáte z jiného uživatelského účtu, nastavte možnost pro zadání uživatelského účtu, pod kterým byla `–user:<name>` neúspěšná instalace spuštěna. Další možnosti a informace o použití zobrazíte spuštěním příkazu z příkazového řádku `Collect.exe -?` správce.

## <a name="live-help"></a>Živá nápověda

Pokud vám řešení uvedená v tomto průvodci odstraňováním potíží nepomáhou s úspěšnou instalací nebo upgradem Visual Studio, pro další pomoc použijte naši možnost podpory [**živého**](https://visualstudio.microsoft.com/vs/support/#talktous) chatu (jenom v angličtině).

## <a name="see-also"></a>Viz také

* [Oprava sady Visual Studio](repair-visual-studio.md)
* [Odebrání Visual Studio](remove-visual-studio.md)
* [Instalace a používání Visual Studio a služeb Azure za bránou firewall nebo proxy server](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
