---
title: Nastavení konfigurace ladění a vydaných verzí | Microsoft Docs
ms.date: 10/05/2018
ms.topic: how-to
f1_keywords:
- vs.debug.builds
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- configurations, release
- build configurations, release
- projects [Visual Studio], release configurations
- debugging [Visual Studio], release configurations
- release builds, changing settings
- debug builds
- debug builds, switching to release build
- debug builds, changing configuration settings
- debugging [Visual Studio], debug configurations
- projects [Visual Studio], debug configurations
- build configurations, debug
- debug configurations
- release builds, switching to debug build
- Visual Basic projects, debug and release builds
ms.assetid: 57b6bbb7-f2af-48f7-8773-127d75034ed2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e85f7c67f8dc25bb69f7de07a19286b5c63e938a
ms.sourcegitcommit: ed4372bb6f4ae64f1fd712b2b253bf91d9ff96bf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2020
ms.locfileid: "89599900"
---
# <a name="set-debug-and-release-configurations-in-visual-studio"></a>Nastavení konfigurace ladění a vydaných verzí v sadě Visual Studio

Projekty sady Visual Studio mají samostatné konfigurace vydaných verzí a ladění pro váš program. Sestavíte ladicí verzi pro ladění a verzi Release pro konečnou distribuci vydaných verzí.

V konfiguraci ladění se program kompiluje s úplnými symbolickými informacemi o ladění a bez optimalizace. Optimalizace komplikuje ladění, protože vztah mezi zdrojovým kódem a vygenerovanými pokyny je složitější.

