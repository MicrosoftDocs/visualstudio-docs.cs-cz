---
title: Nepovedlo se připojit k Microsoft Visual Studio Sledování vzdáleného ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: d62e7ce1c419a9c53e40e1ecf2f71497d60d7a23
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477067"
---
# <a name="unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor"></a>Nepodařilo se připojit ke sledování Microsoft Visual Studio Remote Debugging Monitor.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chybová zpráva se zobrazí, když v dialogovém okně **připojit k procesu** zadáte neplatný název sady Visual Studio sledování vzdáleného ladění. Název Sledování vzdáleného ladění je obvykle stejný jako počítač, ke kterému se pokoušíte připojit pro vzdálené ladění. Tato zpráva může nastat, protože vzdálený počítač v síti neexistuje, sledování vzdáleného ladění není správně nastaveno na vzdáleném počítači, nebo je vzdálený počítač nepřístupný z důvodu problémů se sítí nebo přítomnosti brány firewall.  
  
> [!IMPORTANT]
> Pokud potřebujete další nápovědu, přečtěte si článek o způsobech, jak kontaktovat Microsoft, v článku kontaktujte [nás](../ide/talk-to-us.md) .  
  
## <a name="i-got-this-message-while-i-was-debugging-locally"></a>Tato zpráva zobrazila, když mi bylo místním ladění  
 Pokud se tato zpráva se zobrazuje při ladění místně, může být na straně zmocnitele antivirový software nebo brány firewall třetích stran. Visual Studio je 32bitová aplikace, aby používalo 64bitovou verzi vzdáleného ladicího programu pro ladění 64bitových aplikací. Dva procesy komunikovat prostřednictvím místní sítě v místním počítači. Žádný síťový provoz neopouští počítač, ale je možné, že by bezpečnostní software jiného výrobce mohl komunikaci zablokovat.  
  
 Následující části uvádějí některé z jiných důvodů, proč jste možná jste získali tuto zprávu, a můžete provést k vyřešení problému.  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Ujistěte se, že je aplikace Visual Studio Sledování vzdáleného ladění nainstalovaná a spuštěná na vzdáleném počítači. Informace o vzdáleném ladicím programu a jeho instalaci najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
- V aplikaci Visual Studio se podívejte na vlastnosti projektu (**projekt/vlastnosti/ladění**). Ujistěte se, že je **název vzdáleného serveru** správný.  
  
- Ověřte, jestli je vzdálený počítač přístupný v síti.  
  
