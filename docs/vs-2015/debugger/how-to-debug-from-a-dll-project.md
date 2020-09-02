---
title: 'Postupy: ladění z projektu knihovny DLL | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 6496d38e753d2338966916d1d7855abca77ace34
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "64819163"
---
# <a name="how-to-debug-from-a-dll-project"></a>Postupy: Ladění z projektu knihovny DLL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Chcete-li spustit ladění projektu knihovny DLL, je nutné zadat volající aplikaci ve vlastnostech projektu. Stránky vlastností C++ se liší v rozložení a obsahu na stránkách vlastností C# a Visual Basic.  
  
 Pokud je spravovaná knihovna DLL volána nativním kódem a chcete ji ladit, můžete ji zadat ve vlastnostech projektu. Další informace najdete v tématu [Postup: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).  
  
> [!NOTE]
> V edicích Express sady Visual Studio nelze zadat externí volající aplikaci. Místo toho je třeba do řešení přidat spustitelný projekt, nastavit jej jako spouštěný projekt a volat metody v knihovně DLL ze spustitelného projektu.  
  
### <a name="to-specify-the-calling-application-in-a-c-project"></a>Určení volající aplikace v projektu C++  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**. Přejít na kartu **ladění** .  
  
2. Ujistěte se, že pole **Konfigurace** v horní části okna je nastaveno na **ladit**.  
  
3. Přejít na **vlastnosti nebo ladění konfigurace**.  
  
4. V seznamu **Spustit ladicí program pro spusťte** možnost **místní ladicí program systému Windows** nebo **vzdálený ladicí program systému Windows**.  
  
5. Do **příkazu** nebo **vzdáleného příkazu** přidejte plně kvalifikovaný název cesty aplikace.  
  
6. Do pole **argumenty příkazu** přidejte všechny nezbytné argumenty programu.  
  
### <a name="to-specify-the-calling-application-in-a-c-or-visual-basic-project"></a>Určení volající aplikace v projektu C# nebo Visual Basic  
  
1. V **Průzkumník řešení** klikněte pravým tlačítkem myši na uzel projektu a vyberte možnost **vlastnosti**. Přejít na kartu **ladění** .  
  
     Vyberte **spustit externí program**a přidejte plně kvalifikovaný název pro spuštění programu.  
  
     Pokud potřebujete přidat argumenty příkazového řádku externího programu, přidejte je do pole **argumenty příkazového řádku** .  
  
2. Můžete také zavolat aplikaci jako adresu URL. (Toto můžete chtít provést, pokud ladíte spravovanou knihovnu DLL používanou místní aplikací ASP.NET.)  
  
     V části **Spustit akci**vyberte možnost **spustit prohlížeč v URL:** přepínač a zadejte adresu URL.  
  
### <a name="to-start-debugging-from-the-dll-project"></a>Spuštění ladění z projektu knihovny DLL  
  
1. V případě potřeby nastavte zarážky.  
  
2. Spusťte ladění (stiskněte klávesu F5, klikněte na zelenou šipku nebo klikněte na **ladění/spustit ladění**).  
  
## <a name="see-also"></a>Viz také  
 [Ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md)   
 [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)
