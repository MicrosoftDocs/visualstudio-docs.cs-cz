---
title: 'Postupy: ladění z projektu knihovny DLL | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 10/10/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- DLL projects, debugging
- debugging DLLs
- DLLs, debugging projects
- debugging [Visual Studio], DLLs
ms.assetid: 40a94339-d3f7-4ab9-b8a1-b8cf82942f44
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e006bbd27acc0fa88cfee1b22cb435acba1e282e
ms.sourcegitcommit: dd839de3aa24ed7cd69f676293648c6c59c6560a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2018
ms.locfileid: "52388251"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Postupy: ladění z projektu knihovny DLL v sadě Visual Studio (C#, C++, Visual Basic, F#)

Jedním ze způsobů k ladění projektu knihovny DLL je volající aplikace zadejte ve vlastnostech projektu knihovny DLL. Potom spustíte ladění z projektu knihovny DLL, samotného. Pro tuto metodu za účelem fungovat musí volat stejné knihovny DLL ve stejném umístění jako ta, kterou nakonfigurujete. Pokud aplikace vyhledá a načte jinou verzi knihovny DLL, tuto verzi nesmí obsahovat vaše zarážky. Další způsoby ladění knihoven DLL najdete v tématu [projektů knihovny DLL ladění](../debugger/debugging-dll-projects.md).
  
Pokud vaše spravovaná aplikace volá nativní knihovnu DLL nebo nativní aplikace volá operaci spravované knihovny DLL, můžete ladit knihovnu DLL a volání aplikace. Další informace najdete v tématu [postupy: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).   

Nativní a spravované projekty knihovny DLL mají různá nastavení zadejte aplikace pro volajícího. 

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Zadejte volání aplikace do nativního projektu knihovny DLL  
  
1. Vyberte projekt knihovny DLL v C++ v **Průzkumníka řešení**. Vyberte **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter**, nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.
   
1. V  **\<Projekt > stránky vlastností** dialogové okno pole, ujistěte se, že **konfigurace** pole v horní části okna je nastaveno **ladění**. 
   
1. Vyberte **vlastnosti konfigurace** > **ladění**.  
   
1. V **ladicí program ke spuštění** , zvolte buď **místní ladicí program Windows** nebo **vzdálený ladicí program Windows**.  
   
1. V **příkaz** nebo **vzdálený příkaz** pole, přidejte plně kvalifikovanou cestu a název souboru volající aplikace, například *.exe* souboru.
   
   ![Okno Vlastnosti ladění](../debugger/media/dbg-debugging-properties-dll.png "ladit vlastnosti okna")  
   
1. Přidat všechny argumenty potřebné program **argumenty příkazu** pole.  
   
1. Vyberte **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Zadejte volání aplikace v spravovaného projektu knihovny DLL  
  
1. Vyberte projekt C# nebo knihovny DLL jazyka Visual Basic v **Průzkumníka řešení**. Vyberte **vlastnosti** ikonu, stiskněte klávesu **Alt**+**Enter**, nebo klikněte pravým tlačítkem a zvolte **vlastnosti**.
   
1. Ujistěte se, že **konfigurace** pole v horní části okna je nastaveno **ladění**.
   
1. V části **zahájení**:
   
   - Pro knihovny DLL .NET Framework, vyberte **externí program Start**a přidejte plně kvalifikovanou cestu a název volající aplikace.
     
   - Nebo vyberte **Start prohlížeč s adresou URL** a zadejte adresu URL místní aplikace ASP.NET. 
   
   - Pro knihovny DLL .NET Core **ladění** stránku vlastností se liší. Vyberte **spustitelný soubor** z **spuštění** rozevírací seznam a pak přidejte plně kvalifikovanou cestu a název volající aplikace v **spustitelný soubor** pole. 
   
1. Přidat všechny potřebné argumenty příkazového řádku **argumenty příkazového řádku** nebo **argumenty aplikace** pole.
   
   ![Okno ladění vlastností jazyka C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "okno ladění vlastností jazyka C#") 
   
1. Použití **souboru** > **uložit vybrané položky** nebo **Ctrl**+**S** uložte změny.

## <a name="debug-from-the-dll-project"></a>Ladění z projektu knihovny DLL  
 
1. Nastavte zarážky v projektu knihovny DLL.

1. Klikněte pravým tlačítkem na projekt knihovny DLL a zvolte **nastavit jako spouštěný projekt**. 

1. Ujistěte se, že **konfigurace řešení** je nastaveno na **ladění**. Stisknutím klávesy **F5**, klikněte na zelené **Start** šipku, nebo vyberte **ladění** > **spustit ladění**.

Pokud ladění nenarazí své zarážky, ujistěte se, že vaše knihovna DLL výstup (ve výchozím nastavení,  *\<Projekt > \Debug* složky) je umístění, které je volání volající aplikace.
  
## <a name="see-also"></a>Viz také:  
 [Ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)   
 [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)