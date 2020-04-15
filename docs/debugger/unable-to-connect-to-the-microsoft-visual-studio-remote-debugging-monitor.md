---
title: Nelze se připojit k programu vzdáleného ladění sady Microsoft Visual Studio | Dokumenty společnosti Microsoft
ms.date: 04/14/2020
ms.topic: reference
f1_keywords:
- vs.debug.error.remote_debug
- vs.debug.error.firewall.remotemachine
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: d509292bc3c7a909289abf0c73babccfead31532
ms.sourcegitcommit: cc58ca7ceae783b972ca25af69f17c9f92a29fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/15/2020
ms.locfileid: "81385402"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nepodařilo se připojit ke sledování Microsoft Visual Studio Remote Debugging Monitor.
Tato zpráva může nastat, protože monitor vzdáleného ladění není správně nastaven ve vzdáleném počítači nebo je vzdálený počítač nepřístupný z důvodu problémů se sítí nebo přítomnosti brány firewall.

> [!IMPORTANT]
> Pokud se domníváte, že jste obdrželi tuto zprávu z důvodu chyby produktu, [nahlaste tento problém](../ide/how-to-report-a-problem-with-visual-studio.md) aplikaci Visual Studio. Pokud potřebujete další pomoc, [přečtěte si informace o způsobech,](../ide/feedback-options.md) jak kontaktovat Microsoft.

## <a name="what-is-the-detailed-error-message"></a><a name="specificerrors"></a>Co je podrobná chybová zpráva?

Zpráva `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` je obecná. Obvykle konkrétnější zpráva je součástí chybového řetězce a které vám mohou pomoci identifikovat příčinu problému nebo vyhledat přesnější opravu. Zde je několik běžných chybových zpráv, které jsou připojeny k hlavní chybové zprávě:

