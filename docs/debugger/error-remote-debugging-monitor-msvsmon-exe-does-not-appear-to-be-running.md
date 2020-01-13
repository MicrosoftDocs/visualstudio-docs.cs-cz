---
title: 'Chyba: Zdá se, že Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) na vzdáleném počítači neběží.'
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.server_machine_no_default
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
ms.openlocfilehash: cc9558ff4d470d30df19ea5982eb6acbcc708eea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/13/2020
ms.locfileid: "75916264"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Chyba: Zdá se, že Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) na vzdáleném počítači neběží.
Tato chybová zpráva znamená, že Visual Studio nemůže najít správné instanci Visual Studio Remote Debugging Monitor na vzdáleném počítači. Pro vzdálené ladění pro práci, musí být nainstalován Visual Studio Remote Debugging Monitor. Informace o stažení a nastavení vzdáleného ladicího programu, najdete v části [vzdálené ladění](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Pokud se domníváte, že jste tuto zprávu dostali kvůli chybě produktu, [ohlaste prosím tento problém aplikaci Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Pokud potřebujete další pomoc, přečtěte si téma [kontaktujte nás](../ide/feedback-options.md) způsoby, jak kontaktovat Microsoft.

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Tato zpráva zobrazila, když mi bylo ladění v sadě Visual Studio 2010 nebo starší
 Pokud je verze sady Visual Studio, kterou používáte Visual Studio 2010 nebo starší, může také tato chyba se zobrazí v případě, že sdílení souborů a tiskáren není povolená. Další informace o tomto problému najdete na verzi sady Visual Studio 2010 této dokumentace: [Chyba: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON. (EXE) zřejmě není spuštěn ve vzdáleném počítači. – Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Tato zpráva zobrazila, když mi bylo místním ladění
 Pokud se tato zpráva se zobrazuje při ladění místně, může být na straně zmocnitele antivirový software nebo brány firewall třetích stran. Visual Studio je 32bitová aplikace, aby používalo 64bitovou verzi vzdáleného ladicího programu pro ladění 64bitových aplikací. Dva procesy komunikovat prostřednictvím místní sítě v místním počítači. Žádný provoz nechá počítač, ale je možné, že zabezpečovací software třetí strany může blokovat komunikaci.

 Následující části uvádějí některé z jiných důvodů, proč jste možná jste získali tuto zprávu, a můžete provést k vyřešení problému.

## <a name="the-remote-machine-is-not-reachable"></a>Vzdálený počítač není dostupný
 Zkuste [ping](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) vzdálený počítač. Pokud je odpověď na příkaz ping, nástroje pro vzdálenou nebude možné se připojit buď. Akci restartování vzdáleném počítači a v opačném případě se ujistěte, zda je správně nakonfigurován v síti.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu neodpovídá verzi sady Visual Studio
 Verze sady Visual Studio, které spouštíte místně musí odpovídat verzi sledování vzdáleného ladění, na kterém běží na vzdáleném počítači. Chcete-li to vyřešit, stáhněte a nainstalujte odpovídající verzi sledování vzdáleného ladění. Přejděte [Download Center](https://www.microsoft.com/download) najít správnou verzi vzdáleného ladicího programu.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různá ověřovací režimy
 Místní a vzdálené počítače musí používat stejný režim ověřování. Problém odstranit, ujistěte se, že oba počítače používají stejný režim ověřování. Další informace o režimech ověřování najdete v tématu [Přehled ověřování Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Vzdálený ladicí program je spuštěn pod účtem jiného uživatele
 Tento problém můžete vyřešit jedním z následujících způsobů:

- Můžete zastavit vzdáleného ladicího programu a restartujte ji pomocí účtu, který používáte v místním počítači.

- Vzdálený ladicí program lze spustit z příkazového řádku pomocí **/ allow \<uživatelské jméno >** parametr: `msvsmon /allow <username@computer>`

- Je-li přidat uživatele na oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu **nástroje > oprávnění**).

- Pokud nemůžete použít metody v předchozích krocích, můžete povolit všem uživatelům provádět vzdálené ladění. V okně vzdáleného ladicího programu, pokračujte **nástroje > Možnosti** dialogového okna. Když vyberete **bez ověřování**, můžete zkontrolovat **dovolit ladění jakémukoliv uživateli**. Tuto možnost byste však použít jenom v případě, že máte žádný výběr nebo pokud jste v privátní síti.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Brány firewall na vzdáleném počítači nebude povolovat příchozí připojení vzdáleného ladicího programu
 Brány firewall na počítači aplikace Visual Studio a brány firewall na vzdáleném počítači musí být nakonfigurovány umožňujícím komunikaci mezi Visual Studio a vzdálený ladicí program. Informace o portech používá vzdálený ladicí program najdete v tématu [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows firewall najdete v tématu [konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení
 Antivirový software Windows povoluje připojení vzdáleného ladicího programu, ale některé třetích stran antivirový software blokuje. V dokumentaci pro váš antivirový software a zjistěte, jak umožnit tato připojení.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokuje komunikaci mezi vzdáleného počítače a sady Visual Studio
 Kontrola zabezpečení vaší sítě, abyste měli jistotu, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě Windows najdete v tématu [nastavení zásad zabezpečení](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněn a nemůže podporovat vzdálené ladění
 Budete muset provádět vzdálené ladění v jinou dobu nebo změnit plán práce v síti pro jiný čas.

## <a name="more-help"></a>Další nápovědu
 Pomoc s více vzdáleného ladicího programu, včetně přepínače příkazového řádku, klikněte na tlačítko **Nápověda > využití** v okně vzdáleného ladicího programu. Pokud nemáte ji otevřete webovou stránku uvidíte tak, že zkopírujete následující řádek, který **Průzkumníka souborů** okna. (Je třeba nahradit \<instalačního adresáře sady Visual Studio > umístění instalace sady Visual Studio.)

 res: / / *\<instalačního adresáře sady Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Viz také:
- [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)
