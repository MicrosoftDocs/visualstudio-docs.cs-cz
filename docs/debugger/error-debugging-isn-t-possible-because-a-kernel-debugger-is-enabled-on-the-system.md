---
title: Ladění &apos; není možné, protože v systému je povolen ladicí program jádra | Microsoft Docs
description: Tato zpráva se zobrazí, když se pokusíte ladit spravovaný kód v systému Windows 7 nebo Windows Vista, který byl spuštěn v režimu ladění, a aplikace používá CLR verze CLR 2,0, 3,0 nebo 3,5.
ms.date: 11/04/2016
ms.topic: error-reference
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ced7fb79a11321678ae2963241807e5ddd4600ab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466456"
---
# <a name="error-debugging-isn39t-possible-because-a-kernel-debugger-is-enabled-on-the-system"></a>Chyba: ladění není&#39;možné, protože v systému je povolen ladicí program jádra.
Při ladění spravovaného kódu se může zobrazit následující chybová zpráva:

```cmd
Debugging isn't possible because a kernel debugger is enabled on the system
```

 Tato zpráva se zobrazí při pokusu o ladění spravovaného kódu:

- v [!INCLUDE[win7](../debugger/includes/win7_md.md)] systému nebo [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] , který byl spuštěn v režimu ladění.

- aplikace používá CLR verze CLR 2,0, 3,0 nebo 3,5.

## <a name="solution"></a>Řešení

#### <a name="to-fix-this-problem"></a>Chcete-li tento problém vyřešit

- Upgradujte aplikaci tak, aby používala CLR verze 4,0 nebo 4,5.

   —nebo—

- Zakáže ladění a ladění jádra v [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   —nebo—

- Ladění pomocí ladicího programu jádra místo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   —nebo—

- V ladicím programu jádra zakažte výjimky v uživatelském režimu.

#### <a name="to-disable-kernel-debugging-in-the-current-session"></a>Zakázání ladění jádra v aktuální relaci

- Na příkazovém řádku zadejte:

    ```cmd
    Kdbgctrl.exe -d
    ```

#### <a name="to-disable-kernel-debugging-for-all-sessions-windows-vista-and-windows-7"></a>Zakázání ladění jádra pro všechny relace (Windows Vista a Windows 7)

1. Na příkazovém řádku zadejte:

    ```cmd
    bcdedit /debug off
    ```

2. Restartujte počítač.

#### <a name="to-disable-kernel-debugging-for-all-sessions-other-windows-operating-systems"></a>Zakázání ladění jádra pro všechny relace (ostatní operační systémy Windows)

1. Na systémové jednotce Najděte boot.ini (obvykle C: \\ ). Soubor boot.ini může být skrytý a jen pro čtení. Proto je nutné použít následující příkaz k zobrazení:

    ```cmd
    dir /ASH
    ```

2. Pomocí poznámkového bloku otevřete boot.ini a odeberte následující možnosti:

    ```cmd
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
- [Zabezpečení ladicího programu](../debugger/debugger-security.md)
- [Ladění spravovaného kódu](../debugger/debugging-managed-code.md)