## <a name="the-remote-machine-is-not-reachable"></a>Vzdálený počítač není dostupný  
 Zkuste provést [test testu](https://technet.microsoft.com/library/ee624059\(v=ws.10\).aspx) na vzdáleném počítači. Pokud neodpovídá na příkaz pro odeslání odpovědi na adresu příkazového testu, nástroje Remote Tools se nebudou moci připojit ani. Akci restartování vzdáleném počítači a v opačném případě se ujistěte, zda je správně nakonfigurován v síti.  
  
## <a name="the-version-of-the-remote-debugger-doesnt-match-the-version-of-visual-studio"></a>Verze vzdáleného ladicího programu se neshoduje s verzí sady Visual Studio.  
 Verze sady Visual Studio, které spouštíte místně musí odpovídat verzi sledování vzdáleného ladění, na kterém běží na vzdáleném počítači. Chcete-li to vyřešit, stáhněte a nainstalujte odpovídající verzi sledování vzdáleného ladění. Přejít na [předplatná sady Visual Studio](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015) a vyhledat správnou verzi vzdáleného ladicího programu pro vaši verzi sady Visual Studio.

## <a name="the-local-and-remote-machines-have-different-authentication-modes"></a>Místní a vzdálené počítače mají různá ověřovací režimy  

 Místní a vzdálené počítače musí používat stejný režim ověřování. Problém odstranit, ujistěte se, že oba počítače používají stejný režim ověřování. Režim ověřování na vzdáleném ladicím programu můžete změnit v dialogovém okně **Nástroje/možnosti** .  
  
 Další informace o režimech ověřování najdete v tématu [Přehled ověřování systému Windows](https://technet.microsoft.com/library/hh831472.aspx).  
  
## <a name="the-remote-debugger-is-running-under-a-different-user-account"></a>Vzdálený ladicí program je spuštěn pod účtem jiného uživatele  
 Tento problém můžete vyřešit jedním z následujících způsobů:  
  
- Můžete zastavit vzdáleného ladicího programu a restartujte ji pomocí účtu, který používáte v místním počítači.  
  
- Vzdálený ladicí program můžete spustit z příkazového řádku s parametrem **/allow \<username >** : `msvsmon /allow <username@computer>`  
  
- Uživatele můžete přidat do oprávnění vzdáleného ladicího programu (v okně vzdáleného ladicího programu, **nástroje/oprávnění**).  
  
- Pokud nemůžete použít metody v předchozích krocích, můžete povolit všem uživatelům provádět vzdálené ladění. V okně vzdáleného ladicího programu přejdete do dialogového okna **nástroje/Options** . Vyberete-li možnost **bez ověřování**, můžete zaškrtnout políčko **umožňuje všem uživatelům ladit**. Tuto možnost byste však použít jenom v případě, že máte žádný výběr nebo pokud jste v privátní síti.  
  
## <a name="the-firewall-on-the-remote-machine-doesnt-allow-incoming-connections-to-the-remote-debugger"></a>Brána firewall na vzdáleném počítači nepovoluje příchozí připojení ke vzdálenému ladicímu programu.  
 Brány firewall na počítači aplikace Visual Studio a brány firewall na vzdáleném počítači musí být nakonfigurovány umožňujícím komunikaci mezi Visual Studio a vzdálený ladicí program. Informace o portech, které používá vzdálený ladicí program, najdete v tématu [Přiřazení portů vzdáleného ladicího programu](../debugger/remote-debugger-port-assignments.md). Informace o konfiguraci brány Windows Firewall najdete v tématu [Konfigurace brány Windows Firewall pro vzdálené ladění](../debugger/configure-the-windows-firewall-for-remote-debugging.md).  
  
## <a name="anti-virus-software-is-blocking-the-connections"></a>Antivirový software blokuje připojení  
 Antivirový software Windows povoluje připojení vzdáleného ladicího programu, ale některé třetích stran antivirový software blokuje. V dokumentaci pro váš antivirový software a zjistěte, jak umožnit tato připojení.  
  
## <a name="network-security-policy-is-blocking-communication-between-the-remote-machine-and-visual-studio"></a>Zásady zabezpečení sítě blokuje komunikaci mezi vzdáleného počítače a sady Visual Studio  
 Kontrola zabezpečení vaší sítě, abyste měli jistotu, že neblokuje komunikaci. Další informace o zásadách zabezpečení sítě systému Windows najdete v tématu [Správa zabezpečení](https://msdn.microsoft.com/library/windows/desktop/ms721855\(v=vs.85\).aspx).  
  
## <a name="the-network-is-too-busy-to-support-remote-debugging"></a>Síť je příliš zaneprázdněn a nemůže podporovat vzdálené ladění  
 Budete muset provádět vzdálené ladění v jinou dobu nebo změnit plán práce v síti pro jiný čas.  
  
## <a name="more-help"></a>Další nápovědu  
 Pokud chcete získat další nápovědu ke vzdálenému ladicímu programu, včetně přepínačů příkazového řádku, otevřete v prohlížeči tyto informace:  
  
 **Res://C: \ program %2 0 soubory \ Microsoft %2 0 Visual %2 0 Studio% 2014.0 \ Common7 \ IDE \ Remote %2 0 Debugger \ x64 \ msvsmon. exe/help. htm**  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění](../debugger/remote-debugging.md)
