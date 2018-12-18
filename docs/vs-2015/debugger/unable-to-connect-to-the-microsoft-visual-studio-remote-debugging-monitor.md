---
title: Nelze se připojit k Microsoft Visual Studio sledování vzdáleného ladění | Dokumentace Microsoftu
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
- vs.debug.error.remote_debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: a1d959fc-3817-491c-831b-e6b768a3877a
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 139c650ac61b9312b069cc2e19fa66d3673ca30f
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733015"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nepodařilo se připojit ke sledování Microsoft Visual Studio Remote Debugging Monitor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chybová zpráva se zobrazí, když zadáte neplatný název v aplikaci Visual Studio Remote Debugging Monitor **připojit k procesu** dialogové okno. Název sledování vzdáleného ladění, je obvykle stejný jako počítač, který se pokoušíte připojit ke vzdálenému ladění. Tato zpráva může dojít, protože vzdálený počítač v síti neexistuje, sledování vzdáleného ladění není správně nastavena na vzdáleném počítači nebo vzdálený počítač není dostupný kvůli potížím se sítí nebo přítomnost brány firewall.  
  
> [!IMPORTANT]
>  Pokud si myslíte, že tato zpráva zobrazila z důvodu chyby produktu, ohlaste prosím tento problém se sadou Visual Studio [poslat smajlíka](http://msdn.microsoft.com/library/5cc9b67a-54d0-41b0-aa8f-80dff4475a6b). Pokud potřebujete další pomoc, přečtěte si téma [kontaktujte nás](../ide/talk-to-us.md) způsoby, jak kontaktovat Microsoft.  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Tato zpráva zobrazila, když mi bylo místním ladění  
 Pokud se tato zpráva se zobrazuje při ladění místně, může být na straně zmocnitele antivirový software nebo brány firewall třetích stran. Visual Studio je 32bitová aplikace, aby používalo 64bitovou verzi vzdáleného ladicího programu pro ladění 64bitových aplikací. Dva procesy komunikovat prostřednictvím místní sítě v místním počítači. Žádné síťové přenosy nechá počítač, ale je možné, že zabezpečovací software třetí strany může blokovat komunikaci.  
  
 Následující části uvádějí některé z jiných důvodů, proč jste možná jste získali tuto zprávu, a můžete provést k vyřešení problému.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Ujistěte se, že je Visual Studio Remote Debugging Monitor na vzdáleném počítači nainstalovaná a spuštěná. Informace o vzdáleného ladicího programu a její instalaci najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
-   V sadě Visual Studio, podívejte se na vlastnosti projektu (**projekt / vlastnosti / ladění**). Ujistěte se, **název vzdáleného serveru** je správná.  
  
-   Ověřte, že vzdálený počítač je přístupný v síti.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Vzdálený počítač není dostupný  
 Zkuste [ping](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) vzdálený počítač. Pokud je odpověď na příkaz ping, nástroje pro vzdálenou nebude možné se připojit buď. Akci restartování vzdáleném počítači a v opačném případě se ujistěte, zda je správně nakonfigurován v síti.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu neodpovídá verzi sady Visual Studio  
 Verze sady Visual Studio, které spouštíte místně musí odpovídat verzi sledování vzdáleného ladění, na kterém běží na vzdáleném počítači. Chcete-li to vyřešit, stáhněte a nainstalujte odpovídající verzi sledování vzdáleného ladění. Přejděte [Download Center](http://www.microsoft.com/download) najít správnou verzi vzdáleného ladicího programu.  
  
## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různá ověřovací režimy  
 Místní a vzdálené počítače musí používat stejný režim ověřování. Problém odstranit, ujistěte se, že oba počítače používají stejný režim ověřování. Můžete změnit na vzdálený ladicí program v režimu ověřování **Nástroje / možnosti** dialogového okna.  
  
 Další informace o režimech ověřování najdete v tématu [Přehled ověřování Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
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
 Pomoc s více vzdáleného ladicího programu, včetně přepínače příkazového řádku, otevřete v prohlížeči následující:  
  
 **res://C:\Program%20Files\Microsoft%20Visual%20Studio%2014.0\Common7\IDE\Remote%20Debugger\x64\msvsmon.exe/help.htm**  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)



