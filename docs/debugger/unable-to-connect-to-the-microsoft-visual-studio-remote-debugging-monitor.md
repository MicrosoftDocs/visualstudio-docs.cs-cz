---
title: Nelze se připojit k Microsoft Visual Studio sledování vzdáleného ladění | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/24/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 1096188a6cf6be34d56c6330d588e56e0c306581
ms.sourcegitcommit: 50b19010b2e2b4736835350710e2edf93b980b56
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/10/2018
ms.locfileid: "49073932"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nepodařilo se připojit ke sledování Microsoft Visual Studio Remote Debugging Monitor.
Tato zpráva může dojít, protože sledování vzdáleného ladění není správně nastavena na vzdáleném počítači nebo vzdálený počítač není dostupný kvůli potížím se sítí nebo přítomnost brány firewall.
  
> [!IMPORTANT]
>  Pokud si myslíte, že tato zpráva zobrazila z důvodu chyby produktu, [tento problém nahlásit](../ide/how-to-report-a-problem-with-visual-studio-2017.md) do sady Visual Studio. Pokud potřebujete další pomoc, přečtěte si téma [kontaktujte nás](../ide/talk-to-us.md) způsoby, jak kontaktovat Microsoft.

## <a name="specificerrors"></a>Co je Podrobná chybová zpráva?

`Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor` Zprávy je obecný. Obvykle podrobnější zprávu je součástí řetězec chyby a, které mohou pomoci identifikovat příčinu problému nebo vyhledejte přesnější opravu. Tady je několik běžných chybových zpráv, které jsou připojeny k hlavním chybová zpráva:

