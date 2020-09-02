---
title: 'Chyba: ověřování protokolu Kerberos nebylo úspěšné | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c18053f9-9074-4bc3-a8bf-13e4acbea921
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b5e85bc7a5bac87692448aab393056fa1db5edbd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "62535630"
---
# <a name="error-kerberos-authentication-failed"></a>Chyba: Ověření protokolem Kerberos se nezdařilo.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při pokusu o vzdálené ladění se může zobrazit následující chybová zpráva:  
  
```  
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos auythentication failed.  
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
  
    ```  
    ping <debugger_host_computer_name>  
    ```  
  
3. První řádek `ping` odpovědi zobrazuje úplný název počítače a IP adresu vrácenou DNS pro zadaný počítač.  
  
4. Na hostitelském počítači ladicího programu otevřete okno **příkazového řádku** a spusťte příkaz `ipconfig` .  
  
5. Porovnejte hodnoty IP adres.  
  
## <a name="see-also"></a>Viz také  
 [Chyby vzdáleného ladění a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
