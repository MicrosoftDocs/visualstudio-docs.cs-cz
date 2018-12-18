---
title: Obecné, prostředí, dialogové okno Možnosti | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 967036aa0aedef2f789a1352e213079270f70339
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2018
ms.locfileid: "49206879"
---
# <a name="general-environment-options-dialog-box"></a>Obecné, prostředí, dialogové okno Možnosti
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Pomocí této stránky můžete změnit barevné motivy, nastavení panelu stavu a přidružení přípony souboru, mezi další možnosti pro integrované vývojové prostředí (IDE). Můžete přistupovat **možnosti** dialogové okno tak, že otevřete **nástroje** nabídku, zvolíte **možnosti**, otevřete **prostředí** složky a pak Výběr **Obecné** stránky. Pokud se tato stránka se nezobrazí v seznamu, vyberte **zobrazit všechna nastavení** zaškrtávací políčko **možnosti** dialogové okno.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, otevřete **nástroje** nabídky a klikněte na tlačítko **nastavení importu a exportu**. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="visual-experience"></a>Vzhled  
 **Barevný motiv**  
 Zvolte **modré**, **světla** nebo **tmavě** barvy motivu rozhraní IDE.  
  
 Můžete nainstalovat další předdefinované motivy a vytvářet vlastní motivy stažením a instalací **Visual Studio 2015 Editor motivů sady** z [Galerie sady Visual Studio](https://visualstudiogallery.msdn.microsoft.com/site/search?f%5B0%5D.Type=RootCategory&f%5B0%5D.Value=tools). Po instalaci tohoto nástroje se zobrazí v seznamu Barva motivu další barevné motivy.  
  
 Použít název velká a malá písmena v řádku nabídek  
 Nabídky jsou v **malých a velkých písmen názvu** ve výchozím nastavení v sadě Visual Studio 2015. Zrušte zaškrtnutí políčka tuto možnost nastavíte **všechna velká mají standardní**.  
  
 **Automaticky upravit vzhled na základě výkonu klienta**  
 Určuje, zda sady Visual Studio úpravy automaticky nastaví na vizuální prostředí nebo explicitně nastavit úpravy. Toto nastavení může změnit zobrazení barvy z přechody pro plochý barev, nebo to může omezit použití animací v nabídkách nebo automaticky otevíraného okna windows.  
  
 **Povolit vzhled plně funkčního klienta**  
 Poskytuje možnost celý vizuální prostředí sady Visual Studio, včetně přechody a animace. Při použití připojení ke vzdálené ploše nebo starší grafických adaptérů, protože tyto funkce může dojít ke snížení výkonu v těchto případech, zrušte tuto možnost. Tato možnost je dostupná jenom v případě, že zrušíte výběr **automaticky upravit vzhled na základě klienta** možnost.  
  
 **Použít hardwarovou akceleraci grafiky, pokud je k dispozici**  
 Používá hardwarovou akceleraci grafiky, pokud je k dispozici, nebo softwarové akcelerace.  
  
## <a name="other"></a>Ostatní  
 **Položek zobrazených v nabídce okno**  
 Přizpůsobí počet období, která se zobrazí v seznamu Windows **okno** nabídky. Zadejte číslo mezi 1 a 24. Ve výchozím nastavení počet je 10.  
  
 **Počet položek zobrazovaných v seznamech**  
 Přizpůsobí počet naposledy použitých projekty a soubory, které se zobrazují na **souboru** nabídky. Zadejte číslo mezi 1 a 24. Ve výchozím nastavení počet je 10. Toto je snadný způsob, jak načíst nedávno použité projekty a soubory.  
  
 **Zobrazit stavový řádek**  
 Zobrazí stavový řádek. Stavový řádek je umístěn na spodní části okna IDE a zobrazí informace o průběhu probíhající operace.  
  
 **Tlačítko Zavřít ovlivní pouze aktivní okno nástrojů**  
 Určuje, kdy **Zavřít** po kliknutí na tlačítko, jen pro okno nástroje, který má právě fokus, je uzavřený a ne všechny oken nástrojů ukotvených v sadě. Ve výchozím nastavení je tato možnost vybrána.  
  
 **Automaticky skrýt ovlivní pouze aktivní okno nástrojů**  
 Určuje, kdy **automaticky skrýt** po kliknutí na tlačítko, pouze panel nástrojů, který má právě fokus, je skrytý automaticky a nikoli všech oken nástrojů ukotvených v sadě. Ve výchozím nastavení tato možnost není vybraná.  
  
 **Správa přidružení souborů**  
 Zobrazí **Windows nastavení asociací programu** dialogové okno, kde můžete zobrazit přípony souborů pro položky, které jsou obvykle přidruženy k sadě Visual Studio a aktuální výchozí program pro otevření všechny typy souborů. Sada Visual Studio výchozí aplikace pro typy souborů, které ještě nejsou s ní spojené, zvolte příponu souboru a klikněte na tlačítko **Uložit**.  
  
 Tato možnost může být užitečné, pokud máte dvě verze sady Visual Studio nainstalované ve stejném počítači a později odinstalujete jednu z verzí. Po odinstalaci, zobrazí se ikony pro soubory sady Visual Studio už v Průzkumníku souborů. Kromě toho Windows již nerozpoznává sady Visual Studio jako výchozí aplikace pro úpravu těchto souborů. Tato možnost obnoví tyto asociace.  
  
## <a name="see-also"></a>Viz také  
 [Dialogové okno Možnosti prostředí](../../ide/reference/environment-options-dialog-box.md)   
 [Přizpůsobení rozložení oken](../../ide/customizing-window-layouts-in-visual-studio.md)



