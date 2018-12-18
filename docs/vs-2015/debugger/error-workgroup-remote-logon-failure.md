---
title: 'Chyba: Selhání přihlášení pracovní skupiny vzdálené | Dokumentace Microsoftu'
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
- vs.debug.error.workgroup_remote_logon_failure
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- logon failure, remote debugging
- remote debugging, logon failure
ms.assetid: 7be2c5bb-40fe-48d6-8cfc-c231fbd3d64e
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13531d3a9dd5249b0c96ddc4e8f736c20696303
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51723662"
---
# <a name="error-workgroup-remote-logon-failure"></a>Chyba: Selhání vzdáleného přihlášení pracovní skupiny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Přečte tuto chybu:  
  
 Chyba přihlášení: Neznámé uživatelské jméno nebo špatné heslo  
  
 **Příčina**  
  
 Této chybě může dojít při ladění z počítače v pracovní skupině a zkuste se připojit ke vzdálenému počítači. Mezi možné příčiny patří:  
  
-   Neexistuje žádný účet s odpovídajícím názvem a hesel na vzdáleném počítači.  
  
-   Pokud počítač Visual Studio a vzdálený počítač jsou v pracovních skupinách, této chybě může dojít z důvodu výchozí **místní zásady zabezpečení** nastavení na vzdáleném počítači. Ve výchozím nastavení **místní zásady zabezpečení** nastavení je **Guest - místní uživatelé ověřit jako hosta**. Chcete-li ladit na tento instalační program, je nutné změnit nastavení ve vzdáleném počítači, na **Classic - místní uživatelé ověřováni pomocí svých účtů**.  
  
> [!NOTE]
>  Musíte být správcem provádět následující úlohy.  
  
### <a name="to-open-the-local-security-policy-window"></a>Chcete-li otevřít okno místní zásady zabezpečení  
  
1.  Spustit **secpol.msc** modul snap-in konzoly Microsoft Management Console. Zadejte secpol.msc ve službě Windows search pole spustit Windows nebo na příkazovém řádku.  
  
### <a name="to-add-user-rights-assignments"></a>Chcete-li přidat přiřazení uživatelských práv  
  
1.  Otevřete místní  
  
2.  Otevřít **místní zásady zabezpečení** okna.  
  
3.  Rozbalte **místní zásady** složky.  
  
4.  Klikněte na tlačítko **přiřazení uživatelských práv**.  
  
5.  V **zásady** sloupce, klikněte dvakrát na **ladit programy** zobrazíte aktuální přiřazení zásad místní skupiny v **nastavení místních zásad zabezpečení** dialogové okno.  
  
     ![Zabezpečení místní zásady uživatelská práva](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6.  Pokud chcete přidat nové uživatele, klikněte na tlačítko **přidat uživatele nebo skupinu** tlačítko.  
  
### <a name="to-change-the-sharing-and-security-model"></a>Chcete-li změnit sdílení a modelu zabezpečení  
  
1.  Otevřít **místní zásady zabezpečení** okna.  
  
2.  Rozbalte **místní zásady** složky.  
  
3.  Klikněte na tlačítko **možnosti zabezpečení**.  
  
4.  V **zásady** sloupce, klikněte dvakrát na **přístup k síti: model sdílení a zabezpečení pro místní účty**.  
  
5.  V **přístup k síti: model sdílení a zabezpečení pro místní účty** dialogové okno pole, změňte hodnotu na **Classic - místní uživatelé ověřováni pomocí svých účtů** a klikněte na tlačítko **použít**tlačítko.  
  
     ![Možnosti místního zabezpečení zásad zabezpečení](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění chyby a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)



