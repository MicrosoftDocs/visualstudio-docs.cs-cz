---
title: Nastavení pro projektu C# ladění config | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/21/2018
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 6de7bfd547516b227063c0d3143b508bcbd9ddfd
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059269"
---
# <a name="project-settings-for--c-debug-configurations"></a>Nastavení projektu pro konfiguraci ladění jazyka C#

Můžete změnit C# nastavení ladění v projektu [karty ladění](#debug-tab) a [karta sestavení](#build-tab) stránky vlastností projektu. 

K otevření stránek vlastností, vyberte projekt v **Průzkumníka řešení** a pak vyberte **vlastnosti** ikonu, nebo klikněte pravým tlačítkem na projekt a vyberte **vlastnosti**.

Další informace najdete v tématu [pro ladění a vydání konfigurace](how-to-set-debug-and-release-configurations.md). 

>[!IMPORTANT]
>Tato nastavení neplatí pro aplikace .NET Core, ASP.NET nebo UWP. Konfigurace nastavení ladění pro aplikace pro UPW, naleznete v tématu [spustíte relaci ladění pro aplikace pro UPW](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).  
  
## <a name="debug-tab"></a>Ladění kartu  
  
|Nastavení|Popis|
|-------------------------------------| - |
| **Konfigurace** | Nastaví režim pro aplikaci. Vyberte **aktivní (ladění)**, **ladění**, **vydání**, nebo **všechny konfigurace** z rozevíracího seznamu. |
| **Spustit akci** | Určuje akci, když vyberete **Start** v konfiguraci ladění.<br />- **Spustit projekt** je výchozí nastavení a spuštění projektu po spuštění pro ladění. Další informace najdete v tématu [výběr spouštěného projektu](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- **Spustit externí program** spustí a připojí se k aplikaci, která není součástí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Další informace najdete v tématu [připojení ke spuštěným procesům pomocí ladicího programu](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Spustit prohlížeč s adresou URL** umožňuje ladění webové aplikace. |
| **Možnosti spuštění** > **argumenty příkazového řádku** | Určuje argumenty příkazového řádku pro aplikaci, který se právě ladí. Název příkazu je název aplikace uvedený v **externí program Start**. |
| **Možnosti spuštění** > **pracovní adresář** | Určuje pracovní adresář aplikace, který se právě ladí. V C#, v pracovním adresáři *\bin\debug* ve výchozím nastavení.
| **Možnosti spuštění** > **použít vzdálený počítač**|Pro vzdálené ladění, vyberte tuto možnost a zadejte název cíl vzdáleného ladění nebo [název serveru Msvsmon](../debugger/remote-debugging.md). <br />Je určená umístění aplikace ve vzdáleném počítači, **výstupní cesta** vlastnost **sestavení** kartu. Umístění musí být sdíleném adresáři na vzdáleném počítači. 
| **Modul ladicího programu** > **povolit ladění nespravovaného kódu** | Ladí volání nativního (nespravovaného) kódu Win32 ze spravovaných aplikací. |
| **Modul ladicího programu** > **povolit ladění SQL serveru** | Ladí objekty databáze systému SQL Server. |
  
## <a name="build-tab"></a>Vytvořit kartu  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Obecné** > **symboly podmíněné kompilace**|Definujte konstanty ladění a trasování, pokud vybraná.<br /><br /> Tyto konstanty povolit podmíněné kompilace [Debug – třída](/dotnet/api/system.diagnostics.debug) a [Trasovací třída](/dotnet/api/system.diagnostics.trace). Pomocí těchto konstanty definované, ladění a trasování metody třídy generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez těchto konstanty nejsou zkompilovány metody třídy ladění a trasování a nebude vygenerován žádný výstup.<br /><br />LADĚNÍ je obvykle definované v ladicí verzi sestavení a nedefinované ve vydané verzi. TRASOVÁNÍ je definována v ladění i vydání verze.|  
|**Obecné** > **optimalizovat kód**|Pokud se zobrazí chyby pouze v optimalizovaném kódu, nechte toto nastavení nevybraných pro sestavení pro ladění. Optimalizovaný kód je těžší ladit, protože pokyny neodpovídají přímo pro příkazy ve zdrojovém kódu.|  
|**Výstup** > **výstupní cesta**|Obvykle nastavena na *bin\Debug* pro ladění.|
|**Pokročilé** tlačítko|Informace o pokročilé možnosti ladění, naleznete v tématu [dialogové okno nastavení rozšířené sestavení (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Přenosný formát pro symbol (*PDB*) souborů je poslední formát pro různé platformy, pro aplikace .NET Core. 
  
## <a name="see-also"></a>Viz také:  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)