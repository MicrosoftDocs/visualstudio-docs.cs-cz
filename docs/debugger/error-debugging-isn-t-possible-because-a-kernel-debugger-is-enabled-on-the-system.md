---
title: 'Chyba: Ladění není&#39;t možné, protože v systému je povolen ladicí program jádra | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- kernel debugger
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4aa8aa820330264357341948a468d58d98c86056
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49853973"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Chyba: Ladění není&#39;t možné, protože v systému je povolen ladicí program jádra
Při ladění spravovaného kódu, může se zobrazit následující chybová zpráva:  
  
```cmd
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Tato zpráva se zobrazí při pokusu o ladění spravovaného kódu:  
  
- na [!INCLUDE[win7](../debugger/includes/win7_md.md)] nebo [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]systém, který se spustil v režimu ladění.  
  
- aplikace používá CLR verze CLR 2.0, 3.0 nebo 3.5.  
  
## <a name="solution"></a>Řešení  
  
#### <a name="to-fix-this-problem"></a>Chcete-li vyřešit tento problém  
  
- Upgrade aplikace pomocí modulu CLR verze 4.0 nebo 4.5  
  
   —nebo—  
  
- Zakázat ladění jádra a ladit v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   —nebo—  
  
- Ladění pomocí ladicího programu jádra místo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
   —nebo—  
  
- V ladicím programu jádra zakažte výjimky v uživatelském režimu.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Chcete-li zakázat ladění jádra v aktuální relaci.  
  
-   V příkazovém řádku zadejte příkaz:  
  
    ```cmd
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Chcete-li zakázat ladění jádra na všechny relace (Windows Vista a Windows 7)  
  
1.  V příkazovém řádku zadejte příkaz:  
  
    ```cmd
    bcdedit /debug off   
    ```  
  
2.  Restartujte počítač.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Chcete-li zakázat ladění jádra na všechny relace (ostatní Windows operační systémy)  
  
1.  Vyhledejte soubor boot.ini na systémovou jednotku (obvykle C:\\). Soubor boot.ini může být skrytý, jen pro čtení. Takže je třeba použít následující příkaz a prohlédněte si ho:  
  
    ```cmd
    dir /ASH  
    ```  
  
2.  Otevřete soubor boot.ini pomocí poznámkového bloku a odeberte následující možnosti:  
  
    ```cmd
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3.  Restartujte počítač.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Chcete-li ladit pomocí ladicího programu jádra  
  
1.  Pokud ladicí program jádra je připojili, zobrazí se zpráva s dotazem, jestli chcete pokračovat v ladění. Klikněte na tlačítko Pokračovat.  
  
2.  Může se zobrazit `User break exception(Int 3).` Pokud k tomu dojde, zadejte následující příkaz ladicí program jádra a pokračujte v ladění:  
  
     `gn`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
