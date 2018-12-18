---
title: 'Chyba: Ověřování protokolem Kerberos se nezdařilo | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.callback_kerberos_auth_failed
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 0cf34885ee715a5685e4c2ced8b5a116e5c33e8d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49857656"
---
# <a name="error-kerberos-authentication-failed"></a>Chyba: Ověření protokolem Kerberos se nezdařilo.
Při pokusu provést vzdálené ladění, může se zobrazit následující chybová zpráva:  
  
```cmd
Error: The Visual Studio Remote Debugger on the target computer cannot connect back to this computer. Kerberos authentication failed.  
```  
  
 K této chybě dochází, když Visual Studio Remote Debugging Monitor běží pod účtem místního systému nebo síťové služby. V rámci jednoho z těchto účtů musí vzdálený ladicí program navázat připojení ověřování protokol Kerberos ke komunikaci zpět na hostitelském počítači ladicího programu sady Visual Studio.  
  
 Ověřování pomocí protokolu Kerberos není k dispozici za těchto podmínek:  
  
- Cílový počítač nebo hostitelský počítač ladicí program je v pracovní skupině místo domény  
  
   \- nebo –  
  
- Na řadiči domény se zakázalo protokolu Kerberos.  
  
  Pokud ověřování protokolu Kerberos není k dispozici, změňte účet, který se používá ke spuštění Visual Studio Remote Debugging Monitor. Tento postup, naleznete v tématu [Chyba: služba The Visual Studio Remote Debugger na cílovém počítači se nemůže připojit zpět k tomuto počítači](../debugger/error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md).  
  
  Pokud oba počítače jsou připojené ke stejné doméně a zachovat si tuto zprávu, ověřte, že DNS v cílovém počítači správně překládá název hostitelského počítače ladicího programu. Viz následující postup.  
  
### <a name="to-verify-that-dns-on-the-target-computer-is-correctly-resolving-the-debugger-host-computer-name"></a>Chcete-li ověřit, že DNS v cílovém počítači správně překládá název hostitelského počítače ladicího programu  
  
1.  V cílovém počítači, otevřete **Start** nabídky, přejděte k **Příslušenství** a potom klikněte na tlačítko **příkazového řádku**.  
  
2.  V **příkazového řádku** okno, zadejte:  
  
    ```cmd
    ping <debugger_host_computer_name>  
    ```  
  
3.  První řádek `ping` odpověď ukazuje úplný název počítače a IP adresu vrácenou funkcí DNS pro zadaný počítač.  
  
4.  Otevřete na hostitelském počítači ladicího programu **příkazového řádku** okna a spusťte `ipconfig`.  
  
5.  Porovnejte hodnoty IP adres.  
  
## <a name="see-also"></a>Viz také  
 [Vzdálené ladění chyby a řešení potíží](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Vzdálené ladění](../debugger/remote-debugging.md)
