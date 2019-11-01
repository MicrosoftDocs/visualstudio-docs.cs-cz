---
title: Nepovedlo se připojit k Microsoft Visual Studio Sledování vzdáleného ladění | Microsoft Docs
ms.date: 08/24/2017
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
ms.openlocfilehash: a2a3f4429341ecdba26dab2f95415332f9cb2eca
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187262"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nepodařilo se připojit ke sledování Microsoft Visual Studio Remote Debugging Monitor.
Tato zpráva může být způsobena tím, že sledování vzdáleného ladění není správně nastaveno na vzdáleném počítači nebo je vzdálený počítač nepřístupný z důvodu problémů se sítí nebo přítomnosti brány firewall.

> [!IMPORTANT]
> Pokud se domníváte, že jste tuto zprávu obdrželi kvůli chybě produktu, [ohlaste prosím tento problém](../ide/how-to-report-a-problem-with-visual-studio.md) aplikaci Visual Studio. Pokud potřebujete další nápovědu, přečtěte si článek o způsobech, jak kontaktovat Microsoft, v článku kontaktujte [nás](../ide/feedback-options.md) .

## <a name="specificerrors"></a>Jaká je podrobná chybová zpráva?

Zpráva `Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` je obecná. V řetězci chyby je obvykle obsažena konkrétnější zpráva, která vám může pomoct identifikovat příčinu problému nebo vyhledat přesnější opravu. Tady je několik nejběžnějších chybových zpráv, které se připojují k hlavní chybové zprávě:

