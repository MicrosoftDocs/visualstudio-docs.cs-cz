---
title: Nastavení projektu pro konfiguraci ladění v jazyce C# | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
manager: jillfra
ms.openlocfilehash: f1ec1c18fe92409a72994e4544215da01325d209
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687521"
---
# <a name="project-settings-for--c-debug-configurations"></a>Nastavení projektu pro konfiguraci ladění jazyka C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Můžete změnit nastavení projektu pro konfiguraci ladění v jazyce C# v okně **stránky vlastností** , jak je popsáno v tématu [Konfigurace ladění a vydání](../debugger/how-to-set-debug-and-release-configurations.md). Následující tabulky ukazují, kde najít nastavení související s ladicím programem v okně **stránky vlastností** .  
  
> [!WARNING]
> Toto téma se nevztahuje na aplikace pro Windows Store. Viz [Spustit ladicí relaci (VB, C#, C++ a XAML)](../debugger/start-a-debugging-session-for-a-store-app-in-visual-studio-vb-csharp-cpp-and-xaml.md)  
  
## <a name="debug-tab"></a><a name="BKMK_Debug_tab"></a> Karta ladění  
  
|**Nastavení**|**Popis**|  
|-----------------|---------------------|  
|**Konfigurace**|Nastaví režim pro kompilaci aplikace. Výběr mezi **aktivními (ladění)**, **laděním**, **vydáním**a **všemi konfiguracemi**.|  
|**Spustit akci**|Tato skupina ovládacích prvků Určuje akci, ke které dojde při zvolení možnosti spustit v nabídce ladění.<br /><br /> -   **Spustit projekt** je výchozí a spustí spouštěný projekt pro ladění. Další informace najdete v tématu [Výběr spouštěného projektu](https://msdn.microsoft.com/222e3f32-a6fe-4941-bf37-6b2a921129fd).<br />-   **Spustit externí program** umožňuje spustit program a připojit se k programu, který není součástí [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] projektu. Další informace najdete v tématu [připojení ke spuštěnému programu](https://msdn.microsoft.com/636d0a52-4bfd-48d2-89ad-d7b9ca4dc4f4).<br />-   Možnost **spustit prohlížeč v adrese URL** vám umožní ladit webovou aplikaci.|  
|**Argumenty příkazového řádku**|Určuje argumenty příkazového řádku pro program, který se má ladit. Název příkazu je název programu zadaný v části spustit externí program. Pokud je počáteční akce nastavená na počáteční adresu URL, argumenty příkazového řádku nejde zadat.|  
|**Pracovní adresář**|Určuje pracovní adresář programu, který se má ladit. V nástroji [!INCLUDE[csprcs](../includes/csprcs-md.md)] je pracovní adresář v adresáři, ve kterém je aplikace spouštěna z \bin\debug ve výchozím nastavení.|  
|**Použít vzdálený počítač**|Název vzdáleného počítače, kde bude aplikace spuštěna pro účely ladění nebo [název serveru msvsmon](https://msdn.microsoft.com/library/55b60ce7-834b-4e83-a10e-fe4248260a4c). Umístění souboru EXE ve vzdáleném počítači je určeno vlastností výstupní cesta ve složce vlastnosti konfigurace, kategorie sestavení. Umístění musí být sdílená složka na vzdáleném počítači.|  
|**Povolit ladění nespravovaného kódu**|Umožňuje ladit volání nativního (nespravovaného) kódu Win32 ze spravované aplikace.|  
|**Povolit ladění SQL Server**|Umožňuje ladění databázových objektů SQL Server.|  
  
## <a name="build-tab"></a><a name="BKMK_Build_tab"></a> Karta sestavení  
  
|Nastavení|Popis|  
|-------------|-----------------|  
|**Symboly podmíněné kompilace:**|Konstanty ladění a trasování jsou zde definovány.<br /><br /> Tyto konstanty umožňují podmíněnou kompilaci [třídy ladění](https://msdn.microsoft.com/library/system.diagnostics.debug.aspx) a [třídy trasování](https://msdn.microsoft.com/library/system.diagnostics.trace.aspx). Pomocí těchto konstant třídy ladění a trasování generují výstup do [okna výstup](../ide/reference/output-window.md). Bez těchto konstant nejsou kompilovány metody třídy ladění a trasování a není vygenerován žádný výstup.<br /><br /> -Ladění je obvykle definováno v ladicí verzi programu a není definováno v vydané verzi.<br />-Trasování je obvykle definováno v ladicí i prodejní verzi.|  
|**Optimalizovat kód**|Pokud nenajdete chybu, která se zobrazí pouze v optimalizovaném kódu, měli byste toto nastavení ponechat v ladicí verzi vypnuté. Optimalizovaný kód je těžší ladit, protože pokyny neodpovídají přímo příkazům ve vašich zdrojových oknech.|  
|**Výstupní cesta:**|Obvykle nastaveno na bin\Debug pro ladění.|  
  
## <a name="see-also"></a>Viz také  
 [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)
