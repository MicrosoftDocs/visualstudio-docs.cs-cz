---
title: Selhání vzdáleného přihlášení pracovní skupiny | Microsoft Docs
description: K této chybě může dojít při ladění z počítače v pracovní skupině a pokusu o připojení ke vzdálenému počítači.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 582b38b7a4115a140f6031b2d4c9227edfd438d1
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2021
ms.locfileid: "102146233"
---
# <a name="error-workgroup-remote-logon-failure"></a>Chyba: Selhání vzdáleného přihlášení pracovní skupiny
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

1. Otevřete okno **místní zásady zabezpečení** .

2. Rozbalte složku **místní zásady** .

3. Klikněte na **přiřazení uživatelských práv**.

4. Ve sloupci **zásady** poklikejte na **ladit programy** a zobrazte aktuální přiřazení místních zásad skupiny v dialogovém okně **Nastavení místních zásad zabezpečení** .

     ![Uživatelská práva místních zásad zabezpečení](../debugger/media/dbg_err_localsecuritypolicy_userrightsdebugprograms.png "DBG_ERR_LocalSecurityPolicy_UserRightsDebugPrograms")

5. Chcete-li přidat nové uživatele, klikněte na tlačítko **Přidat uživatele nebo skupinu** .

### <a name="to-change-the-sharing-and-security-model"></a>Změna modelu sdílení a zabezpečení

1. Otevřete okno **místní zásady zabezpečení** .

2. Rozbalte složku **místní zásady** .

3. Klikněte na možnost **Možnosti zabezpečení**.

4. Ve sloupci **zásady** poklikejte na **přístup k síti: sdílení a model zabezpečení místních účtů**.

5. V dialogovém okně **přístup k síti: model sdílení a zabezpečení místních účtů** změňte hodnotu na **klasický – místní uživatelé se ověřují jako sami** a klikněte na tlačítko **použít** .

     ![Možnosti zabezpečení místních zásad zabezpečení](../debugger/media/dbg_err_localsecuritypolicy_securityoptions_networkaccess.png "DBG_ERR_LocalSecurityPolicy_SecurityOptions_NetworkAccess")

## <a name="see-also"></a>Viz také
- [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
