---
title: Ověřování protokolem Kerberos se nezdařilo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
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
ms.openlocfilehash: ae81d7503ef325da24db7d553a98837f97a96168
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852690"
---
# <a name="error-kerberos-authentication-failed"></a>Chyba: Ověření protokolem Kerberos se nezdařilo.
Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:

```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.
```

 K této chybě dochází, pokud Sledování vzdáleného ladění Visual Studio běží pod účtem místní systém nebo síťová služba. V jednom z těchto účtů musí vzdálený ladicí program navázat připojení pro ověřování protokolem Kerberos, aby komunikoval zpátky s hostitelským počítačem ladicího programu sady Visual Studio.

 Ověřování protokolem Kerberos není v těchto podmínkách k dispozici:

- Cílový počítač nebo hostitelský počítač ladicího programu se nachází v pracovní skupině, nikoli v doméně.

   \- ani

- Protokol Kerberos byl na řadiči domény zakázán.

  Pokud není k dispozici ověřování protokolu Kerberos, změňte účet, který se používá ke spuštění sady Visual Studio Sledování vzdáleného ladění. Postup najdete v tématu [Chyba: služba Visual Studio Remote Debugger v cílovém počítači se nemůže připojit zpět k tomuto počítači](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).

  Pokud jsou oba počítače připojeny ke stejné doméně a stále se zobrazí tato zpráva, ověřte, zda DNS na cílovém počítači správně překládá název hostitelského počítače ladicího programu. Podívejte se na následující postup.

### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Postup správného překladu DNS v cílovém počítači na název hostitelského počítače ladicího programu

1. V cílovém počítači otevřete nabídku **Start** , přejděte na položku **příslušenství** a poté klikněte na položku **příkazový řádek**.

2. V okně **příkazového řádku** zadejte:

    ```cmd
    ping <debugger_host_computer_name>
    ```

3. První řádek `ping` odpovědi zobrazuje úplný název počítače a IP adresu vrácenou DNS pro zadaný počítač.

4. Na hostitelském počítači ladicího programu otevřete okno **příkazového řádku** a spusťte příkaz `ipconfig` .

5. Porovnejte hodnoty IP adres.

## <a name="see-also"></a>Viz také
- [Chyby a řešení potíží se vzdáleným laděním](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Vzdálené ladění](../debugger/remote-debugging.md)
