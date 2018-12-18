---
title: Nastavení pro konfiguraci ladění jazyka Visual Basic projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vbProjectPropertiesDebug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- debugging [Visual Basic], debugger settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debug configurations, Visual Basic
ms.assetid: 72a8483a-af0b-4403-8b0d-ee9ad71ee435
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f3b221af6267966a9621d7926c3aeb5aa684cdad
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51735984"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] konfiguraci ladění v **stránky vlastností** okna, jak je popsáno v [konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** okna.  
  
> [!WARNING]
>  Toto téma se nevztahuje na aplikace pro Store. Zobrazit [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Ladění kartu  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Konfigurace**|Nastaví režim pro kompilaci aplikace. Zvolte mezi **aktivní (ladění)**, **ladění**, **vydání**, **všechny konfigurace**.|  
|**Spustit akci**|Tato skupina ovládacích prvků určuje akci, která bude vytvářena při výběru spuštění v nabídce ladění.<br /><br /> -   **Spustit projekt** je výchozí nastavení a spuštění projektu po spuštění pro ladění. Další informace najdete v tématu [NIB jak: nastavit projekty po spuštění](http://msdn.microsoft.com/en-us/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Spustit externí program** umožňuje spuštění a připojení k programu, který není součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Další informace najdete v tématu [připojení k běžící procesy](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   **Spustit prohlížeč v adrese URL** umožňuje ladění webové aplikace.|  
|**Argumenty příkazového řádku**|Určuje argumenty příkazového řádku pro program k ladění. Název příkazu je zadané ve spuštění programu externí název programu. Pokud se spouštěcí akce nastavená na Otevřít adresu URL, argumenty příkazového řádku jsou ignorovány.|  
|**Pracovní adresář**|Určuje pracovní adresář laděného programu. V [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], pracovní adresář je adresář od spuštění aplikace. Výchozí pracovní adresář je \bin\Debug nebo \bin\Release, v závislosti na aktuální konfiguraci.|  
|**Použití vzdáleného počítače**|Když je políčko zaškrtnuto, vzdálené ladění je povolen. Do textového pole, můžete zadat název vzdáleného počítače kde bude aplikace spuštěna, pro účely ladění nebo [název serveru Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Umístění souboru exe ve vzdáleném počítači, je určené vlastností výstupní cestu na kartě sestavení. Umístění musí být sdíleném adresáři na vzdáleném počítači.|  
|**Ladění nespravovaného kódu**|Umožňuje ladit volání nativního (nespravovaného) kódu Win32 z vaší spravované aplikace. To má stejný účinek jako výběr smíšený typ ladicího programu v [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu.|  
|**Ladění SQL serveru**|Umožňuje ladění objektů databáze systému SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Kompilace kartě: tlačítko Upřesnit možnosti kompilace  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Povolit optimalizace**|Tato možnost by měla nezaškrtnuté. Optimalizace způsobí, že kód, který je odlišný od zdrojového kódu v skutečně proveden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]a proto znesnadňuje ladění. Pokud je kód zoptimalizovaný, nejsou symboly načíst ve výchozím nastavení při ladění s jen můj kód.|  
|**Generovat ladicí informace**|Definované ve výchozím nastavení ladění a vydání verze, toto nastavení (odpovídá možnosti kompilátoru/Debug) vytvoří informace o ladění v okamžiku sestavení. Ladicí program používá tyto informace zobrazit názvy proměnných a další informace ve formě užitečné při ladění. Pokud kompilujete aplikace bez těchto informací, bude omezené funkce ladicího programu. Další informace najdete v tématu [/debug](http://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Definovat konstantu DEBUG**|Definování tento symbol umožňuje podmíněné kompilace výstup funkcí z [Debug – třída](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Tento symbol definovaný, ladění metody třídy generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez tento symbol nejsou zkompilovány metody třídy ladění a nebude vygenerován žádný výstup. Tento symbol by měl definované v ladicí verzi a není definovaný ve vydané verzi. Definování tento symbol v prodejní verzi vytvoří nepotřebný kód, který může zpomalit vaši aplikaci.|  
|**Definovat konstantu TRACE**|Definování tento symbol umožňuje podmíněné kompilace výstup funkcí z [Trasovací třída](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Tento symbol definovaný, metody třídy trasování generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez tento symbol nejsou zkompilovány metody třídy trasování a nebude vygenerován žádný výstup trasování. Tento symbol je definované ve výchozím nastavení pro ladění a vydání verze.|  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)



