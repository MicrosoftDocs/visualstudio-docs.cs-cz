---
title: 'Postupy: používání protokolu aktivit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, debugging
- VSPackages, troubleshooting
ms.assetid: bb3d3322-0e5e-4dd5-b93a-24d5fbcd2ffd
caps.latest.revision: 30
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d450e02d23159f186fd85bf1b687a2fb2c18e82a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64824257"
---
# <a name="how-to-use-the-activity-log"></a>Postupy: Použití protokolu aktivit
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sady VSPackage můžou zapisovat zprávy do protokolu aktivit. Tato funkce je užitečná hlavně při ladění VSPackage v maloobchodních prostředích.  
  
> [!TIP]
> Protokol aktivit je vždycky zapnutý. Visual Studio uchovává vyrovnávací paměť posledních 100 záznamů a také prvních deset položek, které mají obecné informace o konfiguraci.  
  
### <a name="to-write-an-entry-to-the-activity-log"></a>Zápis položky do protokolu aktivit  
  
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
  
### <a name="to-examine-the-activity-log"></a>Kontrola protokolu aktivit  
  
1. Vyhledejte protokol aktivit v podsložce pro data aplikace Visual Studio: *% data%* \Microsoft\VisualStudio\14.0\ActivityLog.XML..  
  
2. Otevřete protokol aktivit v libovolném textovém editoru. Tady je typická položka:  
  
    ```  
    Called for: Company.MyApp.MyAppPackage ...  
    ```  
  
## <a name="robust-programming"></a>Robustní programování  
 Vzhledem k tomu, že protokol aktivit je služba, protokol aktivit není v konstruktoru VSPackage k dispozici.  
  
 Protokol aktivit byste měli získat těsně před zapsáním do něj. Neukládejte protokol aktivit do mezipaměti ani neukládejte ho pro budoucí použití.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__ACTIVITYLOG_ENTRYTYPE>   
 [Řešení potíží s VSPackage](../extensibility/troubleshooting-vspackages.md)   
 [Balíčky VSPackage](../extensibility/internals/vspackages.md)
