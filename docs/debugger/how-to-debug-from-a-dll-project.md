---
title: Ladění z projektu knihovny DLL | Microsoft Docs
Description: Můžete spustit ladění projektu knihovny DLL z samotného projektu zadáním volající aplikace do vlastností projektu. Podrobnosti najdete v tomto článku.
ms.custom: SEO-VS-2020
ms.date: 10/10/2018
ms.topic: how-to
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 723f35142ec125c016caa3653be450b61fb05d02
ms.sourcegitcommit: 40d758f779d42c66cb02ae7face8a62763a8662b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2020
ms.locfileid: "97398555"
---
# <a name="how-to-debug-from-a-dll-project-in-visual-studio-c-c-visual-basic-f"></a>Postupy: ladění z projektu knihovny DLL v aplikaci Visual Studio (C#, C++, Visual Basic, F #)

Jedním ze způsobů, jak ladit projekt knihovny DLL, je určit volající aplikaci ve vlastnostech projektu knihovny DLL. Pak můžete spustit ladění z samotného projektu knihovny DLL. Aby tato metoda fungovala, musí aplikace volat stejnou knihovnu DLL ve stejném umístění jako ta, kterou nakonfigurujete. Pokud aplikace najde a načte jinou verzi knihovny DLL, nebude tato verze obsahovat vaše zarážky. Další metody ladění knihoven DLL naleznete v tématu [ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md).

Pokud vaše spravovaná aplikace volá nativní knihovnu DLL nebo vaše nativní aplikace volá spravovanou knihovnu DLL, můžete ladit jak knihovnu DLL, tak volající aplikaci. Další informace najdete v tématu [Postup: ladění ve smíšeném režimu](../debugger/how-to-debug-in-mixed-mode.md).

Nativní a spravované projekty knihovny DLL mají různá nastavení pro určení volání aplikací.

## <a name="specify-a-calling-app-in-a-native-dll-project"></a>Určení volající aplikace v nativním projektu knihovny DLL

1. Vyberte projekt C++ DLL v **Průzkumník řešení**. Vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER** nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. V dialogovém okně **\<Project> stránky vlastností** se ujistěte, že je pole **Konfigurace** v horní části okna nastaveno na hodnotu **ladit**.

1. Vyberte možnosti **Konfigurace**  >  **ladění**.

1. V seznamu **Spustit ladicí program** vyberte buď **místní ladicí program systému Windows** , nebo **vzdálený ladicí program systému Windows**.

1. Do **příkazu** nebo **vzdáleného příkazu** přidejte úplnou cestu a název souboru volající aplikace, jako je například soubor *. exe* .

   ![okno Vlastnosti ladění](../debugger/media/dbg-debugging-properties-dll.png "okno Vlastnosti ladění")

1. Do pole **argumenty příkazu** přidejte všechny nezbytné argumenty programu.

1. Vyberte **OK**.

## <a name="specify-a-calling-app-in-a-managed-dll-project"></a>Určení volající aplikace v projektu spravované knihovny DLL

1. Vyberte projekt v jazyce C# nebo Visual Basic DLL v **Průzkumník řešení**. Vyberte ikonu **vlastnosti** , stiskněte klávesu **ALT** + **ENTER** nebo klikněte pravým tlačítkem myši a zvolte možnost **vlastnosti**.

1. Ujistěte se, že pole **Konfigurace** v horní části okna je nastaveno na **ladit**.

1. V části **spouštěcí akce**:

   - V případě .NET Framework DLL vyberte možnost **spustit externí program** a přidejte plně kvalifikovanou cestu a název volající aplikace.

   - Případně vyberte možnost **spustit prohlížeč s adresou URL** a zadejte adresu URL místní aplikace ASP.NET.

   - V případě knihoven DLL .NET Core se stránka vlastnosti **ladění** liší. V rozevíracím seznamu **Spustit** vyberte **spustitelný soubor** a potom do pole **spustitelného souboru** přidejte plně kvalifikovanou cestu a název volající aplikace.

1. Do **argumentů příkazového řádku** nebo do pole **argumenty aplikace** přidejte všechny nezbytné argumenty příkazového řádku.

   ![Okno Vlastnosti ladění C#](../debugger/media/dbg-debugging-properties-dll-csharp.png "Okno Vlastnosti ladění C#")

1.   >  Chcete-li uložit změny, použijte možnost **Uložit vybrané položky** nebo **CTRL** + **S** .

## <a name="debug-from-the-dll-project"></a>Ladění z projektu knihovny DLL

1. Nastavte zarážky v projektu knihovny DLL.

1. Klikněte pravým tlačítkem na projekt knihovny DLL a vyberte **nastavit jako spouštěný projekt**.

1. Ujistěte se, že pole **Konfigurace řešení** je nastaveno na **ladit**. Stiskněte klávesu **F5**, klikněte na zelenou šipku **Start** nebo vyberte **ladit**  >  **Spustit ladění**.

Pokud ladění nevrátí vaše zarážky, ujistěte se, že váš výstup knihovny DLL (ve výchozím nastavení složka *\<project> \debug.* ) je umístění, ve kterém volající aplikace volá.

## <a name="see-also"></a>Viz také
- [Ladění projektů knihovny DLL](../debugger/debugging-dll-projects.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C#](../debugger/project-settings-for-csharp-debug-configurations.md)
- [Nastavení projektu pro konfiguraci ladění jazyka Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)