- [Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl přeložit zadaný název počítače.](#cannot_connect)
- [Vzdálený ladicí program odmítl žádost o připojení.](#rejected)
- [Neplatný přístup k umístění v paměti](#invalid_access)
- [Na vzdáleném počítači není spuštěn žádný server se zadaným názvem.](#no_server)
- [Požadovaný název byl platný, ale nebyla nalezena žádná data požadovaného typu.](#valid_name)
- [Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači.](#cant_connect_back)
- [Přístup byl odepřen](#access_denied)
- [Došlo k chybě specifického balíčku zabezpečení.](#security_package)

## <a name="cannot_connect"></a>Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl přeložit zadaný název počítače.

Vyzkoušejte tyto kroky:

1. Nezapomeňte zadat platný název počítače a číslo portu v dialogovém okně **připojit k procesu** nebo ve vlastnostech projektu (pro nastavení vlastností se podívejte na [tyto kroky](#server_incorrect)). Název počítače musí být v následujícím formátu:

    `computername:port`

    > [!NOTE]
    > Číslo portu se musí shodovat s [číslem portu vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md), který *musí být spuštěný* na cílovém počítači.

2. Pokud název počítače nefunguje, zkuste místo toho použít IP adresu a číslo portu.

3. Ujistěte se, že verze vzdáleného ladicího programu běžícího na cílovém počítači odpovídá vaší verzi sady Visual Studio. Správnou verzi vzdáleného ladicího programu najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

    > [!TIP]
    > Pokud se k procesu připojujete a úspěšně jste se připojili, ale nevidíte požadovaný proces, zaškrtněte políčko **Zobrazit procesy všech uživatelů**. Tím se zobrazí procesy, pokud jste připojeni pod jiným uživatelským účtem.

4. Pokud tyto kroky tuto chybu nevyřešily, přečtěte si téma [vzdálený počítač není dostupný](#dns).

## <a name="rejected"></a>Vzdálený ladicí program odmítl žádost o připojení.

V dialogovém okně **připojit k procesu** nebo ve vlastnostech projektu se ujistěte, že název vzdáleného počítače a číslo portu se shodují s názvem a číslem portu zobrazeným v okně vzdáleného ladicího programu. Pokud je nesprávná, opravte je a zkuste to znovu.

Pokud jsou tyto hodnoty správné a zpráva uvádí režim **ověřování systému Windows** , ověřte, že je vzdálený ladicí program ve správném režimu ověřování (**Nástroje > Možnosti**).

## <a name="invalid_access"></a>Neplatný přístup k umístění v paměti

Došlo k vnitřní chybě. Restartujte Visual Studio a zkuste to znovu.

## <a name="no_server"></a>Na vzdáleném počítači není spuštěn žádný server se zadaným názvem.

Visual Studio se nemohlo připojit ke vzdálenému ladicímu programu. Tato zpráva může nastat z několika důvodů:

- Vzdálený ladicí program může běžet pod jiným uživatelským účtem. Zobrazit [tyto kroky](#user_accounts)

- Port je zablokován v bráně firewall. Ujistěte se, že brána firewall [neblokuje vaši žádost](#firewall), zejména pokud používáte bránu firewall jiného výrobce.

- Verze vzdáleného ladicího programu neodpovídá aplikaci Visual Studio. Správnou verzi vzdáleného ladicího programu najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="valid_name"></a>Požadovaný název byl platný, ale nebyla nalezena žádná data požadovaného typu.

Vzdálený počítač existuje, ale Visual Studio se nemůže připojit ke vzdálenému ladicímu programu. Tato zpráva může nastat z několika důvodů:

- Problém se službou DNS brání v připojení. Podívejte se na [tyto kroky](#dns).

- Vzdálený ladicí program může běžet pod jiným uživatelským účtem. Postupujte podle [těchto kroků](#user_accounts).

- Port je zablokován v bráně firewall. Ujistěte se, že brána firewall [neblokuje vaši žádost](#firewall), zejména pokud používáte bránu firewall jiného výrobce.

- Verze vzdáleného ladicího programu neodpovídá aplikaci Visual Studio. Správnou verzi vzdáleného ladicího programu najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a>Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači.

Vzdálený ladicí program může běžet pod jiným uživatelským účtem. Ve vzdáleném ladicím programu otevřete **nástroje > oprávnění** , aby bylo možné přidat uživatele do oprávnění vzdáleného ladicího programu. Další informace najdete v tématu [vzdálený ladicí program běží pod jiným uživatelským účtem](#user_accounts).

Pokud chybová zpráva také zmiňuje bránu firewall, brána firewall v místním počítači může zabránit komunikaci ze vzdáleného počítače zpět do sady Visual Studio. Podívejte se na [tyto kroky](#firewall).

## <a name="access_denied"></a>Přístup byl odepřen

Tato chyba se může zobrazit, pokud se pokusíte ladit na 64ém vzdáleném počítači z 32 počítače (Nepodporováno).

## <a name="security_package"></a>Došlo k chybě specifického balíčku zabezpečení.

Může se jednat o starší problém, který je specifický pro systémy Windows XP a Windows 7. Podívejte se na tyto [informace](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package).

## <a name="causes-and-recommendations"></a>Příčiny a doporučení

### <a name="dns"></a>Vzdálený počítač není dosažitelný.

Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste místo toho použít IP adresu. K získání adresy IPv4 můžete použít `ipconfig` na příkazovém řádku na vzdáleném počítači. Pokud používáte soubor hostitelů, ověřte, zda je správně nakonfigurován.

Pokud se to nepovede, ověřte, jestli je vzdálený počítač přístupný v síti (na vzdáleném počítači[otestujete test](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) ). Vzdálené ladění přes Internet se nepodporuje, s výjimkou některých Microsoft Azurech scénářů.

### <a name="server_incorrect"></a>Název serveru je nesprávný nebo software jiného výrobce nekoliduje se vzdáleným ladicím programem.

V aplikaci Visual Studio se podívejte na vlastnosti projektu a ujistěte se, že je název serveru správný. Viz témata pro [ C# a Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) a [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). V případě ASP.NET otevřete **vlastnosti, webové/servery** nebo **Vlastnosti/ladění** v závislosti na typu projektu.

> [!NOTE]
> Pokud se k procesu připojujete, není použito vzdálené nastavení ve vlastnostech projektu.

Pokud je název serveru správný, může vzdálený ladicí program blokovat antivirový software nebo brána firewall jiného výrobce. Při ladění místně to může nastat, protože Visual Studio je 32 aplikace, takže používá 64 verzi vzdáleného ladicího programu k ladění 64 bitů aplikací. 32 a 64 procesy navzájem komunikují pomocí místní sítě v rámci místního počítače. Žádný síťový provoz neopouští počítač, ale je možné, že by bezpečnostní software jiného výrobce mohl komunikaci zablokovat.

### <a name="user_accounts"></a>Vzdálený ladicí program je spuštěný pod jiným uživatelským účtem.

Vzdálený ladicí program ve výchozím nastavení akceptuje pouze připojení od uživatele, který spustil vzdálený ladicí program a členy skupiny Administrators. Dalším uživatelům musí být explicitně uděleno oprávnění.

Můžete to vyřešit jedním z následujících způsobů:

- Přidejte uživatele sady Visual Studio do oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu vyberte možnost **nástroje > oprávnění**).

- Na vzdáleném počítači restartujte vzdálený ladicí program pod stejným uživatelským účtem a heslem, které používáte v počítači se systémem Visual Studio.

    > [!NOTE]
    > Pokud používáte vzdálený ladicí program na vzdáleném serveru, klikněte pravým tlačítkem na aplikaci vzdáleného ladicího programu a vyberte **Spustit jako správce** (nebo můžete spustit vzdálený ladicí program jako službu). Pokud ho nepoužíváte na vzdáleném serveru, stačí ho spustit normálně.

- Vzdálený ladicí program můžete spustit z příkazového řádku s parametrem **/allow \<username >** : `msvsmon /allow <username@computer>`.

- Případně můžete všem uživatelům povolit vzdálené ladění. V okně vzdáleného ladicího programu přejdete do dialogového okna **Možnosti nástrojů >** . Vyberete-li možnost **bez ověřování**, můžete zaškrtnout políčko **umožňuje všem uživatelům ladit**. Tuto možnost byste však měli vyzkoušet pouze v případě, že ostatní možnosti selžou, nebo pokud jste v privátní síti.

### <a name="firewall"></a>Brána firewall na vzdáleném počítači nepovoluje příchozí připojení ke vzdálenému ladicímu programu.
 Brána firewall na počítači sady Visual Studio a brána firewall na vzdáleném počítači musí být nakonfigurované tak, aby umožňovaly komunikaci mezi Visual Studio a vzdáleným ladícím programem. Informace o portech, které používá vzdálený ladicí program, najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows Firewall najdete v tématu [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu se neshoduje s verzí sady Visual Studio.
 Verze sady Visual Studio, kterou používáte místně, musí odpovídat verzi sledování vzdáleného ladění, která běží na vzdáleném počítači. Chcete-li tento problém vyřešit, Stáhněte a nainstalujte si verzi sledování vzdáleného ladění. Správnou verzi vzdáleného ladicího programu najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají odlišné režimy ověřování.
 Místní a vzdálené počítače musí používat stejný režim ověřování. Pokud to chcete opravit, ujistěte se, že oba počítače používají stejný režim ověřování. Režim ověřování můžete změnit. V okně vzdáleného ladicího programu přejdete do dialogového okna **Možnosti nástrojů >** .

 Další informace o režimech ověřování najdete v tématu [Přehled ověřování systému Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

### <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení.
 Antivirový software systému Windows umožňuje připojení vzdáleného ladicího programu, ale antivirový software jiných výrobců je může blokovat. Podívejte se na dokumentaci k antivirovému softwaru, abyste zjistili, jak tato připojení povolíte.

### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokují komunikaci mezi vzdáleným počítačem a sady Visual Studio.
 Zkontrolujte zabezpečení sítě, abyste se ujistili, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě Windows najdete v tématu [nastavení zásad zabezpečení](/windows/device-security/security-policy-settings/security-policy-settings).

### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněna, aby podporovala vzdálené ladění.
 Je možné, že budete muset vzdálené ladění provést v jinou dobu nebo znovu naplánovat práci v síti na jinou dobu.

## <a name="more-help"></a>Další informace
 Pokud chcete získat další nápovědu ke vzdálenému ladicímu programu, otevřete stránku Nápověda ke vzdálenému ladicímu programu (**nápověda > používání** ve vzdáleném ladicím programu).

## <a name="see-also"></a>Viz také:
- [Vzdálené ladění](../debugger/remote-debugging.md)
