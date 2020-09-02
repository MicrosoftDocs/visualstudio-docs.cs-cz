---
title: 'Chyba: selhání vzdáleného přihlášení pracovní skupiny | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 09f018982b81535ae23eafe7158aa88c0b6b08a7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64798713"
---
# <a name="error-workgroup-remote-logon-failure"></a>Chyba: Selhání vzdáleného přihlášení pracovní skupiny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Tato chyba čte:  
  
 Chyba přihlášení: neznámé uživatelské jméno nebo špatné heslo  
  
 **Příčina**  
  
 K této chybě může dojít při ladění z počítače v pracovní skupině a pokusu o připojení ke vzdálenému počítači. Mezi možné příčiny patří:  
  
- Ve vzdáleném počítači není žádný účet se shodným jménem a heslem.  
  
- Pokud je počítač se systémem Visual Studio i vzdálený počítač v pracovních skupinách, k této chybě může dojít z důvodu výchozího nastavení **místních zásad zabezpečení** na vzdáleném počítači. Výchozí nastavení **místních zásad zabezpečení** je **jenom hosté – místní uživatelé se ověřují jako host**. Chcete-li provést ladění v této instalaci, je třeba změnit nastavení na vzdáleném počítači na **klasický – místní uživatelé se ověřují jako sami**.  
  
> [!NOTE]
> Chcete-li provést následující úkoly, musíte být správcem.  
  
### <a name="to-open-the-local-security-policy-window"></a>Otevření okna místní zásady zabezpečení  
  
1. Spusťte modul snap-in **secpol. msc** Microsoft Management Console. Zadejte secpol. msc ve Windows Search, v poli Windows Run nebo na příkazovém řádku.  
  
### <a name="to-add-user-rights-assignments"></a>Přidání přiřazení uživatelských práv  
  
1. Otevřete Loca  
  
2. Otevřete okno **místní zásady zabezpečení** .  
  
3. Rozbalte složku **místní zásady** .  
  
4. Klikněte na **přiřazení uživatelských práv**.  
  
5. Ve sloupci **zásady** poklikejte na **ladit programy** a zobrazte aktuální přiřazení místních zásad skupiny v dialogovém okně **Nastavení místních zásad zabezpečení** .  
  
     ![Uživatelská práva místních zásad zabezpečení](../debugger/media/dbg-err-localsecuritypolicy-userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")  
  
6. Chcete-li přidat nové uživatele, klikněte na tlačítko **Přidat uživatele nebo skupinu** .  
  
### <a name="to-change-the-sharing-and-security-model"></a>Změna modelu sdílení a zabezpečení  
  
1. Otevřete okno **místní zásady zabezpečení** .  
  
2. Rozbalte složku **místní zásady** .  
  
3. Klikněte na možnost **Možnosti zabezpečení**.  
  
4. Ve sloupci **zásady** poklikejte na **přístup k síti: sdílení a model zabezpečení místních účtů**.  
  
5. V dialogovém okně **přístup k síti: model sdílení a zabezpečení místních účtů** změňte hodnotu na **klasický – místní uživatelé se ověřují jako sami** a klikněte na tlačítko **použít** .  
  
     ![Možnosti zabezpečení místních zásad zabezpečení](../debugger/media/dbg-err-localsecuritypolicy-securityoptions-networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")  
  
## <a name="see-also"></a>Viz také  
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
