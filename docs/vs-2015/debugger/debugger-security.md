---
title: Zabezpečení ladicího programu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], security
- debugger, security
- security [Visual Studio], debugging best practices
ms.assetid: d4fc3c43-e844-419c-8dbb-551cc2a9b09e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7f8166c7aea86b0decad84631f8c98054ee69253
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51765359"
---
# <a name="debugger-security"></a>Zabezpečení ladicího programu
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Možnost ladit jiným procesem poskytuje velmi široký mocniny, ke kterým by jinak máte, zejména v případě vzdáleného ladění. Škodlivý ladicí program může způsobit poškození rozšířených na počítači, který se právě ladí.  
  
 Nicméně mnoho vývojářů není dobré si uvědomit, že ohrožení zabezpečení můžete také tok v opačném směru. Je možné, škodlivý kód v laděném procesu ohrozit zabezpečení počítače ladění: počet musí mít ochranu proti zneužití zabezpečení.  
  
## <a name="security-best-practices"></a>Doporučené postupy zabezpečení  
 Existuje implicitní důvěryhodnost poměr mezi kódem, který ladíte a ladicí program. Pokud jste ochotní něco ladit, byste měli také natolik, abyste ho spustit. Dolní řádek je, že je budete moci důvěřovat, co ladění. Případě, že důvěřujete jeho, pak by neměl ladit nebo by ho ladit z počítače, který si můžete dovolit ohrozit a v izolovaném prostředí.  
  
 Pokud chcete snížit potenciální prostor pro napadení, musí se zakázat ladění na počítačích v produkčním prostředí. Ze stejného důvodu by nikdy být povoleno ladění po neomezenou dobu.  
  
### <a name="managed-debugging-security"></a>Spravované ladění zabezpečení  
 Tady jsou některé obecná doporučení, které se vztahují na všechny spravované ladění.  
  
- Buďte opatrní při připojování k procesu je nedůvěryhodný uživatel: Pokud tak učiníte, můžete předpokládat, že je důvěryhodný. Při pokusu o připojení k procesu je nedůvěryhodný uživatel, se zobrazí potvrzovací dialogové okno s upozorněním zabezpečení s dotazem, jestli se má připojit k procesu. "Důvěryhodných uživatelů" zahrnout, a sadu standardních uživatelů obvykle definovány na počítače, které mají nainstalováno, například rozhraní .NET Framework **aspnet**, **localsystem**, **networkservice**, a **localservice**. Další informace najdete v tématu [upozornění zabezpečení: připojení k procesu vlastněnému nedůvěryhodným uživatelským může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md).  
  
- Buďte opatrní při stahování projekt Internetu a načítají do [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. To je velmi riskantní provést i bez ladění. Když toto provedete, jsou za předpokladu, že projekt a kód, který obsahuje jsou důvěryhodné.  
  
  Další informace najdete v tématu [ladění spravovaného kódu](../debugger/debugging-managed-code.md).  
  
### <a name="remote-debugging-security"></a>Zabezpečení vzdálené ladění  
 Místní ladění je obecně bezpečnější než vzdálené ladění. Vzdálené ladění zvyšuje celkový počet, který můžete zkoumat.  
  
 Visual Studio Remote Debugging Monitor (msvsmon.exe) se používá ve vzdálené ladění a existuje několik doporučení zabezpečení pro jeho konfiguraci. Preferovaný způsob, jak konfigurovat režim ověřování je ověřování Windows, protože není bezpečné a režim bez ověřování.  
  
 ![Dialogové okno s chybou](../debugger/media/dbg-err-remotepermissionschanged.png "DBG_ERR_RemotePermissionsChanged")  
  
 Při použití režimu ověřování Windows mějte na paměti, že udělení oprávnění nedůvěryhodné uživatele pro připojení k msvsmon je nebezpečné, protože uživateli je udělen všechna oprávnění v počítači...  
  
 Není Neznámý procesu ve vzdáleném počítači ladění: neexistují potenciální zneužití, který může mít vliv na počítači spuštěná ladicí program, nebo které by mohlo ohrozit msvsmon.exe Visual Studio Remote Debugging Monitor. Pokud musíte ladit naprosto neznámý proces, zkuste místním ladění a zachovat všechny potenciální hrozby lokalizovány pomocí brány firewall.  
  
 Další informace najdete v tématu [vzdálené ladění](../debugger/remote-debugging.md).  
  
### <a name="web-services-debugging-security"></a>Ladění zabezpečení webových služeb  
 Je bezpečnější, chcete-li ladit místně, ale od té doby budete pravděpodobně nemají [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nainstalovaný na webovém serveru, místní ladění nemusí být praktické. Obecně platí ladění webových služeb se prováděla vzdáleně, s výjimkou během vývoje, tak doporučení pro zabezpečení vzdálené ladění také použít k ladění webových služeb. Tady jsou některé další osvědčené postupy. Další informace najdete v tématu [ladění webových služeb XML](http://msdn.microsoft.com/en-us/c900b137-9fbd-4f59-91b5-9c2c6ce06f00).  
  
-   Nepovolujte ladění na webovém serveru, který byl napaden.  
  
-   Ujistěte se, že víte, že je před její ladění zabezpečený webový server. Pokud si nejste jisti, že je zabezpečené, není ho ladit.  
  
-   Buďte opatrní hlavně Pokud ladíte webové služby, který je přístupný na Internetu.  
  
### <a name="external-components"></a>Externí komponenty  
 Mějte na paměti ze stavu důvěryhodnosti externí komponenty, které aplikace komunikuje se službou, zejména v případě, že nezapsal kód. Také být vědomi komponenty, která [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nebo použít ladicí program.  
  
### <a name="symbols-and-source-code"></a>Symbolů a zdrojového kódu  
 Dvě [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] nástroje, které vyžadují přemýšlení o zabezpečení jsou následující:  
  
- Zdrojový Server, který vám poskytne verze zdrojového kódu z úložiště zdrojového kódu. Je vhodné, pokud nemá aktuální verzi zdrojový kód aplikace. [Upozornění zabezpečení: Ladicí program musí spustit nedůvěryhodný příkaz](../debugger/security-warning-debugger-must-execute-untrusted-command.md).  
  
- Server symbolů, který slouží k poskytování symboly potřebné k ladění selhání během volání systému.  
  
  Zobrazit [zadání symbolu (.pdb) a zdrojové soubory](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
## <a name="see-also"></a>Viz také  
 [Nastavení ladicího programu a příprava](../debugger/debugger-settings-and-preparation.md)   
 [Základy ladicího programu](../debugger/debugger-basics.md)   
 [Upozornění zabezpečení: Připojení k procesu, jehož vlastníkem je nedůvěryhodný uživatel, může být nebezpečné. Pokud následující informace vypadají podezřele nebo si nejste jisti, nepřipojujte k tomuto procesu](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)   
 [Upozornění zabezpečení: Ladicí program musí spustit nedůvěryhodný příkaz.](../debugger/security-warning-debugger-must-execute-untrusted-command.md)





