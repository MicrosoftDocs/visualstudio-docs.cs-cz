---
title: Řešení potíží s instalací nebo upgradem
description: V některých případech může docházet k chybám. Pokud se instalace nebo upgrade sady Visual Studio nepovede, může vám tato stránka popomáhat.
ms.date: 06/24/2020
ms.custom: seodec18
ms.topic: troubleshooting
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 418cc9f75842cb4f3e9d8c0c0753084e2f0633c2
ms.sourcegitcommit: c076fe12e459f0dbe2cd508e1294af14cb53119f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2020
ms.locfileid: "85350807"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Řešení potíží s instalací a upgradem sady Visual Studio

> [!IMPORTANT]
> Máte problém s instalací? Můžeme vám pomůžeme. Nabízíme možnost podpory [**instalace**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině).

Tato příručka pro řešení potíží obsahuje podrobné pokyny, které by měly vyřešit většinu problémů s instalací.

## <a name="online-installations"></a>Online instalace

Následující kroky jsou optimalizované pro typickou online instalaci. Problém, který má vliv na offline instalaci, najdete v tématu [jak řešit potíže s offline instalací](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 – ověření, zda se jedná o známý problém

::: moniker range="vs-2017"

U Instalační program pro Visual Studio, které Microsoft pracuje na řešení, dochází k některým známým problémům. Pokud chcete zjistit, jestli existuje alternativní řešení vašeho problému, podívejte se do [části známé problémy v našem poznámkách k verzi](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

U Instalační program pro Visual Studio, které Microsoft pracuje na řešení, dochází k některým známým problémům. Pokud chcete zjistit, jestli existuje alternativní řešení vašeho problému, podívejte se do [části známé problémy v našem poznámkách k verzi](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---try-repairing-visual-studio"></a>Krok 2 – Zkuste opravit Visual Studio

Oprava opravuje mnoho běžných problémů s aktualizací. Další informace o tom, kdy a jak používat funkce opravy v aplikaci Visual Studio, naleznete v tématu [Oprava sady Visual Studio](repair-visual-studio.md).

### <a name="step-3---check-with-the-developer-community"></a>Krok 3 – Projděte si komunitu vývojářů

Vyhledejte svou chybovou zprávu pomocí [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Jiní členové komunity si mohli zdokumentovat řešení vašeho problému.

### <a name="step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 4 – odstranění adresáře Instalační program pro Visual Studio pro vyřešení problémů s upgradem

Zaváděcí nástroj Instalační program pro Visual Studio je minimální spustitelný soubor, který nainstaluje zbytek Instalační program pro Visual Studio. Odstranění Instalační program pro Visual Studio souborů a následného spuštění zaváděcího nástroje může vyřešit některé chyby aktualizace.

> [!NOTE]
> Při provádění následujících akcí se přeinstalují Instalační program pro Visual Studio soubory a obnoví se metadata instalace.

::: moniker range="vs-2017"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář Instalační program pro Visual Studio. Obvykle je adresář `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Spusťte zaváděcí nástroj Instalační program pro Visual Studio. Zaváděcí nástroj můžete najít ve složce stažené soubory s názvem souboru, který následuje `vs_[Visual Studio edition]__*.exe` vzor. Pokud tuto aplikaci nenajdete, můžete zaváděcí nástroj stáhnout tak, že přejdete na stránku [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a kliknete na **Stáhnout** pro vaši edici sady Visual Studio. Potom spusťte spustitelný soubor a obnovte metadata instalace.
4. Zkuste znovu nainstalovat nebo aktualizovat Visual Studio. Pokud se instalační program stále nedaří, pokračujte na další krok.

::: moniker-end

::: moniker range="vs-2019"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář Instalační program pro Visual Studio. Obvykle je adresář `C:\Program Files (x86)\Microsoft Visual Studio\Installer` .
3. Spusťte zaváděcí nástroj Instalační program pro Visual Studio. Zaváděcí nástroj můžete najít ve složce stažené soubory s názvem souboru, který následuje `vs_[Visual Studio edition]__*.exe` vzor. Pokud tuto aplikaci nenajdete, můžete zaváděcí nástroj stáhnout tak, že přejdete na stránku [soubory ke stažení pro Visual Studio](https://visualstudio.microsoft.com/downloads) a kliknete na **Stáhnout** pro vaši edici sady Visual Studio. Potom spusťte spustitelný soubor a obnovte metadata instalace.
4. Zkuste znovu nainstalovat nebo aktualizovat Visual Studio. Pokud se instalační program stále nedaří, pokračujte na další krok.

::: moniker-end

### <a name="step-5---report-a-problem"></a>Krok 5 – nahlášení problému

V některých situacích, jako jsou například ty, které souvisejí s poškozenými soubory, se může stát, že se tyto problémy budou považovat za případ od případu. Abychom vám pomohli, udělejte prosím toto:

::: moniker range="vs-2017"

1. Shromáždí protokoly instalace. Podrobnosti najdete v tématu [Jak získat podrobnosti o instalačních protokolech sady Visual Studio](#installation-logs) .
2. Otevřete Instalační program pro Visual Studio a potom kliknutím na **ohlásit problém** otevřete nástroj pro zpětnou vazbu sady Visual Studio.
![Kartu můžete zobrazit tlačítkem zadat zpětnou vazbu a otevřít tak Nástroj pro zpětnou vazbu.](media/report-a-problem.png)
3. Dejte vašemu problému zprávu s názvem a poskytněte příslušné podrobnosti. Kliknutím na **Další** přejděte do části **přílohy** a pak připojte vygenerovaný soubor protokolu (obvykle se jedná o soubor `%TEMP%\vslogs.zip` ).
4. Kliknutím na **Další** Zkontrolujte zprávu o problému a pak klikněte na **Odeslat**.

::: moniker-end

::: moniker range="vs-2019"

1. Shromáždí protokoly instalace. Podrobnosti najdete v tématu [Jak získat podrobnosti o instalačních protokolech sady Visual Studio](#installation-logs) .
2. Otevřete Instalační program pro Visual Studio a potom kliknutím na **ohlásit problém** otevřete nástroj pro zpětnou vazbu sady Visual Studio.
![Kartu můžete zobrazit tlačítkem zadat zpětnou vazbu a otevřít tak Nástroj pro zpětnou vazbu.](media/vs-2019/vs-installer-report-problem.png)
3. Dejte vašemu problému zprávu s názvem a poskytněte příslušné podrobnosti. Kliknutím na **Další** přejděte do části **přílohy** a pak připojte vygenerovaný soubor protokolu (obvykle se jedná o soubor `%TEMP%\vslogs.zip` ).
4. Kliknutím na **Další** Zkontrolujte zprávu o problému a pak klikněte na **Odeslat**.

::: moniker-end

### <a name="step-6---run-installcleanupexe-to-remove-installation-files"></a>Krok 6 – spuštění InstallCleanup.exe pro odebrání instalačních souborů

Jako poslední možnost můžete [odebrat aplikaci Visual Studio](remove-visual-studio.md) a odebrat všechny instalační soubory a informace o produktu.

1. Postupujte podle pokynů v tématu [odebrání sady Visual Studio](remove-visual-studio.md).
2. Spusťte znovu zaváděcí nástroj, který je popsaný v [kroku 4 – odstraněním instalační program pro Visual Studio adresáře opravíte problémy s upgradem](#step-4---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Zkuste znovu nainstalovat nebo aktualizovat Visual Studio.

### <a name="step-7---contact-us-optional"></a>Krok 7 – kontaktujte nás (nepovinné)

Pokud žádný z předchozích kroků nepomohly úspěšně nainstalovat nebo upgradovat sadu Visual Studio, kontaktujte nás pomocí možnosti podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), kde najdete další pomoc.

## <a name="offline-installations"></a>Offline instalace

Tady je tabulka známých problémů a některá alternativní řešení, která vám můžou při vytváření [offline instalace](create-an-offline-installation-of-visual-studio.md) a následné instalaci z místního rozložení pomáhat.

| Problém       | Položka                   | Řešení |
| ----------- | ---------------------- | -------- |
| Uživatelé nemají přístup k souborům. | oprávnění (seznamy ACL) | Ujistěte se, že jste upravili oprávnění (ACL), aby mohli jiní uživatelé udělit přístup pro čtení *před* sdílením offline instalace. |
| Nedaří se nainstalovat nové úlohy, součásti nebo jazyky.  | `--layout`  | Ujistěte se, že máte přístup k Internetu, pokud instalujete z částečného rozložení a vyberete úlohy, komponenty nebo jazyky, které nebyly dříve staženy v tomto částečném rozložení. |

Další informace o řešení potíží s [instalací sítě](create-a-network-installation-of-visual-studio.md)najdete v tématu [řešení potíží souvisejících se sítí při instalaci nebo používání sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Protokoly instalace

Pro řešení většiny problémů s instalací je potřeba nainstalovat protokoly. Při odeslání problému pomocí [nahlášení problému](../ide/how-to-report-a-problem-with-visual-studio.md) v instalační program pro Visual Studio jsou tyto protokoly automaticky zahrnuty do sestavy.

Pokud se obrátíte na podpora Microsoftu, možná budete muset zadat tyto protokoly instalace pomocí [Nástroje pro Microsoft Visual Studio a .NET Framework pro shromažďování protokolů](https://www.microsoft.com/download/details.aspx?id=12493). Nástroj shromažďování protokolů shromažďuje protokoly instalace ze všech komponent nainstalovaných aplikací Visual Studio, včetně .NET Framework, Windows SDK a SQL Server. Shromažďuje také informace o počítači, Instalační služba systému Windows inventáře a informace protokolu událostí systému Windows pro Instalační program pro Visual Studio, Instalační služba systému Windows a obnovení systému.

Postup shromáždění protokolů:

1. [Stáhněte si nástroj](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otevřete příkazový řádek pro správu.
3. Spusťte `Collect.exe` z adresáře, kam jste nástroj uložili.
4. Vyhledá výsledný `vslogs.zip` soubor v `%TEMP%` adresáři, například `C:\Users\YourName\AppData\Local\Temp\vslogs.zip` .

> [!NOTE]
> Nástroj musí být spuštěn pod stejným uživatelským účtem, pod kterým byla neúspěšná instalace spuštěna. Pokud nástroj spouštíte z jiného uživatelského účtu, nastavte `–user:<name>` možnost zadat uživatelský účet, pod kterým byla spuštěna instalace, která selhala. `Collect.exe -?`Další možnosti a informace o využití získáte spuštěním z příkazového řádku správce.

## <a name="live-help"></a>Živá pomáhat

Pokud řešení uvedená v této příručce pro odstraňování potíží nepomáhají úspěšně nainstalovat nebo upgradovat Visual Studio, použijte možnost podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (jenom v angličtině), kde najdete další pomoc.

## <a name="see-also"></a>Viz také

* [Oprava sady Visual Studio](repair-visual-studio.md)
* [Odebrat Visual Studio](remove-visual-studio.md)
* [Nainstalujte a použijte Visual Studio a služby Azure za bránou firewall nebo proxy server](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Příručka správce sady Visual Studio](visual-studio-administrator-guide.md)
