---
title: 'Postupy: používání protokolu aktivit | Microsoft Docs'
description: Sady VSPackage můžou zapisovat zprávy do protokolu aktivit. Naučte se používat protokol aktivit pro ladění VSPackage v maloobchodních prostředích.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f02a8dd1497680239db9363a2e0682082f0c68d8
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057335"
---
# <a name="how-to-use-the-activity-log"></a>Postupy: použití protokolu aktivit
Sady VSPackage můžou zapisovat zprávy do protokolu aktivit. Tato funkce je užitečná hlavně při ladění VSPackage v maloobchodních prostředích.

> [!TIP]
> Protokol aktivit je vždycky zapnutý. Visual Studio uchovává vyrovnávací paměť posledních 100 záznamů a také prvních 10 položek, které mají obecné informace o konfiguraci.

## <a name="to-write-an-entry-to-the-activity-log"></a>Zápis položky do protokolu aktivit

1. Vložte tento kód do <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metody nebo jakékoliv jiné metody s výjimkou konstruktoru VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Tento kód získá <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> službu a přetypování ji na <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A> Zapíše informační záznam do protokolu aktivit pomocí aktuálního kulturního kontextu.

2. Po načtení balíčku VSPackage (obvykle když je vyvolán příkaz nebo je otevřeno okno) se text zapíše do protokolu aktivit.

## <a name="to-examine-the-activity-log"></a>Kontrola protokolu aktivit

1. Spusťte Visual Studio s přepínačem příkazového řádku [/log](../ide/reference/log-devenv-exe.md) a zapište ActivityLog.xml na disk během vaší relace.

2. Po zavření sady Visual Studio vyhledejte protokol aktivit v podsložce pro data sady Visual Studio:

   <em> *% Data%</em>\Microsoft\VisualStudio \\ \<version>\ActivityLog.xml*.

3. Otevřete protokol aktivit v libovolném textovém editoru. Tady je typická položka:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Robustní programování

Vzhledem k tomu, že protokol aktivit je služba, protokol aktivit není v konstruktoru VSPackage k dispozici.

Protokol aktivit byste měli získat těsně před zapsáním do něj. Neukládejte protokol aktivit do mezipaměti ani neukládejte ho pro budoucí použití.

## <a name="see-also"></a>Viz také

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Řešení potíží s rozšířením VSPackages](../extensibility/troubleshooting-vspackages.md)
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
