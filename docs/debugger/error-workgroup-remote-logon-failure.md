---
title: 'Chyby: Selhání přihlášení pracovní skupiny vzdálené | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- CSharp
- VB
- FSharp
- JScript
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 60cee4e6bdb4ebab925325695eb9ad6813929879
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2018
ms.locfileid: "31481993"
---
# <a name="error-workgroup-remote-logon-failure"></a>Chyba: Selhání vzdáleného přihlášení pracovní skupiny
Přečte tuto chybu:  
  
 Přihlašovací chyba: Neznámé uživatelské jméno nebo nesprávné heslo  
  
 **Příčina**  
  
 Této chybě může dojít, když jsou ladění z počítače v pracovní skupině a zkuste se připojit ke vzdálenému počítači. Možné příčiny:  
  
-   Neexistuje žádný účet odpovídající název a heslo ve vzdáleném počítači.  
  
-   Pokud v sadě Visual Studio počítači i vzdálený počítač jsou v pracovních skupinách, této chybě může dojít z důvodu výchozí **místní zásady zabezpečení** nastavení ve vzdáleném počítači. Výchozí nastavení **místní zásady zabezpečení** nastavení je **hosta pouze – místní uživatelé ověřit jako hosta**. K ladění na tento instalační program, musíte změnit nastavení ve vzdáleném počítači k **Classic - místní uživatelé ověřováni pomocí svých účtů**.  
  
> [!NOTE]
>  Musíte být správce provádět následující úlohy.  
  
### <a name="to-open-the-local-security-policy-window"></a>Otevřete okno místní zásady zabezpečení  
  
1.  Spuštění **secpol.msc** modul snap-in konzoly Microsoft Management Console. Zadejte secpol.msc ve Windows search je pole spustit Windows nebo na příkazovém řádku.  
  
### <a name="to-add-user-rights-assignments"></a>Chcete-li přidat přiřazení uživatelských práv  
  
1.  Otevřete **místní zásady zabezpečení** okno.  
  
2.  Rozbalte **místní zásady** složky.  
  
3.  Klikněte na tlačítko **přiřazení uživatelských práv**.  
  
4.  V **zásad** sloupce, klikněte dvakrát na **ladění programů** zobrazení aktuální přiřazení zásad místní skupiny v **nastavení místních zásad zabezpečení** dialogové okno.  
  
     ![Zabezpečení místní zásady uživatelská práva](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
5.  Chcete-li přidat nové uživatele, klikněte na tlačítko **přidat uživatele nebo skupinu** tlačítko.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Chcete-li změnit sdílení a Model zabezpečení  
  
1.  Otevřete **místní zásady zabezpečení** okno.  
  
2.  Rozbalte **místní zásady** složky.  
  
3.  Klikněte na tlačítko **možnosti zabezpečení**.  
  
4.  V **zásad** sloupce, klikněte dvakrát na **přístup k síti: model sdílení a zabezpečení pro místní účty**.  
  
5.  V **přístup k síti: model sdílení a zabezpečení pro místní účty** dialogové okno pole, změňte hodnotu na **Classic - místní uživatelé ověřováni pomocí svých účtů** a klikněte na tlačítko **použít**tlačítko.  
  
     ![Možnosti zabezpečení místní zásady zabezpečení](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění chyby a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)