- [Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl přeložit zadaný název počítače.](#cannot_connect)
- [Požadavek na připojení byl odmítnut vzdáleným ladicím programem.](#rejected)
- [Neplatný přístup k umístění paměti](#invalid_access)
- [Ve vzdáleném počítači není spuštěn žádný server se zadaným názvem.](#no_server)
- [Požadovaný název byl platný, ale nebyla nalezena žádná data požadovaného typu.](#valid_name)
- [Vzdálený ladicí program sady Visual Studio v cílovém počítači se nemůže připojit zpět k tomuto počítači.](#cant_connect_back)
- [Přístup byl odepřen.](#access_denied)
- [Došlo k chybě specifické pro bezpečnostní balíček.](#security_package)

## <a name="the-debugger-cannot-connect-to-the-remote-computer-the-debugger-was-unable-to-resolve-the-specified-computer-name"></a><a name="cannot_connect"></a>Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl přeložit zadaný název počítače.

Vyzkoušejte tyto kroky:

1. Ujistěte se, že jste v dialogovém okně **Připojit k procesu** nebo ve vlastnostech projektu zadali platný název počítače a číslo portu (Nastavení vlastností naleznete v [těchto krocích).](#server_incorrect) Název počítače musí mít následující formát:

    `computername:port`

    > [!NOTE]
    > Číslo portu se musí shodovat s [číslem portu vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md), který *musí být spuštěn* v cílovém počítači.

2. Pokud název počítače nefunguje, zkuste místo toho adresu IP a číslo portu.

3. Ujistěte se, že verze vzdáleného ladicího programu spuštěného v cílovém počítači odpovídá vaší verzi sady Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, [přečtěte si část Vzdálené ladění](../debugger/remote-debugging.md).

    > [!TIP]
    > Pokud se připojujete k procesu a úspěšně se připojujete, ale nevidíte požadovaný proces, zaškrtněte **políčko Zobrazit procesy od všech uživatelů**. Zobrazí se procesy, pokud jste připojeni pod jiným uživatelským účtem.

4. Pokud tyto kroky tuto chybu nevyřeší, [přečtěte si](#dns)téma Vzdálený počítač není dostupný .

## <a name="connection-request-was-rejected-by-the-remote-debugger"></a><a name="rejected"></a>Požadavek na připojení byl odmítnut vzdáleným ladicím programem.

V dialogovém okně **Připojit k procesu** nebo ve vlastnostech projektu zkontrolujte, zda název vzdáleného počítače a číslo portu odpovídají názvu a číslu portu zobrazenému v okně vzdáleného ladicího programu. Pokud je nesprávná, opravte ji a akci opakujte.

Pokud jsou tyto hodnoty správné a zpráva uvádí režim **ověřování systému Windows,** zkontrolujte, zda je vzdálený ladicí program ve správném režimu ověřování **(Nástroje > možnosti**).

## <a name="the-connection-with-the-remote-endpoint-was-terminated"></a><a name="connection_terminated"></a>Připojení se vzdáleným koncovým bodem bylo ukončeno.

Pokud ladíte aplikaci služby Azure App Service, zkuste místo **připojit k procesu**použít příkaz [Připojit ladicí program](../debugger/remote-debugging-azure.md#remote_debug_azure_app_service) z Průzkumníka cloudu nebo Průzkumníka serveru .

Pokud používáte **připojit k procesu** ladění:

1. V dialogovém okně **Připojit k procesu** nebo ve vlastnostech projektu zkontrolujte, zda název vzdáleného počítače a číslo portu odpovídají názvu a číslu portu zobrazenému v okně vzdáleného ladicího programu. Pokud je nesprávná, opravte ji a akci opakujte.

2. Podrobnější informace, které vám pomohou problém vyřešit, naleznete v protokolu aplikace na serveru (Prohlížeč událostí v systému Windows).

3. V opačném případě zkuste restartovat visual studio s oprávněními správce a akci opakujte.

## <a name="invalid-access-to-memory-location"></a><a name="invalid_access"></a>Neplatný přístup k umístění paměti

Došlo k vnitřní chybě. Restartujte visual studio a akci opakujte.

## <a name="there-is-no-server-by-the-specified-name-running-on-the-remote-computer"></a><a name="no_server"></a>Ve vzdáleném počítači není spuštěn žádný server se zadaným názvem.

Visual Studio se nemůže připojit ke vzdálenému ladicímu programu. Tato zpráva může dojít z několika důvodů:

- Vzdálený ladicí program může být spuštěn pod jiným uživatelským účtem. Podívejte se [na tyto kroky](#user_accounts)

- Port je blokován v bráně firewall. Ujistěte se, že brána firewall [neblokuje váš požadavek](#firewall), zejména pokud používáte bránu firewall jiného výrobce.

- Verze vzdáleného ladicího programu neodpovídá sadě Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, [přečtěte si část Vzdálené ladění](../debugger/remote-debugging.md).

## <a name="the-requested-name-was-valid-but-no-data-of-the-requested-type-was-found"></a><a name="valid_name"></a>Požadovaný název byl platný, ale nebyla nalezena žádná data požadovaného typu.

Vzdálený počítač existuje, ale visual studio se nemůže připojit ke vzdálenému ladicímu programu. Tato zpráva může dojít z několika důvodů:

- Problém se službou DNS brání připojení. Podívejte se [na tyto kroky](#dns).

- Vzdálený ladicí program může být spuštěn pod jiným uživatelským účtem. Postupujte [takto](#user_accounts).

- Port je blokován v bráně firewall. Ujistěte se, že brána firewall [neblokuje váš požadavek](#firewall), zejména pokud používáte bránu firewall jiného výrobce.

- Verze vzdáleného ladicího programu neodpovídá sadě Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, [přečtěte si část Vzdálené ladění](../debugger/remote-debugging.md).

## <a name="the-visual-studio-remote-debugger-on-the-target-computer-cannot-connect-back-to-this-computer"></a><a name="cant_connect_back"></a>Vzdálený ladicí program sady Visual Studio v cílovém počítači se nemůže připojit zpět k tomuto počítači.

Vzdálený ladicí program může být spuštěn pod jiným uživatelským účtem. Ve vzdáleném ladicím programu otevřete **nástroje > oprávnění a** přidejte uživatele do oprávnění vzdáleného ladicího programu. Další informace naleznete [v tématu Vzdálený ladicí program je spuštěn pod jiným uživatelským účtem](#user_accounts).

Pokud se chybová zpráva také zmiňuje bránu firewall, brána firewall v místním počítači může bránit komunikaci ze vzdáleného počítače zpět do sady Visual Studio. Podívejte se [na tyto kroky](#firewall).

## <a name="access-denied"></a><a name="access_denied"></a>Přístup byl odepřen.

Tato chyba se může zobrazit, pokud se pokusíte ladit v 64bitovém vzdáleném počítači z 32bitového počítače (není podporováno).

## <a name="a-security-package-specific-error-occurred"></a><a name="security_package"></a>Došlo k chybě specifické pro bezpečnostní balíček.

To může být starší problém specifický pro Windows XP a Windows 7. Viz tyto [informace](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Příčiny a doporučení

### <a name="the-remote-machine-is-not-reachable"></a><a name="dns"></a>Vzdálený počítač není dostupný

Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste místo toho použít adresu IP. Pomocí příkazového řádku ve vzdáleném počítači můžete `ipconfig` získat adresu IPv4. Pokud používáte soubor HOSTS, ověřte, zda je správně nakonfigurován.

Pokud se to nepodaří, ověřte, zda je vzdálený počítač přístupný v síti[(příkaz ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) na vzdáleném počítači). Vzdálené ladění přes Internet není podporováno, s výjimkou některých scénářů Microsoft Azure.

### <a name="the-server-name-is-incorrect-or-third-party-software-is-interfering-with-the-remote-debugger"></a><a name="server_incorrect"></a>Název serveru je nesprávný nebo software jiného výrobce narušuje vzdálený ladicí program.

V sadě Visual Studio se podívejte na vlastnosti projektu a ujistěte se, že název serveru je správný. Viz témata pro [C# a Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) a [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Pro ASP.NET otevřete **vlastnosti / web / servery** nebo **vlastnosti / ladění** v závislosti na typu projektu.

> [!NOTE]
> Pokud se připojujete k procesu, vzdálená nastavení ve vlastnostech projektu se nepoužívají.

Pokud je název serveru správný, je možné, že vzdálený ladicí program blokuje antivirový software nebo brána firewall jiného výrobce. Při místním ladění k tomu může dojít, protože Visual Studio je 32bitová aplikace, takže používá 64bitovou verzi vzdáleného ladicího programu k ladění 64bitových aplikací. 32bitové a 64bitové procesy komunikují pomocí místní sítě v místním počítači. Žádný síťový provoz neopouští počítač, ale je možné, že bezpečnostní software třetích stran může komunikaci zablokovat.

### <a name="the-remote-debugger-is-running-under-a-different-user-account"></a><a name="user_accounts"></a>Vzdálený ladicí program je spuštěn pod jiným uživatelským účtem.

Vzdálený ladicí program bude ve výchozím nastavení přijímat pouze připojení od uživatele, který spustil vzdálený ladicí program, a členů skupiny Administrators. Dalším uživatelům musí být explicitně udělena oprávnění.

Můžete to vyřešit jedním z následujících způsobů:

- Přidejte uživatele sady Visual Studio do oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu zvolte **Nástroje > Oprávnění).**

- Ve vzdáleném počítači restartujte vzdálený ladicí program pod stejným uživatelským účtem a heslem, které používáte v počítači sady Visual Studio.

    > [!NOTE]
    > Pokud používáte vzdálený ladicí program na vzdáleném serveru, klikněte pravým tlačítkem myši na aplikaci Vzdálený ladicí program a zvolte **Spustit jako správce** (Nebo můžete spustit vzdálený ladicí program jako službu). Pokud jej nepoužíváte na vzdáleném serveru, stačí jej spustit normálně.

- Vzdálený ladicí program můžete spustit z příkazového řádku s `msvsmon /allow <username@computer>`parametrem **/allow \<username>:** .

- Případně můžete povolit libovolnému uživateli vzdálené ladění. V okně vzdáleného ladicího programu přejděte do dialogového okna **Nástroje > možnosti.** Pokud vyberete **možnost Žádné ověřování**, můžete zkontrolovat Možnost **Povolit ladění libovolného uživatele**. Tuto možnost byste však měli vyzkoušet pouze v případě, že ostatní možnosti se nezdaří nebo pokud jste v privátní síti.

### <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a><a name="firewall"></a>Brána firewall ve vzdáleném počítači neumožňuje příchozí připojení ke vzdálenému ladicímu programu
 Brána firewall v počítači sady Visual Studio a brána firewall ve vzdáleném počítači musí být nakonfigurována tak, aby umožňovala komunikaci mezi aplikací Visual Studio a vzdáleným ladicím programem. Informace o portech, které používá vzdálený ladicí program, naleznete v [tématu Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány firewall systému Windows naleznete [v tématu Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu neodpovídá verzi sady Visual Studio
 Verze sady Visual Studio, kterou používáte místně, musí odpovídat verzi vzdáleného ladicího monitoru spuštěného ve vzdáleném počítači. Chcete-li tento problém vyřešit, stáhněte a nainstalujte odpovídající verzi vzdáleného ladicího monitoru. Chcete-li získat správnou verzi vzdáleného ladicího programu, [přečtěte si část Vzdálené ladění](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různé režimy ověřování
 Místní a vzdálené počítače musí používat stejný režim ověřování. Chcete-li tento problém vyřešit, ujistěte se, že oba počítače používají stejný režim ověřování. Můžete změnit režim ověřování. V okně vzdáleného ladicího programu přejděte do dialogového okna **Nástroje > možnosti.**

 Další informace o režimech ověřování naleznete v tématu [Přehled ověřování systému Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení
 Antivirový software systému Windows umožňuje připojení vzdáleného ladicího programu, ale nějaký antivirový software jiných výrobců je může zablokovat. V dokumentaci k antivirovému softwaru zjistěte, jak tato připojení povolit.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokují komunikaci mezi vzdáleným počítačem a aplikací Visual Studio.
 Zkontrolujte zabezpečení sítě a ujistěte se, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě systému Windows naleznete v [tématu Nastavení zásad zabezpečení](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněna pro podporu vzdáleného ladění.
 Možná budete muset provést vzdálené ladění v jiném čase nebo přeplánovat práci v síti na jinou dobu.

## <a name="more-help"></a>Další nápověda
 Chcete-li získat další pomoc vzdáleného ladicího programu, otevřete stránku nápovědy vzdáleného ladicího programu **(Nápověda > použití** ve vzdáleném ladicím programu).

## <a name="see-also"></a>Viz také
- [Vzdálené ladění](../debugger/remote-debugging.md)
