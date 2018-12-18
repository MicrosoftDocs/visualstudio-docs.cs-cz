---
title: Nastavení pro konfiguraci ladění jazyka C# projektu | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debug configurations, C#
- debugging [J#], debugger settings
- project settings [Visual Studio], debug configurations
- debug builds, project settings
- projects [Visual Studio], debug configurations
- project configurations, debug
- debugging [C#], debugger settings
- debug configurations, J#
ms.assetid: e30ca810-66e9-4d6e-9cf6-9f285cd0b100
caps.latest.revision: 25
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07da36adc1615217315d5ebb23f8ef62db59f5c7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721177"
---
# <a name="project-settings-for--c-debug-configurations"></a>Nastavení projektu pro konfiguraci ladění jazyka C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu pro konfiguraci ladění jazyka C# v **stránky vlastností** okna, jak je popsáno v [konfigurace ladění a verzí](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky popisují, kde najít nastavení související s ladicí program v **stránky vlastností** okna.  
  
> [!WARNING]
>  Toto téma se nevztahuje na aplikace Windows Store. Zobrazit [spustíte relaci ladění (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
##  <a name="BKMK_Debug_tab"></a> Ladění kartu  
  
|**Nastavení**|**Popis**|  
|-----------------|---------------------|  
|**Konfigurace**|Nastaví režim pro kompilaci aplikace. Zvolte mezi **aktivní (ladění)**, **ladění**, **vydání**, **všechny konfigurace**.|  
|**Spustit akci**|Tato skupina ovládacích prvků určuje akci, která bude vytvářena při výběru spuštění v nabídce ladění.<br /><br /> -   **Spustit projekt** je výchozí nastavení a spuštění projektu po spuštění pro ladění. Další informace najdete v tématu [výběr spouštěného projektu](http://msdn.microsoft.com/en-us/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Spustit externí program** umožňuje spuštění a připojení k programu, který není součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Další informace najdete v tématu [připojení ke spuštění programu](http://msdn.microsoft.com/en-us/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   **Spustit prohlížeč v adrese URL** umožňuje ladění webové aplikace.|  
|**Argumenty příkazového řádku**|Určuje argumenty příkazového řádku pro program k ladění. Název příkazu je zadané ve spuštění programu externí název programu. Pokud se spouštěcí akce nastavená na Otevřít adresu URL, nelze zadat argumenty příkazového řádku.|  
|**Pracovní adresář**|Určuje pracovní adresář laděného programu. V [!INCLUDE[csprcs](../includes/csprcs-md.md)], pracovní adresář je adresář spuštění aplikace z \bin\debug ve výchozím nastavení.|  
|**Použití vzdáleného počítače**|Název vzdáleného počítače kde bude aplikace spuštěna, pro účely ladění nebo [název serveru Msvsmon](http://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Umístění souboru exe ve vzdáleném počítači, je určené vlastností výstupní cestu ve složce vlastnosti konfigurace sestavení kategorie. Umístění musí být sdíleném adresáři na vzdáleném počítači.|  
|**Povolit ladění nespravovaného kódu**|Umožňuje ladit volání nativního (nespravovaného) kódu Win32 z vaší spravované aplikace.|  
|**Povolit ladění SQL serveru**|Umožňuje ladění objektů databáze systému SQL Server.|  
  
##  <a name="BKMK_Build_tab"></a> Vytvořit kartu  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Symboly podmíněné kompilace:**|Zde jsou definovány konstanty ladění a trasování.<br /><br /> Tyto konstanty povolit podmíněné kompilace [Debug – třída](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) a [Trasovací třída](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Pomocí těchto konstanty definované, ladění a trasování metody třídy generovat výstup do [okno výstup](../ide/reference/output-window.md). Bez těchto konstanty ladění a trasování metody třídy nejsou zkompilovány a nebude vygenerován žádný výstup.<br /><br /> -Debug je obvykle definované v ladicí verzi programu a nedefinované ve vydané verzi.<br />-Trasování je obvykle definováno v ladění i vydání verze.|  
|**Optimalizovat kód**|Pokud zjistíte chybu, která se zobrazí pouze v optimalizovaném kódu, nechte toto nastavení vypnuté v ladicí verzi. Optimalizovaný kód je těžší ladit, protože pokyny neodpovídají přímo pro příkazy ve zdrojových oknech.|  
|**Výstupní cesta:**|Nastavte obvykle bin\Debug pro ladění.|  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)