Konfigurace vydané verze vašeho programu neobsahuje symbolické ladicí informace a je plně optimalizována. Pro spravovaný kód a kód jazyka C++ lze informace o ladění generovat v souborech. pdb v [závislosti na použitých možnostech kompilátoru](#BKMK_symbols_release) . Vytváření souborů. pdb může být užitečné, pokud budete později muset ladit prodejní verzi.

Další informace o konfiguracích sestavení naleznete v tématu [Principy konfigurací sestavení](../ide/understanding-build-configurations.md).

Můžete změnit konfiguraci sestavení z nabídky **sestavit** , z panelu nástrojů nebo na stránkách vlastností projektu. Stránky vlastností projektu jsou specifické pro jazyk. Následující postup ukazuje, jak změnit konfiguraci sestavení z nabídky a panelu nástrojů. Další informace o tom, jak změnit konfiguraci sestavení v projektech v různých jazycích, naleznete v části [Viz také](#see-also) níže.

## <a name="change-the-build-configuration"></a>Změna konfigurace sestavení

Chcete-li změnit konfiguraci sestavení, proveďte jednu z těchto akcí:

* V nabídce **sestavení** vyberte **Configuration Manager**a pak vyberte **ladit** nebo **vydat**.

nebo

* Na panelu nástrojů vyberte buď možnost **ladit** , nebo **vydaná verze** v seznamu **Konfigurace řešení** .

  ![konfigurace sestavení panelů nástrojů](../debugger/media/toolbarbuildconfiguration.png "ToolbarBuildConfiguration")

## <a name="generate-symbol-pdb-files-for-a-build-c-c-visual-basic-f"></a><a name="BKMK_symbols_release"></a>Generování souborů symbolů (. pdb) pro sestavení (C#, C++, Visual Basic, F #)

Můžete zvolit generování souborů symbolů (. pdb) a informace o ladicím programu, které chcete zahrnout. Pro většinu typů projektů kompilátor generuje soubory symbolů ve výchozím nastavení pro sestavení ladění a vydání, zatímco jiné výchozí nastavení se liší podle typu projektu a verze sady Visual Studio.

> [!IMPORTANT]
> Ladicí program načte pouze soubor PDB pro spustitelný soubor, který přesně odpovídá souboru .pdb vytvořeném, když byl sestaven spustitelný soubor (to znamená, že PDB musí být originál nebo kopie původního souboru .pdb). Další informace najdete v tématu [Proč Visual Studio vyžaduje soubory symbolů ladicího programu, aby přesně odpovídaly binárním souborům, se kterými byly vytvořeny?](/archive/blogs/jimgries/why-does-visual-studio-require-debugger-symbol-files-to-exactly-match-the-binary-files-that-they-were-built-with).

Každý typ projektu může mít jiný způsob, jak tyto možnosti nastavovat.

### <a name="generate-symbol-files-for-a-c-aspnet-or-visual-basic-project"></a>Generovat soubory symbolů pro projekt C#, ASP.NET nebo Visual Basic

Podrobné informace o nastavení projektu pro konfiguraci ladění v jazyce C# nebo Visual Basic naleznete v tématu [nastavení projektu pro konfiguraci ladění c#](../debugger/project-settings-for-csharp-debug-configurations.md) nebo [nastavení projektu pro Visual Basic konfiguraci ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md).

1. V Průzkumník řešení vyberte projekt.

2. Vyberte ikonu **vlastnosti** (nebo stiskněte klávesu **ALT + ENTER**).

3. V bočním podokně vyberte **sestavení** (nebo **zkompilujte** v Visual Basic).

4. V seznamu **Konfigurace** vyberte možnost **ladění** nebo **vydání**.

5. Vyberte tlačítko **Upřesnit** (nebo tlačítko **Upřesnit možnosti kompilace** v Visual Basic).

6. V seznamu **ladicích informací** (nebo v seznamu **vygenerovat informace o ladění** v Visual Basic) vyberte **úplné**, **pouze PDB**nebo **přenosné**.

   Přenosný formát je nejnovější formát pro více platforem pro .NET Core. Další informace o možnostech najdete v tématu [dialogové okno Upřesnit nastavení sestavení (C#)](../ide/reference/advanced-build-settings-dialog-box-csharp.md).

   ![Generovat soubory PDB pro sestavení v jazyce C #](../debugger/media/dbg_project_properties_pdb_csharp.png "GeneratePDBsForCSharp")

7. Sestavte projekt.

   Kompilátor vytvoří soubory symbolů ve stejné složce jako spustitelný soubor nebo hlavní výstupní soubor.

### <a name="generate-symbol-files-for-a-c-project"></a>Generování souborů symbolů pro projekt C++

1. V Průzkumník řešení vyberte projekt.

2. Vyberte ikonu **vlastnosti** (nebo stiskněte klávesu **ALT + ENTER**).

3. V seznamu **Konfigurace** vyberte možnost **ladění** nebo **vydání**.

4. V bočním podokně zvolte **Linker > ladění**a pak vyberte možnosti pro **vygenerování informací o ladění**.

   Podrobné informace o nastavení projektu pro konfiguraci ladění v jazyce C++ naleznete v tématu [nastavení projektu pro konfiguraci ladění jazyka c++](../debugger/project-settings-for-a-cpp-debug-configuration.md).

5. Nakonfigurujte možnosti pro **vygenerování souborů databáze programu**.

   Ve většině projektů C++ je výchozí hodnota `$(OutDir)$(TargetName).pdb` , která generuje soubory. pdb ve výstupní složce.

   ![Generovat soubory PDB pro sestavení v C++](../debugger/media/dbg_project_properties_pdb_cplusplus.png "GeneratePDBsforCPlusPlus")

6. Sestavte projekt.

   Kompilátor vytvoří soubory symbolů ve stejné složce jako spustitelný soubor nebo hlavní výstupní soubor.

## <a name="see-also"></a><a name="see-also"></a>Viz také

- [Určení souborů symbolů (. pdb) a zdrojových souborů v ladicím programu sady Visual Studio](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)<br/>
- [Nastavení a příprava ladicího programu](../debugger/debugger-settings-and-preparation.md)<br/>
- [Nastavení projektu pro konfiguraci ladění jazyka C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)<br/>
- [Nastavení projektu pro konfiguraci ladění v jazyce C#](../debugger/project-settings-for-csharp-debug-configurations.md)<br/>
- [Nastavení projektu pro konfiguraci Visual Basicho ladění](../debugger/project-settings-for-a-visual-basic-debug-configuration.md)<br/>
- [Postupy: vytváření a úpravy konfigurací](../ide/how-to-create-and-edit-configurations.md)