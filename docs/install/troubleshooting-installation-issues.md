---
title: Poradce při potížích s instalací nebo upgradem
description: Někdy se věci mohou pokazit. Pokud se instalace nebo upgrade sady Visual Studio nezdaří, může vám tato stránka pomoci.
ms.date: 09/13/2019
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
ms.openlocfilehash: 9dfdf504378dafd7d71288cae1927dd8d6bb9e56
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114998"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Poradce při potížích s instalací a upgradem sady Visual Studio

> [!IMPORTANT]
> Máte potíže s instalací? Můžeme pomoct. Nabízíme možnost podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině).

Tento průvodce odstraňováním potíží obsahuje podrobné pokyny, které by měly vyřešit většinu problémů s instalací.

## <a name="online-installations"></a>Online instalace

Následující kroky jsou optimalizovány pro typickou online instalaci. Problém, který má vliv na instalaci offline, naleznete v [tématu Řešení potíží s offline instalací](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 – Zkontrolujte, zda se jedná o známý problém

::: moniker range="vs-2017"

Existují některé známé problémy s Instalační službou sady Visual Studio, které společnost Microsoft pracuje na opravě. Chcete-li zjistit, zda váš problém něco řešení, podívejte se do [části Známé problémy v našich poznámkách k verzi](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Existují některé známé problémy s Instalační službou sady Visual Studio, které společnost Microsoft pracuje na opravě. Chcete-li zjistit, zda váš problém něco řešení, podívejte se do [části Známé problémy v našich poznámkách k verzi](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Krok 2 – Obraťte se na komunitu vývojářů

Vyhledejte chybovou zprávu pomocí [komunity vývojářů sady Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Ostatní členové komunity mohli zdokumentovat řešení vašeho problému.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 3 – Odstranění adresáře Instalační služby sady Visual Studio k opravě problémů s upgradem

Zaváděcí nástroj Instalační služby sady Visual Studio je minimální lehký spustitelný soubor, který nainstaluje zbytek instalačního programu sady Visual Studio. Odstranění souborů instalačního programu sady Visual Studio a opětovné spuštění zaváděcího nástroje může vyřešit některé chyby aktualizace.

> [!NOTE]
> Provedením následujících akcí přeinstalujete instalační soubory sady Visual Studio a obnovíte metadata instalace.

::: moniker range="vs-2017"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář Instalační služby sady Visual Studio. Adresář je `C:\Program Files (x86)\Microsoft Visual Studio\Installer`obvykle .
3. Spusťte zaváděcí nástroj Instalační služby sady Visual Studio. Zaváděcí nástroj můžete najít ve složce Ke `vs_[Visual Studio edition]__*.exe` stažení s názvem souboru, který následuje za vzorem. Pokud tuto aplikaci nenajdete, můžete nástrojař stáhnout tak, že přejdete na stránku [stažení sady Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) a kliknete na **stáhnout** pro edici sady Visual Studio. Potom spusťte spustitelný soubor obnovit metadata instalace.
4. Zkuste znovu nainstalovat nebo aktualizovat visual studio. Pokud instalační program nadále selhává, přejděte k dalšímu kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář Instalační služby sady Visual Studio. Adresář je `C:\Program Files (x86)\Microsoft Visual Studio\Installer`obvykle .
3. Spusťte zaváděcí nástroj Instalační služby sady Visual Studio. Zaváděcí nástroj můžete najít ve složce Ke `vs_[Visual Studio edition]__*.exe` stažení s názvem souboru, který následuje za vzorem. Pokud tuto aplikaci nenajdete, můžete nástrojař stáhnout tak, že přejdete na stránku [stažení sady Visual Studio](https://visualstudio.microsoft.com/downloads) a kliknete na **stáhnout** pro edici sady Visual Studio. Potom spusťte spustitelný soubor obnovit metadata instalace.
4. Zkuste znovu nainstalovat nebo aktualizovat visual studio. Pokud instalační program nadále selhává, přejděte k dalšímu kroku.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Krok 4 – Nahlášení problému

V některých situacích, například v situacích souvisejících s poškozenými soubory, může být třeba problémy prohlížet případ od případu. Chcete-li nám pomoci, proveďte následující kroky:

::: moniker range="vs-2017"

1. Shromážděte protokoly nastavení. Podrobnosti [najdete v tématu Jak získat protokoly instalace sady Visual Studio.](#installation-logs)
2. Otevřete Instalační službu sady Visual Studio a kliknutím na **Nahlásit problém** otevřete nástroj Visual Studio Feedback.
![Chcete-li otevřít nástroj pro zpětnou vazbu, můžete pomocí karty Poskytnout zpětnou vazbu](media/report-a-problem.png)
3. Poskytněte název hlášení o problému a uveďte příslušné podrobnosti. Klepnutím na tlačítko **Další** přejdete do části **Přílohy** a pak připojte generovaný soubor protokolu (obvykle je soubor na). `%TEMP%\vslogs.zip`
4. Klepnutím na tlačítko **Další** zkontrolujte hlášení o problému a potom klepněte na tlačítko **Odeslat**.

::: moniker-end

::: moniker range="vs-2019"

1. Shromážděte protokoly nastavení. Podrobnosti [najdete v tématu Jak získat protokoly instalace sady Visual Studio.](#installation-logs)
2. Otevřete Instalační službu sady Visual Studio a kliknutím na **Nahlásit problém** otevřete nástroj Visual Studio Feedback.
![Chcete-li otevřít nástroj pro zpětnou vazbu, můžete pomocí karty Poskytnout zpětnou vazbu](media/vs-2019/vs-installer-report-problem.png)
3. Poskytněte název hlášení o problému a uveďte příslušné podrobnosti. Klepnutím na tlačítko **Další** přejdete do části **Přílohy** a pak připojte generovaný soubor protokolu (obvykle je soubor na). `%TEMP%\vslogs.zip`
4. Klepnutím na tlačítko **Další** zkontrolujte hlášení o problému a potom klepněte na tlačítko **Odeslat**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Krok 5 – Spuštění souboru InstallCleanup.exe k odebrání instalačních souborů

Jako poslední možnost můžete [aplikaci Visual Studio odebrat](remove-visual-studio.md) a odebrat všechny instalační soubory a informace o produktu.

1. Postupujte podle pokynů v [aplikaci Remove Visual Studio](remove-visual-studio.md).
2. Znovu spusťte zaváděcí nástroj popsaný v [kroku 3 – Odstraňte adresář Instalační služby sady Visual Studio a opravte problémy s upgradem](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Zkuste znovu nainstalovat nebo aktualizovat visual studio.

### <a name="step-6---contact-us-optional"></a>Krok 6 - Kontaktujte nás (nepovinné)

Pokud vám žádný z předchozích kroků nepomůže úspěšně nainstalovat nebo upgradovat visual studio, kontaktujte nás pomocí možnosti podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině) s žádostí o další pomoc.

## <a name="offline-installations"></a>Instalace offline

Zde je tabulka známých problémů a některá řešení, která vám mohou pomoci při vytváření [offline instalace](create-an-offline-installation-of-visual-studio.md) a instalaci z místního rozložení.

| Problém       | Položka                   | Řešení |
| ----------- | ---------------------- | -------- |
| Uživatelé nemají přístup k souborům. | oprávnění (ACLs) | Ujistěte se, že jste upravili oprávnění (ACL) tak, aby před sdílením offline instalace udělovali přístup pro čtení ostatním *uživatelům.* |
| Instalace nových úloh, součástí nebo jazyků se nepodaří nainstalovat.  | `--layout`  | Ujistěte se, že máte přístup k Internetu, pokud instalujete z částečného rozložení a vyberete úlohy, součásti nebo jazyky, které nebyly dříve staženy v tomto částečném rozložení. |

Další informace o řešení problémů se [síťovou instalací](create-a-network-installation-of-visual-studio.md)naleznete v [tématu Poradce při potížích se sítí při instalaci nebo použití sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Protokoly instalace

K řešení většiny problémů s instalací jsou zapotřebí protokoly instalace. Při odeslání problému pomocí [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) v Instalační službě sady Visual Studio, tyto protokoly jsou automaticky zahrnuty do sestavy.

Pokud se obrátíte na podporu společnosti Microsoft, bude pravděpodobně nutné poskytnout tyto protokoly instalace pomocí [sady Microsoft Visual Studio a nástroje .NET Framework Log Collection Tool](https://www.microsoft.com/download/details.aspx?id=12493). Nástroj pro shromažďování protokolů shromažďuje protokoly instalace ze všech součástí nainstalovaných aplikací Visual Studio, včetně rozhraní .NET Framework, sady Windows SDK a serveru SQL Server. Shromažďuje také informace o počítači, inventář instalačníslužby systému Windows a informace protokolu událostí systému Windows pro Instalační službu sady Visual Studio, Instalační službu systému Windows a Nástroj Obnovení systému.

Chcete-li shromažďovat protokoly:

1. [Stáhněte si nástroj](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otevřete příkazový řádek pro správu.
3. Spusťte `Collect.exe` z adresáře, do kterého jste nástroj uložili.
4. Najděte výsledný `vslogs.zip` soubor `%TEMP%` v adresáři, `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`například .

> [!NOTE]
> Nástroj musí být spuštěn pod stejným uživatelským účtem, pod kterým byla spuštěna neúspěšná instalace. Pokud nástroj používáte z jiného uživatelského `–user:<name>` účtu, nastavte možnost určení uživatelského účtu, pod kterým byla spuštěna neúspěšná instalace. Další `Collect.exe -?` možnosti a informace o využití získáte spuštěním z příkazového řádku správce.

## <a name="live-help"></a>Živá nápověda

Pokud vám řešení uvedená v této příručce pro řešení potíží nepomohou úspěšně nainstalovat nebo upgradovat visual studio, použijte další pomoc pomocí možnosti podpory [**živého chatu**](https://visualstudio.microsoft.com/vs/support/#talktous) (pouze v angličtině).

## <a name="see-also"></a>Viz také

* [Odebrat Visual Studio](remove-visual-studio.md)
* [Instalace a použití sady Visual Studio a služeb Azure Services za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Průvodce správcem sady Visual Studio](visual-studio-administrator-guide.md)
