---
title: 'Postup: Použití protokolu aktivit | Dokumenty společnosti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 64986be303370cf8c9048612ff3d44e82e96805a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710582"
---
# <a name="how-to-use-the-activity-log"></a>Postup: Použití protokolu aktivit
VSPackages můžete psát zprávy do protokolu aktivit. Tato funkce je užitečná zejména pro ladění balíčků VSPackages v maloobchodních prostředích.

> [!TIP]
> Protokol aktivit je vždy zapnutý. Visual Studio udržuje postupné vyrovnávací paměti z posledních 100 položek, jakož i prvních 10 položek, které mají obecné informace o konfiguraci.

## <a name="to-write-an-entry-to-the-activity-log"></a>Zápis položky do protokolu aktivit

1. Vložte tento <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> kód do metody nebo do jakékoli jiné metody kromě konstruktoru VSPackage:

    ```csharp
    IVsActivityLog log = GetService(typeof(SVsActivityLog)) as IVsActivityLog;
    if (log == null) return;

    int hr = log.LogEntry((UInt32)__ACTIVITYLOG_ENTRYTYPE.ALE_INFORMATION,
        this.ToString(),
        string.Format(CultureInfo.CurrentCulture,
        "Called for: {0}", this.ToString()));
    ```

     Tento kód <xref:Microsoft.VisualStudio.Shell.Interop.SVsActivityLog> získá službu a <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> přetypová do rozhraní. <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog.LogEntry%2A>zapíše informační záznam do protokolu aktivit pomocí aktuálního kulturního kontextu.

2. Při načtení VSPackage (obvykle při vyvolání příkazu nebo otevření okna), text je zapsán do protokolu aktivit.

## <a name="to-examine-the-activity-log"></a>Chcete-li zkontrolovat protokol aktivit

1. Spusťte Visual Studio s přepínačem příkazového řádku [/Log](../ide/reference/log-devenv-exe.md) pro zápis souboru ActivityLog.xml na disk během relace.

2. Po zavření sady Visual Studio vyhledejte protokol aktivit v podsložce pro data sady Visual Studio:

   <em> *%AppData%</em>\Microsoft\VisualStudio\\\<verze>\ActivityLog.xml*.

3. Otevřete protokol aktivit s libovolným textovým editorem. Zde je typický záznam:

   ```
   Called for: Company.MyApp.MyAppPackage ...
   ```

## <a name="robust-programming"></a>Robustní programování

Vzhledem k tomu, že protokol aktivit je služba, protokol aktivit není k dispozici v konstruktoru VSPackage.

Protokol aktivit byste měli získat těsně před zápisem do něj. Neukládejte do mezipaměti ani neukládejte protokol aktivit pro budoucí použití.

## <a name="see-also"></a>Viz také

- [/Log (devenv.exe)](../ide/reference/log-devenv-exe.md)
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>
- <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>
- [Řešení potíží s rozšířením VSPackages](../extensibility/troubleshooting-vspackages.md)
- [Balíčky VSPackage](../extensibility/internals/vspackages.md)