- [Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl vyřešit zadaný název počítače](#cannot_connect)
- [Vzdálený ladící program odmítl žádost o připojení](#rejected)
- [Neplatný přístup k umístění v paměti](#invalid_access)
- [Není k dispozici žádný server se zadaným názvem na vzdáleném počítači spuštěny](#no_server)
- [Název požadovaného byl platný, ale nebyla nalezena žádná data požadovaného typu](#valid_name)
- [Visual Studio Remote Debugger na cílovém počítači se nemůže připojit zpět k tomuto počítači.](#cant_connect_back)
- [Přístup byl odepřen](#access_denied)
- [Došlo k chybě konkrétní balíček zabezpečení](#security_package)

## <a name="cannot_connect"></a> Ladicí program se nemůže připojit ke vzdálenému počítači. Ladicí program nemohl vyřešit zadaný název počítače

Proveďte následující kroky:

1. Ujistěte se, že zadejte platný název počítače a číslo portu **připojit k procesu** dialogové okno nebo ve vlastnostech projektu (Chcete-li nastavit vlastnosti, přečtěte si téma [tyto kroky](#server_incorrect)). Název počítače musí být v následujícím formátu:

    `computername:port`

    > [!NOTE]
    > Číslo portu musí odpovídat [port číslo vzdáleného ladícího programu](../debugger/remote-debugger-port-assignments.md), což *musí běžet* na cílovém počítači.

2. Pokud název počítače nefunguje, zkuste IP adresu a číslo portu místo.

3. Ujistěte se, že verze vzdálený ladicí program běžící na cílovém počítači shoduje s vaší verzí sady Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, najdete v článku [vzdálené ladění](../debugger/remote-debugging.md).

    > [!TIP]
    > Pokud při připojování k procesu a úspěšně připojit, ale proces, kterému chcete nevidíte, vyberte **Zobrazit procesy všech uživatelů zaškrtávací políčko**. Tím se zobrazí procesy Pokud jsou připojené pod účtem jiného uživatele.

4. Pokud tuto chybu nelze vyřešit pomocí těchto kroků, přečtěte si téma [vzdálený počítač není dosažitelný](#dns).

## <a name="rejected"></a> Vzdálený ladící program odmítl žádost o připojení

V **připojit k procesu** dialogové okno pole nebo ve vlastnostech projektu, ujistěte se, že název vzdáleného počítače a číslo portu odpovídá na název a port číslo zobrazené v okně vzdáleného ladicího programu. Pokud správné, opravte a zkuste to znovu.

Pokud tyto hodnoty jsou správné a zpráva uvádí **ověřování Windows** režimu, zkontrolujte, jestli je vzdálený ladicí program v správný režim ověřování (**nástroje > Možnosti**).

## <a name="invalid_access"></a> Neplatný přístup k umístění v paměti

Došlo k vnitřní chybě. Restartujte sadu Visual Studio a zkuste to znovu.

## <a name="no_server"></a> Není k dispozici žádný server se zadaným názvem na vzdáleném počítači spuštěny

Visual Studio nemohla připojit k vzdálený ladicí program. Tato zpráva může mít několik příčin:

- Vzdálený ladicí program může běžet pod účtem jiného uživatele. Zobrazit [tyto kroky](#user_accounts)

- Port je blokována v bráně firewall. Ujistěte se, že brána firewall je [není blokuje vaši žádost](#firewall), zejména v případě, že používáte bránu firewall jiného dodavatele.

- Verze vzdáleného ladicího programu se neshoduje s Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, najdete v článku [vzdálené ladění](../debugger/remote-debugging.md)


## <a name="valid_name"></a> Název požadovaného byl platný, ale nebyla nalezena žádná data požadovaného typu

Existuje vzdáleném počítači, ale nelze se připojit k vzdálený ladicí program sady Visual Studio. Tato zpráva může mít několik příčin:

- DNS problém brání připojení. Zobrazit [tyto kroky](#dns).

- Vzdálený ladicí program může běžet pod účtem jiného uživatele. Postupujte podle [tyto kroky](#user_accounts).

- Port je blokována v bráně firewall. Ujistěte se, že brána firewall je [není blokuje vaši žádost](#firewall), zejména v případě, že používáte bránu firewall jiného dodavatele.

- Verze vzdáleného ladicího programu se neshoduje s Visual Studio. Chcete-li získat správnou verzi vzdáleného ladicího programu, najdete v článku [vzdálené ladění](../debugger/remote-debugging.md).

## <a name="cant_connect_back"></a> Visual Studio Remote Debugger na cílovém počítači se nemůže připojit zpět k tomuto počítači.

Vzdálený ladicí program může běžet pod účtem jiného uživatele. Vzdálený ladicí program, otevřete **nástroje > oprávnění** přidejte uživatele na oprávnění vzdáleného ladicího programu. Další informace najdete v tématu [vzdálený ladicí program je spuštěn pod jiným uživatelským účtem](#user_accounts).

Pokud chybová zpráva uvádí, brána firewall, brána firewall v místním počítači, asi blokuje komunikaci ze vzdáleného počítače zpět do sady Visual Studio. Zobrazit [tyto kroky](#firewall).

## <a name="access_denied"></a> Přístup byl odepřen

Tato chyba může zobrazit, pokud se pokusíte ladit ve vzdáleném počítači 64-bit z 32bitového počítače (nepodporuje se).

## <a name="security_package"></a> Došlo k chybě konkrétní balíček zabezpečení

To může být starší verze problém specifická pro Windows XP a Windows 7. Najdete v tomto [informace](https://stackoverflow.com/questions/4786016/unable-to-connect-to-the-microsoft-remote-debugging-monitor-a-security-package). 

## <a name="causes-and-recommendations"></a>Způsobí, že a doporučení

### <a name="dns"></a> Vzdálený počítač není dostupný 

Pokud se nemůžete připojit pomocí názvu vzdáleného počítače, zkuste místo toho použít IP adresu. Můžete použít `ipconfig` v příkazovém řádku na vzdáleném počítači k získání adresy IPv4. Pokud používáte soubor HOSTS, ověřte, zda je správně nakonfigurována.

Pokud se nezdaří, zkontrolujte, že vzdálený počítač přístupný v síti ([ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) vzdálený počítač). Vzdálené ladění přes Internet není podporováno, s výjimkou v některých scénářích Microsoft Azure.
  
### <a name="server_incorrect"></a> Název serveru je nesprávný nebo se softwarem třetích stran zasahovala do vzdáleného ladicího programu

V sadě Visual Studio podívejte se na vlastnosti projektu a ujistěte se, že je název serveru správný. Najdete v tématech [jazyka C# a Visual Basic](../debugger/remote-debugging-csharp.md#remote_csharp) a [C++](../debugger/remote-debugging-cpp.md#remote_cplusplus). Pro technologii ASP.NET, otevřete **vlastnosti / Web / servery** nebo **vlastnosti / ladění** v závislosti na typu vašeho projektu.

> [!NOTE]
> Pokud se připojujete k procesu, nepoužívají se vzdálené nastavení ve vlastnostech projektu.

Pokud je název serveru správný, antivirový software nebo brány firewall třetích stran může blokovat vzdálený ladicí program. Při místním ladění tomu může dojít, protože Visual Studio je 32bitová aplikace, aby používalo 64bitovou verzi vzdáleného ladicího programu pro ladění 64bitových aplikací. 32bitové a 64bitové procesy komunikovat prostřednictvím místní sítě v místním počítači. Žádné síťové přenosy nechá počítač, ale je možné, že zabezpečovací software třetí strany může blokovat komunikaci.

### <a name="user_accounts"></a> Vzdálený ladicí program je spuštěn pod účtem jiného uživatele 

Vzdálený ladicí program, ve výchozím nastavení, přijímal pouze připojení od uživatele, kteří spustili vzdálený ladicí program a členy skupiny Administrators. Další uživatelé musí explicitně udělit oprávnění. 
 
Tento problém můžete vyřešit jedním z následujících způsobů:  

-   Přidejte uživatele sady Visual Studio na oprávnění vzdáleného ladicího programu (v okně vzdáleného ladícího programu zvolte **nástroje > oprávnění**).

-   Na vzdáleném počítači restartujte vzdálený ladicí program v rámci stejného uživatelského účtu a heslo, které používáte na počítači aplikace Visual Studio.

    > [!NOTE]
    > Pokud používáte vzdálený ladicí program na vzdáleném serveru, klikněte pravým tlačítkem na aplikaci vzdálený ladicí program a zvolte **spustit jako správce** (nebo můžete spustit vzdálený ladicí program jako službu). Pokud vy nespouštíte na vzdáleném serveru, stačí spusťte normálně.
  
-   Vzdálený ladicí program lze spustit z příkazového řádku pomocí **/ allow \<uživatelské jméno >** parametr: `msvsmon /allow <username@computer>`. 
  
-   Alternativně můžete povolit všem uživatelům provádět vzdálené ladění. V okně vzdáleného ladicího programu, pokračujte **nástroje > Možnosti** dialogového okna. Když vyberete **bez ověřování**, můžete zkontrolovat **dovolit ladění jakémukoliv uživateli**. Tato možnost však doporučujeme jenom v případě selhání další možnosti, nebo pokud jste v privátní síti.

### <a name="firewall"></a> Brány firewall na vzdáleném počítači nebude povolovat příchozí připojení vzdáleného ladicího programu  
 Brány firewall na počítači aplikace Visual Studio a brány firewall na vzdáleném počítači musí být nakonfigurovány umožňujícím komunikaci mezi Visual Studio a vzdálený ladicí program. Informace o portech používá vzdálený ladicí program najdete v tématu [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows firewall najdete v tématu [konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).
  
### <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu neodpovídá verzi sady Visual Studio  
 Verze sady Visual Studio, které spouštíte místně musí odpovídat verzi sledování vzdáleného ladění, na kterém běží na vzdáleném počítači. Chcete-li to vyřešit, stáhněte a nainstalujte odpovídající verzi sledování vzdáleného ladění. Chcete-li získat správnou verzi vzdáleného ladicího programu, najdete v článku [vzdálené ladění](../debugger/remote-debugging.md).
  
### <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různá ověřovací režimy  
 Místní a vzdálené počítače musí používat stejný režim ověřování. Problém odstranit, ujistěte se, že oba počítače používají stejný režim ověřování. Můžete změnit režim ověřování. V okně vzdáleného ladicího programu, pokračujte **nástroje > Možnosti** dialogové okno.
  
 Další informace o režimech ověřování najdete v tématu [Přehled ověřování Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).   
  
### <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení  
 Antivirový software Windows povoluje připojení vzdáleného ladicího programu, ale některé třetích stran antivirový software blokuje. V dokumentaci pro váš antivirový software a zjistěte, jak umožnit tato připojení.  
  
### <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokuje komunikaci mezi vzdáleného počítače a sady Visual Studio  
 Kontrola zabezpečení vaší sítě, abyste měli jistotu, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě Windows najdete v tématu [nastavení zásad zabezpečení](/windows/device-security/security-policy-settings/security-policy-settings).  
  
### <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněn a nemůže podporovat vzdálené ladění  
 Budete muset provádět vzdálené ladění v jinou dobu nebo změnit plán práce v síti pro jiný čas.  
  
## <a name="more-help"></a>Další nápovědu  
 Pomoc s více vzdálený ladicí program, otevřete stránku nápovědy vzdáleného ladicího programu (**Nápověda > využití** v vzdálený ladicí program).
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)
