---
title: Nastavení projektu VB ladění config | Dokumentace Microsoftu
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d70ec195418b46a022ca73d6ac3656de8e652f06
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/07/2018
ms.locfileid: "53059688"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka Visual Basic
Můžete změnit nastavení projektu [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] konfiguraci ladění v **stránky vlastností** okna, jak je popsáno v [konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** okna.  
  
> [!WARNING]
>  Toto téma se nevztahuje na aplikacích pro UPW. Zobrazit [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Ladění kartu  
  
| Nastavení | Popis |
|------------------------------| - |
| **Konfigurace** | Nastaví režim pro kompilaci aplikace. Zvolte mezi **aktivní (ladění)**, **ladění**, **vydání**, **všechny konfigurace**. |
| **Spustit akci** | Tato skupina ovládacích prvků určuje akci, která bude vytvářena při výběru spuštění v nabídce ladění.<br /><br /> -   **Spustit projekt** je výchozí nastavení a spuštění projektu po spuštění pro ladění. <br />-   **Spustit externí program** umožňuje spuštění a připojení k programu, který není součástí [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] projektu. Další informace najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Spustit prohlížeč v adrese URL** umožňuje ladění webové aplikace. |
| **Argumenty příkazového řádku** | Určuje argumenty příkazového řádku pro program k ladění. Název příkazu je zadané ve spuštění programu externí název programu. Pokud se spouštěcí akce nastavená na Otevřít adresu URL, argumenty příkazového řádku jsou ignorovány. |
| **Pracovní adresář** | Určuje pracovní adresář laděného programu. V [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], pracovní adresář je adresář od spuštění aplikace. Výchozí pracovní adresář je \bin\Debug nebo \bin\Release, v závislosti na aktuální konfiguraci. |
| **Použití vzdáleného počítače** | Když je políčko zaškrtnuto, vzdálené ladění je povolen. Do textového pole, můžete zadat název vzdáleného počítače kde bude aplikace spuštěna, pro účely ladění nebo [název serveru Msvsmon](../debugger/remote-debugging.md). Umístění souboru exe ve vzdáleném počítači, je určené vlastností výstupní cestu na kartě sestavení. Umístění musí být sdíleném adresáři na vzdáleném počítači. |
| **Ladění nespravovaného kódu** | Umožňuje ladit volání nativního (nespravovaného) kódu Win32 z vaší spravované aplikace. To má stejný účinek jako výběr smíšený typ ladicího programu v [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] projektu. |
| **Ladění SQL serveru** | Umožňuje ladění objektů databáze systému SQL Server. |
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Kompilace kartě: tlačítko Upřesnit možnosti kompilace  
  
| Nastavení | Popis |
|---------------------------| - |
| **Povolit optimalizace** | Tato možnost by měla nezaškrtnuté. Optimalizace způsobí, že kód, který je odlišný od zdrojového kódu v skutečně proveden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]a proto znesnadňuje ladění. Pokud je kód zoptimalizovaný, nejsou symboly načíst ve výchozím nastavení při ladění s jen můj kód. |
| **Generovat ladicí informace** | Definované ve výchozím nastavení ladění a vydání verze, toto nastavení (odpovídá možnosti kompilátoru/Debug) vytvoří informace o ladění v okamžiku sestavení. Ladicí program používá tyto informace zobrazit názvy proměnných a další informace ve formě užitečné při ladění. Pokud kompilujete aplikace bez těchto informací, bude omezené funkce ladicího programu. Další informace najdete v tématu [/debug](/dotnet/visual-basic/reference/command-line-compiler/debug). |
| **Definovat konstantu DEBUG** | Definování tento symbol umožňuje podmíněné kompilace výstup funkcí z [Debug – třída](/dotnet/api/system.diagnostics.debug). Tento symbol definovaný, ladění metody třídy generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez tento symbol nejsou zkompilovány metody třídy ladění a nebude vygenerován žádný výstup. Tento symbol by měl definované v ladicí verzi a není definovaný ve vydané verzi. Definování tento symbol v prodejní verzi vytvoří nepotřebný kód, který může zpomalit vaši aplikaci. |
| **Definovat konstantu TRACE** | Definování tento symbol umožňuje podmíněné kompilace výstup funkcí z [Trasovací třída](/dotnet/api/system.diagnostics.trace). Tento symbol definovaný, metody třídy trasování generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez tento symbol nejsou zkompilovány metody třídy trasování a nebude vygenerován žádný výstup trasování. Tento symbol je definované ve výchozím nastavení pro ladění a vydání verze. |
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)