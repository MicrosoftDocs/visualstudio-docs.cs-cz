---
title: Aplikace Windows Store spustit na místním počítači | Dokumentace Microsoftu
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
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40fafcbdacac8a63a4aba70526a473d091b35de8
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766843"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Spusťte Windows Store apps na místním počítači
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí pouze pro Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Chcete-li ladit, testovat nebo spouštět analýzu výkonu v aplikaci Windows Store, můžete spustit aplikaci na stejném počítači, který je hostitelem aplikace Visual Studio. Je-li zobrazovat na zařízení dotykově ovládaný, můžete také vyzkoušet všechny funkce aplikace. v opačném případě bude omezená na gesta myš a klávesnici.  
  
##  <a name="BKMK_In_this_topic"></a> V tomto tématu  
 Další:  
  
 [Jak spustit na místním počítači](#BKMK_How_to_run_on_a_local_machine)  
  
 [Jak přepínat mezi aplikací Windows Store a sady Visual Studio na jednoho monitoru](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Jak spustit na místním počítači  
 Chcete-li spustit aplikaci na místním počítači, vyberte **místního počítače** z rozevíracího seznamu vedle tlačítka Spustit ladění na ladicí program **standardní** nástrojů.  
  
 ![Spustit na místním počítači](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Pokud nevidíte **standardní** nástrojů, klikněte na tlačítko **zobrazení** nabídky, přejděte na **panely nástrojů**a potom klikněte na **standardní**.  
  
 Podle výběru v rozevíracím seznamu se ukládají v souboru vlastnosti projektu a stane výchozím spustit cíl.  
  
 Spuštění cíle můžete také nastavit přímo v souboru vlastnosti projektu. Klikněte pravým tlačítkem na název projektu v **Průzkumníka řešení** a klikněte na tlačítko **vlastnosti**. Udělejte jednu z následujících akcí:  
  
-   V projektech C# a Visual Basic, klikněte na tlačítko **ladění** a pak vyberte **místního počítače** z **cílové zařízení** rozevíracího seznamu.  
  
     ![C&#35; a stránky vlastností projektu jazyka Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   V projektech C++ a JavaScript, rozbalte **vlastnosti konfigurace** uzel, klikněte na tlačítko **ladění**a pak vyberte **místní ladicí program** z **ladicího programu ke spuštění** seznamu.  
  
     ![C&#43; &#43; a stránky vlastností projektu JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Jak přepínat mezi aplikací Windows Store a sady Visual Studio na jednoho monitoru  
 **Chcete-li přepnout z běžící instance aplikace pro Windows Store se sadou Visual Studio**  
  
 Při spuštění aplikace Windows Store v místním počítači a používat pouze jednoho monitoru, můžete chtít přepněte zpět do sady Visual Studio a ponechání spuštěné aplikace. Například aplikace může být ve stavu, který nelze dosáhnout, zarážky, jako je například čekání na událost nebo zachycena v dlouhé nebo nekonečné smyčce. Pokud chcete vrátit do sady Visual Studio, stiskněte ALT + TAB.



