---
title: 'Chyba: ladění&#39;není možné, protože v systému je povolen ladicí program jádra | Microsoft Docs'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a966869ff1d200a51c6019a6ae937bea7c447bd
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737748"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Chyba: ladění&#39;není možné, protože v systému je povolen ladicí program jádra.
Při ladění spravovaného kódu se může zobrazit následující chybová zpráva:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Tato zpráva se zobrazí při pokusu o ladění spravovaného kódu:

- na [!INCLUDE[win7](../debugger/includes/win7_md.md)] nebo [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)]system, které byly spuštěny v režimu ladění.

- aplikace používá CLR verze CLR 2,0, 3,0 nebo 3,5.

## <a name="solution"></a>Řešení

#### <a name="to-fix-this-problem"></a>Chcete-li tento problém vyřešit

- Upgradujte aplikaci tak, aby používala CLR verze 4,0 nebo 4,5.

   —nebo—

- Zakáže ladění a ladění jádra v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   —nebo—

- Ladění pomocí ladicího programu jádra místo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   —nebo—

- V ladicím programu jádra zakažte výjimky v uživatelském režimu.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Zakázání ladění jádra v aktuální relaci

- V příkazovém řádku zadejte příkaz:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Zakázání ladění jádra pro všechny relace (Windows Vista a Windows 7)

1. V příkazovém řádku zadejte příkaz:

    ```cmd
    bcdedit /debug off
    ```

2. Restartujte počítač.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Zakázání ladění jádra pro všechny relace (ostatní operační systémy Windows)

1. Vyhledejte soubor Boot. ini na systémové jednotce (obvykle C: \\). Soubor Boot. ini může být skrytý a jen pro čtení. Proto je nutné použít následující příkaz k zobrazení:

    ```cmd
    dir /ASH
    ```

2. Otevřete soubor Boot. ini pomocí poznámkového bloku a odeberte následující možnosti:

    ```cmd
    /debug
    /debugport
    /baudrate
    ```

3. Restartujte počítač.

#### <a name="to-debug-with-the-kernel-debugger"></a>Ladění pomocí ladicího programu jádra

1. Pokud je ladicí program jádra zapojen, zobrazí se zpráva s dotazem, zda chcete pokračovat v ladění. Pokračujte kliknutím na tlačítko.

2. Může se zobrazit `User break exception(Int 3).` Pokud k tomu dojde, zadáním následujícího příkazu ladicího programu jádra pokračujte v ladění:

     `gn`

## <a name="see-also"></a>Viz také:
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
