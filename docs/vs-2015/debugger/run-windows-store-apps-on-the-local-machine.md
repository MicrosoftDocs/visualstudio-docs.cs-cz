---
title: Spustit aplikace pro Windows Store v místním počítači | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196327"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Spouštění aplikací pro Windows Store v místním počítači
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Platí jenom pro Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Chcete-li ladit, testovat nebo spustit analýzu výkonu v aplikaci pro Windows Store, můžete aplikaci spustit ve stejném počítači, který je hostitelem sady Visual Studio. Pokud je displej na zařízení zapnutý dotykové ovládání, můžete využívat všechny funkce aplikace. jinak budete omezeni na gesta myší a klávesnicí.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> V tomto tématu  
 Můžete se dozvědět:  
  
 [Jak spustit na místním počítači](#BKMK_How_to_run_on_a_local_machine)  
  
 [Jak přepínat mezi aplikací pro Windows Store a Visual studiem na jednom monitoru](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Jak spustit na místním počítači  
 Pokud chcete aplikaci spustit na místním počítači, vyberte v rozevíracím seznamu vedle tlačítka Spustit ladění na panelu nástrojů **standardní** ladicí program možnost **místní počítač** .  
  
 ![Spustit na místním počítači](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Pokud nevidíte **standardní** panel nástrojů, klikněte na nabídku **zobrazení** , přejděte na **panely nástrojů**a klikněte na tlačítko **standardní**.  
  
 Volba, kterou provedete v rozevíracím seznamu, je trvalá v souboru vlastností projektu a vytvoří se jako výchozí cíl spuštění.  
  
 Cíl spuštění lze také nastavit přímo v souboru vlastností projektu. Klikněte pravým tlačítkem myši na název projektu v **Průzkumník řešení** a zvolte možnost **vlastnosti**. Pak proveďte jednu z následujících akcí:  
  
- V projektech C# a Visual Basic klikněte na **ladit** a v rozevíracím seznamu **cílové zařízení** vyberte **místní počítač** .  
  
     ![Stránka vlastností projektu C&#35; a Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- V projektech C++ a JavaScript rozbalte uzel **Vlastnosti konfigurace** , klikněte na možnost **ladění**a potom vyberte možnost **místní ladicí program** z **ladicího programu pro spuštění** seznamu.  
  
     ![Stránka vlastností projektu jazyka C&#43;&#43; a JavaScriptu](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Jak přepínat mezi aplikací pro Windows Store a Visual studiem na jednom monitoru  
 **Přepnutí z běžící instance aplikace pro Windows Store do sady Visual Studio**  
  
 Když spustíte aplikaci pro Windows Store na místním počítači a použijete jenom jedno monitorování, můžete přejít zpátky do sady Visual Studio a nechat aplikaci spuštěnou. Například aplikace může být ve stavu, který nemůže být dosažitelný zarážkou, například čekáním na událost nebo přesahy do dlouhého nebo nekonečné smyčky. Pokud se chcete vrátit do sady Visual Studio, stiskněte klávesy ALT + TAB.
