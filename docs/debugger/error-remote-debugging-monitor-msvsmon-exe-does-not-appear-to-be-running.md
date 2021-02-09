---
title: Zdá se, že na vzdáleném počítači neběží sledování vzdáleného ladění sady Microsoft Visual Studio (MSVSMON.EXE)
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 8ecb8a0a3c725403d57769090229f690281026a1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871504"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Chyba: Zdá se, že Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) na vzdáleném počítači neběží.
Tato chybová zpráva znamená, že Visual Studio nemohlo najít správnou instanci sady Visual Studio Sledování vzdáleného ladění na vzdáleném počítači. Aby mohla vzdálené ladění fungovat, musí být nainstalovaná aplikace Visual Studio Sledování vzdáleného ladění. Informace o stažení a nastavení vzdáleného ladicího programu naleznete v tématu [vzdálené ladění](../debugger/remote-debugging.md).

> [!IMPORTANT]
> Pokud se domníváte, že jste tuto zprávu dostali kvůli chybě produktu, [ohlaste prosím tento problém aplikaci Visual Studio](../ide/how-to-report-a-problem-with-visual-studio.md). Pokud potřebujete další nápovědu, přečtěte si článek o způsobech, jak kontaktovat Microsoft, v článku kontaktujte [nás](../ide/feedback-options.md) .

## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Zobrazila se mi zpráva při ladění v aplikaci Visual Studio 2010 nebo starší
 Pokud je verze sady Visual Studio, kterou používáte, sady Visual Studio 2010 nebo starší, může se tato chyba zobrazit také v případě, že není povoleno sdílení souborů a tiskáren. Další informace o tomto problému naleznete v této dokumentaci ve verzi Visual Studio 2010: [Chyba: Microsoft Visual Studio sledování vzdáleného ladění (MSVSMON.EXE) na vzdáleném počítači pravděpodobně neběží. – Visual Studio 2010](/previous-versions/visualstudio/visual-studio-2010/ms164726(v=vs.100))

## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Zobrazila se mi tato zpráva při místním ladění
 Pokud se tato zpráva zobrazuje při místním ladění, může být antivirový software nebo brána firewall jiného výrobce viny. Visual Studio je 32 aplikace, takže používá 64 verzi vzdáleného ladicího programu k ladění aplikací v 64. Tyto dva procesy komunikují pomocí místní sítě v rámci místního počítače. Žádný provoz neopouští počítač, ale je možné, že by bezpečnostní software jiného výrobce mohl komunikaci zablokovat.

 V následujících částech jsou uvedeny některé další důvody, proč se vám může zobrazit tato zpráva a co můžete udělat k vyřešení problému.

## <a name="the-remote-machine-is-not-reachable"></a>Vzdálený počítač není dosažitelný.
 Zkuste provést [test testu](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/ee624059(v=ws.10)) na vzdáleném počítači. Pokud neodpovídá na příkaz pro odeslání odpovědi na adresu příkazového testu, nástroje Remote Tools se nebudou moci připojit ani. Zkuste restartovat vzdálený počítač a jinak se ujistěte, že je správně nakonfigurovaný v síti.

## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu se neshoduje s verzí sady Visual Studio.
 Verze sady Visual Studio, kterou používáte místně, musí odpovídat verzi sledování vzdáleného ladění, která běží na vzdáleném počítači. Chcete-li tento problém vyřešit, Stáhněte a nainstalujte si verzi sledování vzdáleného ladění. Pro vyhledání správné verze vzdáleného ladicího programu navštivte [Centrum stahování](https://www.microsoft.com/download) .

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají odlišné režimy ověřování.
 Místní a vzdálené počítače musí používat stejný režim ověřování. Pokud to chcete opravit, ujistěte se, že oba počítače používají stejný režim ověřování. Další informace o režimech ověřování najdete v tématu [Přehled ověřování systému Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831472(v=ws.11)).

## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Vzdálený ladicí program je spuštěný pod jiným uživatelským účtem.
 Můžete to vyřešit jedním z následujících způsobů:

- Můžete zastavit vzdálený ladicí program a restartovat ho s účtem, který používáte v místním počítači.

- Vzdálený ladicí program můžete spustit z příkazového řádku s parametrem **/Allow \<username>** :`msvsmon /allow <username@computer>`

- Uživatele můžete přidat do oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu, **nástroje > oprávnění**).

- Pokud nemůžete použít metody v předchozích krocích, můžete každému uživateli povolit vzdálené ladění. V okně vzdáleného ladicího programu přejdete do dialogového okna **Možnosti nástrojů >** . Vyberete-li možnost   **bez ověřování**, můžete zaškrtnout políčko **umožňuje všem uživatelům ladit**. Tuto možnost byste ale měli použít jenom v případě, že nemáte žádnou volbu, nebo pokud jste v privátní síti.

## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Brána firewall na vzdáleném počítači nepovoluje příchozí připojení ke vzdálenému ladicímu programu.
 Brána firewall na počítači sady Visual Studio a brána firewall na vzdáleném počítači musí být nakonfigurované tak, aby umožňovaly komunikaci mezi Visual Studio a vzdáleným ladícím programem. Informace o portech, které používá vzdálený ladicí program, najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows Firewall najdete v tématu [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).

## <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení.
 Antivirový software systému Windows umožňuje připojení vzdáleného ladicího programu, ale antivirový software jiných výrobců je může blokovat. Podívejte se na dokumentaci k antivirovému softwaru, abyste zjistili, jak tato připojení povolíte.

## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokují komunikaci mezi vzdáleným počítačem a sady Visual Studio.
 Zkontrolujte zabezpečení sítě, abyste se ujistili, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě Windows najdete v tématu [nastavení zásad zabezpečení](/windows/device-security/security-policy-settings/security-policy-settings).

## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněna, aby podporovala vzdálené ladění.
 Je možné, že budete muset vzdálené ladění provést v jinou dobu nebo znovu naplánovat práci v síti na jinou dobu.

## <a name="more-help"></a>Další informace
 Pokud chcete získat další nápovědu ke vzdálenému ladicímu programu, včetně přepínačů příkazového řádku, klikněte na **nápověda > využití** v okně vzdáleného ladicího programu. Pokud ho ještě nemáte, můžete zobrazit webovou stránku tak, že zkopírujete následující řádek do okna  **Průzkumníka souborů** . (Musíte nahradit \<Visual Studio installation directory> umístěním instalace sady Visual Studio.)

 res:// *\<Visual Studio installation directory>* \Common7\IDE\Remote% 20Debugger\x64\msvsmon.exe/help.htm

## <a name="see-also"></a>Viz také
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)
