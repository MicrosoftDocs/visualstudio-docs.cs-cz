---
title: Zadejte verzi .NET Framework pro ladění | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- .NET Framework, specifying version for debugging
- debugging [Visual Studio], specifying .NET Framework version
ms.assetid: 7a4893ba-4620-4774-893f-378d4ca28893
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1f6107d6396c6228be1d511e81003fbe7faf06c9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72732642"
---
# <a name="specify-an-older-net-framework-version-for-debugging-c-visual-basic-f"></a>Zadejte starší verzi .NET Framework pro ladění (C#, Visual Basic, F#).

Ladicí program sady Visual Studio podporuje ladění starších verzí Microsoft .NET Framework a aktuální verze. Pokud spustíte aplikaci ze sady Visual Studio, ladicí program může vždy identifikovat správnou verzi .NET Framework pro aplikaci, kterou ladíte. Pokud je však aplikace již spuštěna a spustíte ladění pomocí možnosti **připojit k**, ladicí program nemusí vždy identifikovat starší verzi .NET Framework. V takovém případě se zobrazí chybová zpráva s informacemi o tom,

``` cmd
The debugger has made an incorrect assumption about the .NET Framework version your application is going to use.
```

Ve výjimečných případech, kdy se zobrazí tato chyba, můžete nastavit klíč registru, který bude označovat ladicímu programu, které verze se má použít.

### <a name="to-specify-a-net-framework-version-for-debugging"></a>Určení verze .NET Framework pro ladění

1. Vyhledejte v adresáři Windows\Microsoft.NET\Framework verze .NET Framework nainstalované na vašem počítači. Čísla verzí vypadají přibližně takto:

    `V1.1.4322`

    Identifikujte správné číslo verze a poznamenejte si ho.

2. Spusťte **Editor registru** (Regedit).

3. V **Editoru registru**otevřete složku HKEY_LOCAL_MACHINE.

4. Přejít na: HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine \\ {449EC4CC-30D2-4032-9256-EE18EB41B62B}

    Pokud klíč neexistuje, klikněte pravým tlačítkem na HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\10.0\AD7Metrics\Engine a klikněte na **nový klíč**. Pojmenujte nový klíč `{449EC4CC-30D2-4032-9256-EE18EB41B62B}`.

5. Po přechodu na {449EC4CC-30D2-4032-9256-EE18EB41B62B} se podívejte do sloupce **název** a vyhledejte klíč CLRVersionForDebugging.

   1. Pokud klíč neexistuje, klikněte pravým tlačítkem na {449EC4CC-30D2-4032-9256-EE18EB41B62B} a pak klikněte na **Nová hodnota řetězce**. Pak klikněte pravým tlačítkem na novou řetězcovou hodnotu, klikněte na **Přejmenovat**a zadejte `CLRVersionForDebugging`.

6. Dvakrát klikněte na **CLRVersionForDebugging**.

7. Do pole **Upravit řetězec** zadejte .NET Framework číslo verze do pole **hodnota** . Příklad: V 1.1.4322

8. Klikněte na tlačítko **OK**.

9. Zavřete **Editor registru**.

     Pokud se vám při zahájení ladění stále zobrazí chybová zpráva, ověřte, že jste v registru zadali číslo verze správně. Ověřte také, že používáte verzi .NET Framework, kterou podporuje aplikace Visual Studio. Ladicí program je kompatibilní s aktuální verzí .NET Framework a předchozími verzemi, ale nemusí být dopředný kompatibilní s budoucími verzemi.

## <a name="see-also"></a>Viz také:
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)