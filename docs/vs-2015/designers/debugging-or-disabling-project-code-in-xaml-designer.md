---
title: Ladění nebo zakázání kódu projektu v Návrháři XAML | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/15/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ac600581-8fc8-49e3-abdf-1569a3483d74
caps.latest.revision: 7
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2507b509ee33957845f010f7c18404d257ad4a38
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/23/2018
ms.locfileid: "49837578"
---
# <a name="debugging-or-disabling-project-code-in-xaml-designer"></a>Ladění nebo zakázání kódu projektu v Návrháři XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

V mnoha případech může být způsobeno neošetřenými výjimkami v Návrháři XAML kód projektu pokusu o přístup k vlastnosti nebo metody, které vracet různé hodnoty nebo fungovat různými způsoby, když je aplikace spuštěna v návrháři. Můžete tyto výjimky vyřešit ladění kódu projektu v jiné instanci sady Visual Studio nebo dočasně zakázat tím, že zakážete kódu projektu v návrháři.  
  
 Kód projektu zahrnuje:  
  
- Vlastní ovládací prvky a uživatelských ovládacích prvků  
  
- Knihovny tříd  
  
- Převodníky hodnot  
  
- Vazby proti návrhovém generován z kódu projektu  
  
  Když kód projektu je zakázaný, Visual Studio bude zobrazovat zástupné symboly jako je například název vlastnosti pro vazbu, kde data už nejsou k dispozici. nebo zástupný text pro ovládací prvek, který je již spuštěn.  
  
  ![Dialogové okno s neošetřenou výjimkou](../designers/media/xaml-unhandledexception.png "XAML_UnhandledException")  
  
#### <a name="to-determine-if-project-code-is-causing-an-exception"></a>Chcete-li zjistit, zda kód projektu je příčinou výjimku  
  
1.  V dialogovém okně neošetřenou výjimku, zvolte **klinutím sem zopakujete zavedení návrháře** odkaz.  
  
2.  Na panelu nabídek zvolte **ladění**, **spustit ladění** sestavíte a spustíte aplikaci.  
  
     Pokud se aplikace sestaví a spustí úspěšně, výjimka návrhu může být způsobeno spuštění v Návrháři projektu kódu.  
  
#### <a name="to-debug-project-code-running-in-the-designer"></a>Chcete-li ladit projekt kódu spuštěného v Návrháři  
  
1.  V dialogovém okně neošetřenou výjimku, zvolte **kliknutím sem zakážete spuštění kódu projektu a opětovné načtení návrháře** odkaz.  
  
2.  Vyberte ve Správci úloh Windows **ukončit úlohu** zavřete všechny instance návrháři XAML sady Visual Studio, které jsou aktuálně spuštěny.  
  
     ![Instance návrháře XAML v úloh](../designers/media/xaml-taskmanager.png "XAML_TaskManager")  
  
3.  V sadě Visual Studio otevřete stránku XAML, který bude obsahovat kód nebo ovládací prvek, který chcete ladit.  
  
4.  Otevřete novou instanci sady Visual Studio a pak otevřete druhou instanci projektu.  
  
5.  Nastavte zarážku v kódu projektu.  
  
6.  V nové instanci sady Visual Studio na řádku nabídek zvolte **ladění**, **připojit k procesu**.  
  
7.  V **připojit k procesu** dialogového okna v **procesy k dispozici** klikněte na položku **XDesProc.exe**a klikněte na tlačítko **připojit** tlačítko.  
  
     ![Proces návrháře XAML](../designers/media/xaml-attach.png "XAML_Attach")  
  
     Jedná se o proces pro návrháře XAML v první instance sady Visual Studio.  
  
8.  V první instanci aplikace Visual Studio v panelu nabídek zvolte **ladění**, **spustit ladění**.  
  
     Nyní můžete krokovat do svého kódu, který je spuštěn v návrháři.  
  
#### <a name="to-disable-project-code-in-the-designer"></a>Chcete-li zakázat kód projektu v Návrháři  
  
-   V dialogovém okně neošetřenou výjimku, zvolte **kliknutím sem zakážete spuštění kódu projektu a opětovné načtení návrháře** odkaz.  
  
-   Můžete také na panelu nástrojů v Návrháři XAML, zvolte **zakázat kód projektu** tlačítko.  
  
     ![Tlačítko Zakázat kód projektu](../designers/media/xaml-disablecode.png "XAML_DisableCode")  
  
     Můžete přepínat na tlačítko znovu pro opětovné povolení kódu projektu.  
  
    > [!NOTE]
    >  Pro projekty, které cílí ARM nebo X64 procesory, Visual Studio nelze spustit kód projektu v návrháři, proto **zakázat kód projektu** je tlačítko neaktivní v návrháři.  
  
-   Možnost způsobí, že návrháře znovu načíst a zakáže pak veškerý kód pro přidružený projekt.  
  
    > [!NOTE]
    >  Zakázání kódu projektu může vést ke ztrátám v návrhovém. Alternativou je pro ladění kódu spuštěného v návrháři.  
  
## <a name="see-also"></a>Viz také  
 [Návrh XAML v sadě Visual Studio a Blend pro Visual Studio](../designers/designing-xaml-in-visual-studio.md)





