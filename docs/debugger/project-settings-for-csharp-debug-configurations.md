---
title: Nastavení projektu pro konfiguraci ladění jazyka C# | Microsoft Docs
description: Zjistěte, jak změnit nastavení projektu pro konfiguraci ladění v jazyce C# v aplikaci Visual Studio pomocí karty ladění a karty sestavení stránky vlastností projektu.
ms.custom: SEO-VS-2020, seodec18
ms.date: 11/21/2018
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 262e46436f1391ae21df0ccdd3ca308eecb347da
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205564"
---
# <a name="project-settings-for--c-debug-configurations"></a>Nastavení projektu pro konfiguraci ladění jazyka C#

Nastavení ladění projektu C# můžete změnit na [kartě ladění](#debug-tab) a na [kartě sestavení](#build-tab) stránky vlastností projektu.

Chcete-li otevřít stránky vlastností, vyberte projekt v **Průzkumník řešení** a pak vyberte ikonu **vlastnosti** , nebo klikněte pravým tlačítkem myši na projekt a vyberte možnost **vlastnosti**.

Další informace najdete v tématu [Konfigurace ladění a vydání](how-to-set-debug-and-release-configurations.md).

>[!IMPORTANT]
>Tato nastavení se nevztahují na aplikace .NET Core, ASP.NET a UWP. Pokud chcete nakonfigurovat nastavení ladění pro aplikace pro UWP, přečtěte si téma [spuštění ladicí relace pro aplikaci pro UWP](start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md).

## <a name="debug-tab"></a>Karta ladění

|Nastavení|Popis|
|-------------------------------------| - |
| **Konfigurace** | Nastaví režim pro sestavování aplikace. V rozevíracím seznamu vyberte **aktivní (ladění)**, **ladění**, **vydání** nebo **všechny konfigurace** . |
| **Spustit akci** | Určuje akci, když v konfiguraci ladění vyberete **Spustit** .<br />- **Spustit projekt** je výchozí a spustí spouštěný projekt pro ladění. Další informace najdete v tématu [Výběr spouštěného projektu](/previous-versions/visualstudio/visual-studio-2010/0s590bew(v=vs.100)).<br />- Spustí se **spuštění externího programu** a připojí se k aplikaci, která není součástí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Další informace najdete v tématu [připojení ke spuštěným procesům pomocí ladicího programu](attach-to-running-processes-with-the-visual-studio-debugger.md).<br />- **Spustit prohlížeč s adresou URL** vám umožní ladit webovou aplikaci. |
| **Možnosti spuštění**  >  **Argumenty příkazového řádku** | Určuje argumenty příkazového řádku pro laděnou aplikaci. Název příkazu je název aplikace zadaný v části **spustit externí program**. |
| **Možnosti spuštění**  >  **Pracovní adresář** | Určuje pracovní adresář laděné aplikace. V jazyce C# je pracovní adresář ve výchozím nastavení *\bin\debug* .
| **Možnosti spuštění**  >  **Použít vzdálený počítač**|Pro vzdálené ladění vyberte tuto možnost a zadejte název cíle vzdáleného ladění nebo [název serveru msvsmon](../debugger/remote-debugging.md). <br />Umístění aplikace na vzdáleném počítači je určeno vlastností **výstupní cesta** na kartě **sestavení** . Umístění musí být sdílená složka na vzdáleném počítači.
| Modul ladicího **programu**  >  **Povolit ladění nespravovaného kódu** | Provede ladění volání nativního (nespravovaného) kódu Win32 ze spravované aplikace. |
| Modul ladicího **programu**  >  **Povolit ladění SQL Server** | Vyladí SQL Server databázových objektů. |

## <a name="build-tab"></a>Karta sestavení

|Nastavení|Popis|
|-------------|-----------------|
|**Obecné**  >  **Symboly podmíněné kompilace**|Definujte konstanty ladění a trasování, pokud je vybrána možnost.<br /><br /> Tyto konstanty umožňují podmíněnou kompilaci [třídy ladění](/dotnet/api/system.diagnostics.debug) a [třídy trasování](/dotnet/api/system.diagnostics.trace). Pomocí těchto konstant třídy ladění a trasování generují výstup do [okna výstup](../ide/reference/output-window.md). Bez těchto konstant nejsou kompilovány metody třídy ladění a trasování a není vygenerován žádný výstup.<br /><br />LADĚNÍ je obvykle definováno v ladicí verzi sestavení a není definováno v vydané verzi. TRASOVÁNÍ je definováno v ladicí verzi i ve verzi Release.|
|**Obecné**  >  **Optimalizovat kód**|Pokud se chyba neobjeví pouze v optimalizovaném kódu, nechte toto nastavení pro ladění sestavení nevybrané. Optimalizovaný kód je těžší ladit, protože pokyny neodpovídají přímo příkazům ve zdrojovém kódu.|
|**Výstup**  >  **Výstupní cesta**|Obvykle nastaveno na *bin\Debug* pro ladění.|
|**Rozšířené** tlačítko|Informace o pokročilých možnostech ladění naleznete v [dialogovém okně Upřesnit nastavení sestavení (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md). Přenosový formát souborů symbolů (*. pdb*) je nedávný formát pro různé platformy pro aplikace .NET Core.

## <a name="see-also"></a>Viz také
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)