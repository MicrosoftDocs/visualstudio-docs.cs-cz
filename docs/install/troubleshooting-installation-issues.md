---
title: Řešení potíží s instalací nebo upgradovat problémy
description: V některých případech může něco selže. Pokud instalace sady Visual Studio nebo upgrade selže, může pomoct tuto stránku.
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
ms.sourcegitcommit: f3f668ecaf11b4c2738ebc91923c6b5e38e74670
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2020
ms.locfileid: "76114998"
---
# <a name="troubleshoot-visual-studio-installation-and-upgrade-issues"></a>Řešení potíží s instalací a upgradem sady Visual Studio

> [!IMPORTANT]
> Máte potíže s instalací? Můžeme pomoct. Nabízíme [ **živý chat** ](https://visualstudio.microsoft.com/vs/support/#talktous) možnost podpory (jenom v angličtině).

Tento průvodce odstraňováním potíží obsahuje podrobné pokyny, které by měla vyřešit většinu problémů s instalací.

## <a name="online-installations"></a>Online instalace

Následující kroky jsou optimalizované pro typické instalace online. Problém, který má vliv na offline instalaci, najdete v tématu [postupy řešení potíží s offline instalací](#offline-installations).

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Krok 1 – Zkontrolujte, zda tento problém se o známý problém

::: moniker range="vs-2017"

Existuje několik známých problémů s nástrojem Visual Studio Installer, který společnost Microsoft pracuje na opravě. Pokud chcete zobrazit, pokud je alternativní řešení vašeho problému, zkontrolujte, [známé problémy v části poznámky k verzi](/visualstudio/releasenotes/vs2017-relnotes#-known-issues).

::: moniker-end

::: moniker range="vs-2019"

Existuje několik známých problémů s nástrojem Visual Studio Installer, který společnost Microsoft pracuje na opravě. Pokud chcete zobrazit, pokud je alternativní řešení vašeho problému, zkontrolujte, [známé problémy v části poznámky k verzi](/visualstudio/releases/2019/release-notes#-known-issues).

::: moniker-end

### <a name="step-2---check-with-the-developer-community"></a>Krok 2: Kontrola s komunitou vývojářů

Hledání na příslušnou chybovou zprávu s [komunity vývojářů v aplikaci Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). Ostatní členové komunity můžou mít dokumentované řešení vašeho problému.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Krok 3: odstranění adresáře instalační program sady Visual Studio k odstraňování problémů s upgradem

Instalační program sady Visual Studio bootstrapper je minimální odlehčené spustitelný soubor, který nainstaluje zbývající části instalačního programu sady Visual Studio. Odstraňování souborů instalačního programu sady Visual Studio a pak znovu spustit zavaděč možná půjde vyřešit některé chyby aktualizace.

> [!NOTE]
> Provedením následujících akcí přeinstaluje soubory instalačního programu sady Visual Studio a obnoví metadat instalace.

::: moniker range="vs-2017"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář instalační program sady Visual Studio. Adresář je obvykle `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Spusťte instalační program sady Visual Studio zaváděcí nástroj. Zaváděcí nástroj může najít ve složce stažené soubory s názvem souboru, který následuje `vs_[Visual Studio edition]__*.exe` vzor. Pokud tuto aplikaci se nepodařilo najít, zaváděcí nástroj můžete stáhnout tak, že přejdete [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) stránku a kliknutím na **Stáhnout** vaší verze sady Visual Studio. Spusťte spustitelný soubor resetovat vaše instalace metadata.
4. Akci pro instalaci nebo aktualizaci sady Visual Studio znovu. Pokud instalační program ani potom nedaří, přejděte k dalšímu kroku.

::: moniker-end

::: moniker range="vs-2019"

1. Ukončete instalační program sady Visual Studio.
2. Odstraňte adresář instalační program sady Visual Studio. Adresář je obvykle `C:\Program Files (x86)\Microsoft Visual Studio\Installer`.
3. Spusťte instalační program sady Visual Studio zaváděcí nástroj. Zaváděcí nástroj může najít ve složce stažené soubory s názvem souboru, který následuje `vs_[Visual Studio edition]__*.exe` vzor. Pokud tuto aplikaci se nepodařilo najít, zaváděcí nástroj můžete stáhnout tak, že přejdete [soubory ke stažení Visual Studio](https://visualstudio.microsoft.com/downloads) stránku a kliknutím na **Stáhnout** vaší verze sady Visual Studio. Spusťte spustitelný soubor resetovat vaše instalace metadata.
4. Akci pro instalaci nebo aktualizaci sady Visual Studio znovu. Pokud instalační program ani potom nedaří, přejděte k dalšímu kroku.

::: moniker-end

### <a name="step-4---report-a-problem"></a>Krok 4 – ohlásit problém

V některých situacích, jako je ta, která souvisí poškozené soubory možná muset problémy se podívali na případ od případu. Abychom pomohli nám umožňují, postupujte prosím takto:

::: moniker range="vs-2017"

1. Shromážděte vaše protokoly instalace. Zobrazit [jak získat protokoly instalace sady Visual Studio](#installation-logs) podrobnosti.
2. Otevřete instalační program sady Visual Studio a pak klikněte na tlačítko **nahlásit problém** otevřete Nástroje pro zpětnou vazbu Visual Studio.
![Vytvořit kartu k tlačítku poskytnout zpětnou vazbu a otevřete nástroj pro zpětnou vazbu](media/report-a-problem.png)
3. Pojmenujte hlášení o problému a poskytuje relevantní podrobnosti. Klikněte na tlačítko **Další** přejdete **přílohy** části a připojte soubor protokolu vygenerovaný (obvykle je soubor na `%TEMP%\vslogs.zip`).
4. Klikněte na tlačítko **Další** zkontrolujte hlášení o problému, a potom klikněte na **odeslat**.

::: moniker-end

::: moniker range="vs-2019"

1. Shromážděte vaše protokoly instalace. Zobrazit [jak získat protokoly instalace sady Visual Studio](#installation-logs) podrobnosti.
2. Otevřete instalační program sady Visual Studio a pak klikněte na tlačítko **nahlásit problém** otevřete Nástroje pro zpětnou vazbu Visual Studio.
![Vytvořit kartu k tlačítku poskytnout zpětnou vazbu a otevřete nástroj pro zpětnou vazbu](media/vs-2019/vs-installer-report-problem.png)
3. Pojmenujte hlášení o problému a poskytuje relevantní podrobnosti. Klikněte na tlačítko **Další** přejdete **přílohy** části a připojte soubor protokolu vygenerovaný (obvykle je soubor na `%TEMP%\vslogs.zip`).
4. Klikněte na tlačítko **Další** zkontrolujte hlášení o problému, a potom klikněte na **odeslat**.

::: moniker-end

### <a name="step-5---run-installcleanupexe-to-remove-installation-files"></a>Krok 5: spuštění InstallCleanup.exe odebrat instalační soubory

Jako poslední možnost, můžete [odebrání sady Visual Studio](remove-visual-studio.md) odebrat všechny instalační soubory a informace o produktu.

1. Postupujte podle pokynů v [odebrat sady Visual Studio](remove-visual-studio.md).
2. Znovu spustit zaváděcí nástroj, který je popsaný v [krok 3 – odstranit adresář instalační program sady Visual Studio k odstraňování problémů s upgradem](#step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
3. Akci pro instalaci nebo aktualizaci sady Visual Studio znovu.

### <a name="step-6---contact-us-optional"></a>Krok 6: Obraťte se na nás (volitelné)

Pokud žádný z předchozích kroků vám pomůžou úspěšně instalaci nebo upgradu sady Visual Studio, kontaktujte nás pomocí našich [ **živý chat** ](https://visualstudio.microsoft.com/vs/support/#talktous) požádejte o pomoc podporu možnost (jenom v angličtině).

## <a name="offline-installations"></a>Offline instalace

Tady je tabulka známých problémů a některá alternativní řešení, která vám můžou při vytváření [offline instalace](create-an-offline-installation-of-visual-studio.md) a následné instalaci z místního rozložení pomáhat.

| Problém       | Položka                   | Řešení |
| ----------- | ---------------------- | -------- |
| Uživatelé nebudou mít přístup k souborům. | oprávnění (ACL) | Ujistěte se, že upravit oprávnění (ACL), tak, aby se ostatním uživatelům udělit oprávnění ke čtení *před* sdílené složky offline instalace. |
| Nové úlohy, komponenty nebo jazyky nepodaří nainstalovat.  | `--layout`  | Ujistěte se, že máte přístup k Internetu, pokud nainstalujete z částečné rozložení a vyberte úlohy, komponenty nebo jazyky, které nebyly staženy dříve v tomto částečné rozložení. |

Další informace o řešení potíží s [instalací sítě](create-a-network-installation-of-visual-studio.md)najdete v tématu [řešení potíží souvisejících se sítí při instalaci nebo používání sady Visual Studio](troubleshooting-network-related-errors-in-visual-studio.md).

## <a name="installation-logs"></a>Protokoly instalace

Protokoly instalace jsou potřeba k odstranění většiny potíží instalace. Po odeslání chyby pomocí [nahlásit problém](../ide/how-to-report-a-problem-with-visual-studio.md) ve Visual Studio Installerem. Tyto protokoly jsou automaticky obsažené v sestavě.

Pokud budete kontaktovat Microsoft Support, možná budete muset poskytnout tyto protokoly instalace pomocí [sady Microsoft Visual Studio a nástroj pro shromažďování protokolů rozhraní .NET Framework](https://www.microsoft.com/download/details.aspx?id=12493). Nástroj shromažďování protokolů shromažďuje protokoly instalace ze všech komponent nainstalovaných aplikací Visual Studio, včetně .NET Framework, Windows SDK a SQL Server. Shromáždí se také informace o počítači inventář Instalační služby systému Windows a informace v protokolu událostí Windows pro instalační program sady Visual Studio, instalační služby systému Windows a nástroj Obnovení systému.

Shromažďování protokolů:

1. [Stáhněte si nástroj](https://www.microsoft.com/download/details.aspx?id=12493).
2. Otevřete příkazový řádek pro správu.
3. Spustit `Collect.exe` z adresáře, kam jste nástroj uložili.
4. Najít výsledný `vslogs.zip` ve vašich `%TEMP%` adresář, například `C:\Users\YourName\AppData\Local\Temp\vslogs.zip`.

> [!NOTE]
> Nástroj musí běžet pod stejným uživatelským účtem, který byl spuštěn neúspěšné instalace v části. Pokud nástroj spouštíte z jiného uživatelského účtu, nastavte `–user:<name>` možnost k určení uživatelského účtu, pod kterým byla spuštěna instalace, která selhala. Spustit `Collect.exe -?` z příkazového řádku správce pro další informace o možnostech a využití.

## <a name="live-help"></a>Živá pomáhat

Pokud řešení uvedené v této příručce pro řešení potíží vám jak úspěšně nainstalovat nebo upgradovat sadu Visual Studio, naší [ **živý chat** ](https://visualstudio.microsoft.com/vs/support/#talktous) požádejte o pomoc podporu možnost (jenom v angličtině).

## <a name="see-also"></a>Viz také:

* [Odebrat Visual Studio](remove-visual-studio.md)
* [Instalace a používání sady Visual Studio a služeb Azure za bránou firewall nebo proxy serverem](install-and-use-visual-studio-behind-a-firewall-or-proxy-server.md)
* [Nástroje pro zjišťování a správu instancí sady Visual Studio](tools-for-managing-visual-studio-instances.md)
* [Příručka pro správce aplikace Visual Studio](visual-studio-administrator-guide.md)
