---
title: 'Chyba: ladění není&#39;možné, protože v systému je povolen ladicí program jádra | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 4f2f963ad2fbdad9453f6c6b853bc720034f613c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197067"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Chyba: ladění není&#39;možné, protože v systému je povolen ladicí program jádra.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Při ladění spravovaného kódu se může zobrazit následující chybová zpráva:  
  
```  
Debugging isn't possible because a kernel debugger is enabled on the system  
```  
  
 Tato zpráva se zobrazí při pokusu o ladění spravovaného kódu:  
  
- v [!INCLUDE[win7](../includes/win7-md.md)] systému nebo [!INCLUDE[wiprlhext](../includes/wiprlhext-md.md)] , který byl spuštěn v režimu ladění.  
  
- aplikace používá CLR verze CLR 2,0, 3,0 nebo 3,5.  
  
## <a name="solution"></a>Řešení  
  
#### <a name="to-fix-this-problem"></a>Chcete-li tento problém vyřešit  
  
- Upgradujte aplikaci tak, aby používala CLR verze 4,0 nebo 4,5.  
  
     —nebo—  
  
- Zakáže ladění a ladění jádra v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     —nebo—  
  
- Ladění pomocí ladicího programu jádra místo [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     —nebo—  
  
- V ladicím programu jádra zakažte výjimky v uživatelském režimu.  
  
#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Zakázání ladění jádra v aktuální relaci  
  
- Na příkazovém řádku zadejte:  
  
    ```  
    Kdbgctrl.exe -d  
    ```  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Zakázání ladění jádra pro všechny relace (Windows Vista a Windows 7)  
  
1. Na příkazovém řádku zadejte:  
  
    ```  
    bcdedit /debug off   
    ```  
  
2. Restartujte počítač.  
  
#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Zakázání ladění jádra pro všechny relace (ostatní operační systémy Windows)  
  
1. Na systémové jednotce Najděte boot.ini (obvykle C: \\ ). Soubor boot.ini může být skrytý a jen pro čtení. Proto je nutné použít následující příkaz k zobrazení:  
  
    ```  
    dir /ASH  
    ```  
  
2. Pomocí poznámkového bloku otevřete boot.ini a odeberte následující možnosti:  
  
    ```  
    /debug  
    /debugport  
    /baudrate  
    ```  
  
3. Restartujte počítač.  
  
#### <a name="to-debug-with-the-kernel-debugger"></a>Ladění pomocí ladicího programu jádra  
  
1. Pokud je ladicí program jádra zapojen, zobrazí se zpráva s dotazem, zda chcete pokračovat v ladění. Pokračujte kliknutím na tlačítko.  
  
2. `User break exception(Int 3).`Pokud k tomu dojde, může se stát, že pro pokračování v ladění zadáte následující příkaz ladicího programu jádra:  
  
     `gn`  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení ladicího programu](../debugger/debugger-security.md)   
 [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
