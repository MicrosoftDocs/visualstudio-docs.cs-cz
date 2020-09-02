---
title: Nastavení projektu pro konfiguraci Visual Basicho ladění | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: 27acc89790e0759d3b284e3d9a4c6798c3d9a16f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687575"
---
# <a name="project-settings-for-a-visual-basic-debug-configuration"></a>Nastavení projektu pro konfiguraci ladění jazyka Visual Basic
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu pro [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] konfiguraci ladění v okně **stránky vlastností** , jak je popsáno v tématu [Konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v okně **stránky vlastností** .  
  
> [!WARNING]
> Toto téma se nevztahuje na aplikace pro Store. Viz [Spustit ladicí relaci (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
### <a name="debug-tab"></a>Karta ladění  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Konfigurace**|Nastaví režim pro kompilaci aplikace. Výběr mezi **aktivními (ladění)**, **laděním**, **vydáním**a **všemi konfiguracemi**.|  
|**Spustit akci**|Tato skupina ovládacích prvků Určuje akci, ke které dojde při zvolení možnosti spustit v nabídce ladění.<br /><br /> -   **Spustit projekt** je výchozí a spustí spouštěný projekt pro ladění. Další informace najdete v tématu [NIB postupy: nastavení projektů po spuštění](https://msdn.microsoft.com/31465836-0911-48db-a5d9-e456b635e970).<br />-   **Spustit externí program** umožňuje spustit program a připojit se k programu, který není součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Další informace najdete v tématu [připojení ke spuštěným procesům](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).<br />-   Možnost **spustit prohlížeč v adrese URL** vám umožní ladit webovou aplikaci.|  
|**Argumenty příkazového řádku**|Určuje argumenty příkazového řádku pro program, který se má ladit. Název příkazu je název programu zadaný v části spustit externí program. Pokud je počáteční akce nastavená na počáteční adresu URL, argumenty příkazového řádku se ignorují.|  
|**Pracovní adresář**|Určuje pracovní adresář programu, který se má ladit. V nástroji [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] je pracovním adresářem adresář, ze kterého se aplikace spouští. Výchozí pracovní adresář je \bin\Debug nebo \bin\Release, v závislosti na aktuální konfiguraci.|  
|**Použít vzdálený počítač**|Když je políčko zaškrtnuté, vzdálené ladění je povolené. Do textového pole můžete zadat název vzdáleného počítače, kde se aplikace spustí pro účely ladění nebo pro [název serveru msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Umístění souboru EXE ve vzdáleném počítači je určeno vlastností výstupní cesta na kartě sestavení. Umístění musí být sdílená složka na vzdáleném počítači.|  
|**Ladění nespravovaného kódu**|Umožňuje ladit volání nativního (nespravovaného) kódu Win32 ze spravované aplikace. To má stejný účinek jako výběr smíšené pro typ ladicího programu v [!INCLUDE[vcprvc](../includes/vcprvc-md.md)] projektu.|  
|**Ladění SQL Server**|Umožňuje ladění databázových objektů SQL Server.|  
  
### <a name="compile-tab-press-advanced-compile-options-button"></a>Karta kompilovat: tlačítko pro rozšířené možnosti kompilace  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Povolit optimalizace**|Tato možnost by měla být nezaškrtnutá. Optimalizace způsobí, že kód, který je skutečně proveden, se liší od zdrojového kódu zobrazeného v [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , a proto je obtížné ladění. Pokud je kód optimalizován, symboly nejsou ve výchozím nastavení načítány při ladění pomocí Pouze můj kód.|  
|**Generovat informace o ladění**|Definováno ve výchozím nastavení v ladicí verzi i ve verzích verze, toto nastavení (ekvivalentní možnosti kompilátoru/Debug) vytvoří informace o ladění v době sestavení. Ladicí program používá tyto informace k zobrazení názvů proměnných a dalších informací ve užitečné formě při ladění. Pokud program zkompilujete bez těchto informací, funkce ladicího programu budou omezené. Další informace najdete v tématu [/Debug](https://msdn.microsoft.com/library/c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2).|  
|**Definovat konstantu DEBUG**|Definování tohoto symbolu umožňuje podmíněné kompilování výstupních funkcí z [třídy ladění](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx). Při definování tohoto symbolu metody třídy ladění generují výstup do [okna výstup](../ide/reference/output-window.md). Bez tohoto symbolu nejsou kompilovány metody třídy ladění a není generován žádný výstup. Tento symbol by měl být definován v ladicí verzi a není definován v vydané verzi. Definováním tohoto symbolu v vydané verzi se vytvoří zbytečný kód, který zpomaluje váš program.|  
|**Definovat konstantu TRACE**|Definování tohoto symbolu umožňuje podmíněné kompilování výstupních funkcí z [třídy Trace](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). S tímto symbolem definovaným metody třídy Trace generují výstup do [okna výstup](../ide/reference/output-window.md). Bez tohoto symbolu nejsou kompilovány metody třídy Trace a nevygenerovaly se žádné výstupy trasování. Tento symbol je ve výchozím nastavení definován pro ladicí i prodejní verzi.|  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
