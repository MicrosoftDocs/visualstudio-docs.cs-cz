---
title: 'Chyba: Ladění není&#39;t možné, protože v systému je povolen ladicí program jádra | Dokumentace Microsoftu'
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
- vs.debug.error.kernel_dbg_enabled
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- kernel debugger
ms.assetid: 630a7abd-3303-4aaa-888a-6de3de14bc01
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: eea2e7d8277bc67df75be3d05d907a8bd13c29c5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51725291"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Chyba: Ladění není&#39;t možné, protože v systému je povolen ladicí program jádra
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění spravovaného kódu, může se zobrazit následující chybová zpráva:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Tato zpráva se zobrazí při pokusu o ladění spravovaného kódu:  
  
-   na [!INCLUDE[win7](../includes/win7-md.md)] nebo [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)]systém, který se spustil v režimu ladění.  
  
-   aplikace používá CLR verze CLR 2.0, 3.0 nebo 3.5.  
  
## <a name="solution"></a>Řešení  
  
#### <a name="to-fix-this-problem"></a>Chcete-li vyřešit tento problém  
  
-   Upgrade aplikace pomocí modulu CLR verze 4.0 nebo 4.5  
  
     —nebo—  
  
-   Zakázat ladění jádra a ladit v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —nebo—  
  
-   Ladění pomocí ladicího programu jádra místo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
     —nebo—  
  
-   V ladicím programu jádra zakažte výjimky v uživatelském režimu.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Chcete-li zakázat ladění jádra v aktuální relaci.  
  
-   V příkazovém řádku zadejte příkaz:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Chcete-li zakázat ladění jádra na všechny relace (Windows Vista a Windows 7)  
  
1.  V příkazovém řádku zadejte příkaz:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2.  Restartujte počítač.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Chcete-li zakázat ladění jádra na všechny relace (ostatní Windows operační systémy)  
  
1.  Vyhledejte soubor boot.ini na systémovou jednotku (obvykle C:\\). Soubor boot.ini může být skrytý, jen pro čtení. Takže je třeba použít následující příkaz a prohlédněte si ho:  
  
    ```  
    dir /ASH  
    ```  
  
2.  Otevřete soubor boot.ini pomocí poznámkového bloku a odeberte následující možnosti:  
  
    ```  
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



