---
title: 'Chyba: Zdá se, že Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) na vzdáleném počítači neběží. | Dokumenty Microsoft'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.error.server_machine_no_default
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 86db9931-50e3-4095-b161-802ed8ef39c9
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 252ed59b5e2ace61e3529743d2d01afb4a4fb360
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51746342"
---
# <a name="error-the-microsoft-visual-studio-remote-debugging-monitor-msvsmonexe-does-not-appear-to-be-running-on-the-remote-computer"></a>Chyba: Zdá se, že Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) na vzdáleném počítači neběží.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chybová zpráva znamená, že Visual Studio nemůže najít správné instanci Visual Studio Remote Debugging Monitor na vzdáleném počítači. Pro vzdálené ladění pro práci, musí být nainstalován Visual Studio Remote Debugging Monitor. Informace o stažení a nastavení vzdáleného ladicího programu, najdete v části [nastavit Up the Remote Tools na zařízení](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
> [!IMPORTANT]
>  Pokud si myslíte, že tato zpráva zobrazila z důvodu chyby produktu, ohlaste prosím tento problém se sadou Visual Studio [poslat smajlíka](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Pokud potřebujete další pomoc, přečtěte si téma [kontaktujte nás](../ide/talk-to-us.md) způsoby, jak kontaktovat Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-in-visual-studio-2010-or-earlier"></a>Tato zpráva zobrazila, když mi bylo ladění v sadě Visual Studio 2010 nebo starší  
 Pokud je verze sady Visual Studio, kterou používáte Visual Studio 2010 nebo starší, může také tato chyba se zobrazí v případě, že sdílení souborů a tiskáren není povolená. Další informace o tomto problému najdete na verzi sady Visual Studio 2010 této dokumentace: [Chyba: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON. (EXE) zřejmě není spuštěn ve vzdáleném počítači. – Visual Studio 2010](https://msdn.microsoft.com/library/ms164726\(v=vs.100\).aspx)  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Tato zpráva zobrazila, když mi bylo místním ladění  
 Pokud se tato zpráva se zobrazuje při ladění místně, může být na straně zmocnitele antivirový software nebo brány firewall třetích stran. Visual Studio je 32bitová aplikace, aby používalo 64bitovou verzi vzdáleného ladicího programu pro ladění 64bitových aplikací. Dva procesy komunikovat prostřednictvím místní sítě v místním počítači. Žádný provoz nechá počítač, ale je možné, že zabezpečovací software třetí strany může blokovat komunikaci.  
  
 Následující části uvádějí některé z jiných důvodů, proč jste možná jste získali tuto zprávu, a můžete provést k vyřešení problému.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Vzdálený počítač není dostupný  
 Zkuste [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) vzdálený počítač. Pokud je odpověď na příkaz ping, nástroje pro vzdálenou nebude možné se připojit buď. Akci restartování vzdáleném počítači a v opačném případě se ujistěte, zda je správně nakonfigurován v síti.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu neodpovídá verzi sady Visual Studio  
 Verze sady Visual Studio, které spouštíte místně musí odpovídat verzi sledování vzdáleného ladění, na kterém běží na vzdáleném počítači. Chcete-li to vyřešit, stáhněte a nainstalujte odpovídající verzi sledování vzdáleného ladění. Přejděte [Download Center](http://www.microsoft.com/download) najít správnou verzi vzdáleného ladicího programu.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různá ověřovací režimy  
 Místní a vzdálené počítače musí používat stejný režim ověřování. Problém odstranit, ujistěte se, že oba počítače používají stejný režim ověřování. Další informace o režimech ověřování najdete v tématu [Přehled ověřování Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Vzdálený ladicí program je spuštěn pod účtem jiného uživatele  
 Tento problém můžete vyřešit jedním z následujících způsobů:  
  
-   Můžete zastavit vzdáleného ladicího programu a restartujte ji pomocí účtu, který používáte v místním počítači.  
  
-   Vzdálený ladicí program lze spustit z příkazového řádku pomocí **/ allow \<uživatelské jméno >** parametr: `msvsmon /allow <username@computer>`  
  
-   Je-li přidat uživatele na oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu **nástroje / oprávnění**).  
  
-   Pokud nemůžete použít metody v předchozích krocích, můžete povolit všem uživatelům provádět vzdálené ladění. V okně vzdáleného ladicího programu, pokračujte **Tools/Options** dialogového okna. Když vyberete **bez ověřování**, můžete zkontrolovat **dovolit ladění jakémukoliv uživateli**. Tuto možnost byste však použít jenom v případě, že máte žádný výběr nebo pokud jste v privátní síti.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Brány firewall na vzdáleném počítači nebude povolovat příchozí připojení vzdáleného ladicího programu  
 Brány firewall na počítači aplikace Visual Studio a brány firewall na vzdáleném počítači musí být nakonfigurovány umožňujícím komunikaci mezi Visual Studio a vzdálený ladicí program. Informace o portech používá vzdálený ladicí program najdete v tématu [přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows firewall najdete v tématu [konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení  
 Antivirový software Windows povoluje připojení vzdáleného ladicího programu, ale některé třetích stran antivirový software blokuje. V dokumentaci pro váš antivirový software a zjistěte, jak umožnit tato připojení.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokuje komunikaci mezi vzdáleného počítače a sady Visual Studio  
 Kontrola zabezpečení vaší sítě, abyste měli jistotu, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě Windows najdete v tématu [bezpečnostní správu](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněn a nemůže podporovat vzdálené ladění  
 Budete muset provádět vzdálené ladění v jinou dobu nebo změnit plán práce v síti pro jiný čas.  
  
## <a name="more-help"></a>Další nápovědu  
 Pomoc s více vzdáleného ladicího programu, včetně přepínače příkazového řádku, klikněte na tlačítko **Nápověda / využití** v okně vzdáleného ladicího programu. Pokud nemáte ji otevřete webovou stránku uvidíte tak, že zkopírujete následující řádek, který **Průzkumníka souborů** okna. (Je třeba nahradit \<instalačního adresáře sady Visual Studio > umístění instalace sady Visual Studio.)  
  
 res: / /*\<instalačního adresáře sady Visual Studio >* \Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm  
  
## <a name="see-also"></a>Viz také  
 [Chyby při vzdáleném ladění a jejich řešení](../debugger/remote-debugging-errors-and-troubleshooting.md)



